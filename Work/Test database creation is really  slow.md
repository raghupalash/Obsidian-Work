So test database is taking really long to create and the culprit is the number of migrations.

First I think I should try to understand the concept of migrations properly.

So migrations are causing our database creation to be really slow, and from what I saw, they are not arranged properly, there are just too many of them, and every developer adds so many  migrations per feature. So need to learn to squash it.