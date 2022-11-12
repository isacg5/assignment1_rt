Python Robotics Simulator
================================

This is the first assignment of Research Track course, based on a simple and portable robot simulator developed by [Student Robotics](https://studentrobotics.org).

In this assignment, the robot has to take the silver boxes, one by one, and put each one next to a golden box. The way the assignment is done has been putting each silver box next to the closest golden one, to avoid any collision or further problem that could exist in real life.


Installing and running
----------------------

The simulator requires a Python 2.7 installation, the [pygame](http://pygame.org/) library, [PyPyBox2D](https://pypi.python.org/pypi/pypybox2d/2.1-r331), and [PyYAML](https://pypi.python.org/pypi/PyYAML/).
```bash
$ sudo apt-get install python-dev python-pip python-pygame
```

```bash
$ sudo pip install pypybox2d
```

How to run it, after cloning the repository

```bash
$ cd robot-sim
$ python2 run.py assignment.py
```

Flowchart
----------------------
Flowchart is a diagram that shows each step of the progress of a program in a sequential order. In this case, the flowchart present is the one of the 'assignment.py' file.

The rhombus represent the decisions, the rounded rectangles the sequence of actions and the rectangles the beginning and end of the program.
![alt text](https://github.com/isacg5/research_track/blob/main/resources/flowchart.png)


Pseudocode
----------------------
Pseudocode is an informal way to descirbe the program done in a simplest and understandable way. Here is presented the pseudocode of the 'assignment.py' file.
```python
while not finished:
    if length_of_ordered_boxes is equal to 12
        finished is True

    find_markers_distance_rotation_and_code

    if no_marker_detected:
        turn

    elif robot_close_to_token:
        if token_to_find is gold:
            release_token
            go_backwards
            add_token_to_ordered_boxes
            token_to_find = silver
        
        else:
            grab_token
            add_token_to_ordered_boxes
            find_closest_gold
            token_to_find = gold

    elif robot_centered:
        go_forward

    elif robot_angle_positive:
        turn_right

    elif robot_andgle_negative:
        turn_left

exit
```


Possible improvements
----------------------
One improvement that could be done for the faster execution of the code would be using the positions in the map. By knowing the positions of everything in the world, the robot could calculate directly the closest token and go there withouth have to have a look to the different tokens.

