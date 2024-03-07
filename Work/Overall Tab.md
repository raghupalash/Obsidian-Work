UI shouldn't be that hard - we just need to add an extra column in the beginning - maybe inside the render function.
	- Creating the backend table is going to be the tricky part. If I can manage to join the two tables correctly, then I think it would be awesome.

Okay, we have an idea, we want our result table to look like this:

| row | a_A  | a_B  | a_C  | b_A  | b_C  | a_overall | b_overall |
|-----|------|------|------|------|------|-----------|-----------|
| row | 1    | 10.0 | 20.0 | NaN  | 30.0 | NaN       | 30        |
| row | 2    | NaN  | 50.0 | 60.0 | NaN  | 110       | 40        |

We don't need to rearrange or anything, because we render using the "row" variable thingy, and the row is the full dictionary.

Right now we do 3d to 2d conversion in the paginated response thing, we should avoid that and instead do that in the results function itself. So the goal now is to rearrange that conversion thing, check if everything is alright, and then we build this functionality.

Doing with row = state, col = marketplace, subcol = brand - data seems good, apart from marketplace_id = 7. Remeber that.
- I think the reason is that in our initial availability_points table, there are some data points whose sub_column values are set to NaN, but percentage is still filled, this gets used in the average calculation and messes up the data. I'll think about that.

But now, we have something we can work with in the UI.

getDataColumns doesn't return multiple "Columns" but one single renderable data column, that's why I don't think it should call the getDataHeader function, because it would be called for each sub column again and again.


Done!