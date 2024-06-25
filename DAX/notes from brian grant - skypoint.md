![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/5096bea4-13fc-4cc6-8b87-203261226413)



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
