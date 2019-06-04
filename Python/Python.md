# 1. Python Library

```python
from turtle import * 
# This line accesses the turtle library, a process called importing. Without this line, we can't use any of the commands that control our turtle.

forward(300) 
# The forward() command is provided by the turtle library. This command tells the turtle to walk forward 300 steps.

bye() 
# The bye() command tells the turtle she is done, and causes the turtle's image to be saved. If you don't run this command, there won't be any picture to see! Unlike the print() and forward() commands, the bye() command doesn't have any arguments. The Python language requires you to include the parentheses anyway.
```





# 2. For loop

```python
from turtle import *
# Repeat ('looped over') 10 times.
color('red')

for i in range(10):
# In Python, all the indented lines that follow the line for i in range(10) will be repeated 10 times.
    left(108)
    forward(200)
# This line is also indented. We run the entire indented segment 10 times, so we will turn left and then move forward 10 times. (We won't turn left 10 times and then move forward 10 times.)
# No more indentation! This marks the end of the for-loop.
bye()
```

