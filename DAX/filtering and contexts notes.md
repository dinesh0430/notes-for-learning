Data model 

![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/7cc5a871-9134-4682-bce6-ff9d8a6e4838)

![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/618af46f-0ee3-484f-aeb3-db260093c27f)

Consider this example:

![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/e265360b-e3cd-4bcf-b040-7bce82a75cd3)

The filter propagates from "One" side to "Many" side, the chain keeps on going for all the connected "One to Many", 
but if the chain encounters at least one "Many to One" it stops propagating, as the filter can't go from "Many to One". 
Consider the filter context for the first row of "AC/DC", the filter context would be having "AC/DC"

![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/a0a844a3-2835-4160-851c-ef6f8f62597e)

We can use the debugger from Tabular Editor 3 and remove the filter on the table, "Artist" to see the affect of it on other tables

![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/9c9d75de-0f71-4cdc-a9a3-c78610d12b9c)

We can see that City, Venue and Subgenre didn't have any change in the row count, while Show, Tour, Artist (obviously), Album and Track had a change in 
their row count, it indicates that the filter propagates as a chain starting from the concerned table and growing to all related ("One to Many") tables 
and stops if it encounters "Many to One" relationships.

