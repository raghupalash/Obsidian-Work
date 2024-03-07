Balaji is saying that since I'm using the production data (Athena) in the report, I would need production access. Also he says that data in my local might not be consistent with the data in Athena, so I would need to go and do some changes?

I think, the most important piece of the puzzle is the query we are sending to Athena. I think it would help us loads if we can figure out how that works.

I have very little understanding of the table.

Is Company == Supplier?

Distributor in Entities?

Looking at where clause building code:

My intuition says that "if marketplace", "if skus", "if states", "if custom_goruping" is for filters and not for actual rows and columns field.

There are two things to do:

1. How to do query on 3 items, instead of 2
	- How to package into Data Frame.
	- How to display it onto frontend.
1. How to get Supplier, Brand and Category into the picture.


So I can't get Supplier and Category into the picture, but Brand is coming!

I have did some change in the logic, and I feel that I have done more than enough sub_columns integration to the backend logic. Now I need to understand how the data is taken in the frontend. 

Let's make frontend the priority! Lets see how it's doing it right now. And lets think about what we can do to change it - to have dynamic sub-columns, instead of just single columns

The row and column html selection is based on the actions of UI only(what options were selected), the backend doesn't seem to have anything to do with it!

I think drawCallBack is called when the data is filled in the boxes. - Confirmed!

So the row and column data is here from before, right? Do we just take them all together?

`restockOpportunitytableColumns` is the column headers. The value is filled by `setupRestockOpportunityTopTable` - which is then used in `restockOpportunityTopTableConfig` and `initializeTopTable`

`restockOpportunityTopTableConfig` -> `initializeTopTable`

`setupRestockOpportunityTopTable` sets up the row and column headers I think and does other setup tasks, after which `initializeTopTable` is executed.

One hypothesis that is coming to mind is, we can have sub_column field in frontend, and we can fill it the same way we fill columns. So we'll already have the headers we need.

I think, but first, I'll need to figure out if a thing like this is possible or not, then we can make changes in the backend.

In case of no sub column, we would need to revert back of previous set up of showing a 2d table.


In my current implementation, for row, it's a list and for columns, it's a function.