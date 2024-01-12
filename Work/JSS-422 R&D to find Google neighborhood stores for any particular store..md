
So here's what I think.

First, we'll need to query the database for stores - we need to make that search as small as possible - we can either narrow our search down to all the stores in a single city, or maybe we can directly filter using lat-long - If we have a big single db, then directly doing it would be better. But we different db based on location, doing filtering in steps would be better.

So each api response seem to have a `viewport` field, that defines the bounded region - lat and long of the diagonal points are given. So we just need to find the stores with lat-long in those ranges.

say `(x1, y1)` and `(x2, y2)` are the co-ordinates of the `viewport` diagonal. A store `(x, y)` is inside the viewport if:
1. `min(x1, x2)` <= `x` <= `max(x1, x2)`
2. `min(y1, y2)` <= `y` <= `max(y1, y2)`

potential issues:
1. Size of the viewport - how google defines it? And wouldn't it be better to provide it ourselves anyways? Like we can have a default value and our users can change it as they like? We don't have to provide different options - simpler UI!
	- take a look at the current ui
		- currently we have two separate options - "Neighbourhood" and "Boundry"
	- study the api's bound thingy! How we can make search - should we do it by name or coordinates and how does the bound thing work?
2. size of the viewport is really small, finding the multiple merchants in the same viewport is going to be a challange.


This is the script I came up with:
```py
from django.db.models import Q
from shieldsuite.models import Merchant

def get_merchants_inside_viewport(viewport):
    ne_lat = viewport['northeast']['lat']
    ne_lng = viewport['northeast']['lng']
    sw_lat = viewport['southwest']['lat']
    sw_lng = viewport['southwest']['lng']

    # Latitude condition
    lat_condition = Q(metadata__results__0__geometry__location__lat__gte=sw_lat) & \
                    Q(metadata__results__0__geometry__location__lat__lte=ne_lat)

    # Longitude condition
    lng_condition = Q(metadata__results__0__geometry__location__lng__gte=sw_lng) & \
                    Q(metadata__results__0__geometry__location__lng__lte=ne_lng)

    merchants_inside_viewport = Merchant.objects.filter(lat_condition, lng_condition).values("id", "name")

    return merchants_inside_viewport

# Example usage
viewport_coordinates = {
    "northeast": {"lat": 40.760646, "lng": -73.964983},
    "southwest": {"lat": 40.757948, "lng": -73.967681}
}

result = get_merchants_inside_viewport(viewport_coordinates)
print(result)
```

And it's working quite well, as far as I have checked...