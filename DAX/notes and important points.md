![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/5096bea4-13fc-4cc6-8b87-203261226413)

### Check "Elements of DAX with Brian Grant" and check out the videos from chapter 6

calculate architecture:
![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/cb01f037-60b5-44e5-9704-1c1bf6c0ef9b)



Brief look at context transition with calculate, and shows how it won't work if calculate is not present


![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/0a0a1890-e077-4a08-9e7c-0263231951b0)



Further look at an expression used in calculate and the same expression put in a measure and the measure directly used (the measure when directly used invokes a calculate implicitly). They both behave the same way and give the same result

Case1:

![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/0ef6f400-e312-4862-86ab-031906ca2d5e)


Case 2:

![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/d8ef3694-f203-4792-aa96-c1f645c32189)

Explanation:

![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/d693f269-1afb-47e8-aee8-3c8c0c257f42)



Additional Filters added as subexpressions and how they evaluate:

![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/1b0240ff-dcdd-49a0-8446-04fefaaac31f)

Calculate table:
![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/c2c5e086-50d6-465a-9883-ebab3fecb79f)


Row context with calculate and how it is visualized in a nested iterator (averageX and sumX):
![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/7fdc0b8b-85dd-4e22-86d7-2a0e0ed5ebfd)


When both "Current row filtering (Context Transition) and override filters" are given to a calculate (take a look at the small grey text at the bottom right for how context transition and override filters interract, basically they both go in at the same time, one shouldn't influence the other)

![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/431dfd22-93e4-42d9-88e4-57e78f52e4f5)


If there is a clash between reviser's filters then, the inner would block the outer reviser's conflicting reviser and continues
![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/8c71e5e0-d959-4976-933c-13c625c172b8)


## SQL BI - Filter context, the image shows what happens if new filter comes in and clashes with existing filter

![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/760bc33b-6b46-43a5-9acc-84e0c24ef44e)


## SQL BI - KEEPFILTERS, important check on how filters combine, remove, replace and add to the filter context

https://youtu.be/L5WR-imfyYI?feature=shared

https://youtu.be/m820AXmoato?feature=shared

![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/a6270858-4638-4546-b18d-55dc6bef361a)
![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/491a5374-9052-4c62-b3b2-e519e2547e32)

![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/7515b537-8421-4a49-ab2a-3bd892a5303c)


## FILTER CONTEXT SOME QUICK POINTS

https://www.sqlbi.com/articles/filter-context-in-dax/

![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/0566cf42-807b-456a-96fd-608781008052)

## Expanded tables are very important to understand the concept of Relationships and etc

https://www.sqlbi.com/articles/expanded-tables-in-dax/

![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/e067dea9-621e-4c3d-ae55-257c7f274020)

![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/940ac999-6402-41cf-9be1-dbd8db321071)

#### Context Transition and how the row context is transitioned to filter context, if the row has multiple columns

![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/dda5afa8-3bf3-4ce2-9bdc-d46ac536bde3)

When we pass a table to a calculate as filter expression, then we are likely passing a large expanded table, which would overwrite many filters

![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/109cb871-1954-47c9-91cf-919fecfbf7b3)
