Python Robotics Simulator
================================

This is the first assignment of Research Track course, based on a simple and portable robot simulator developed by [Student Robotics](https://studentrobotics.org).


Installing and running
----------------------

The simulator requires a Python 2.7 installation, the [pygame](http://pygame.org/) library, [PyPyBox2D](https://pypi.python.org/pypi/pypybox2d/2.1-r331), and [PyYAML](https://pypi.python.org/pypi/PyYAML/).
```bash
$ sudo apt-get install python-dev python-pip python-pygame
```

```bash
$ sudo pip install pypybox2d
```

How to run it

```bash
$ python2 run.py assignment.py
```

Functions in the code
----------------------
To have a better approach to the knowledge of how the code works, the functions that appear in the code are deeply explained here.

- get_velocity(distance): This function calcuilate the linear velocity of the robot depending on the distance. Is used a proportional linear formula, in a way that the farest the robot is, the fastest it will move. Are also considered velocity limits in the case that the robot is too close or too far.

- get_rotation_vel(rot_y): This fuction does the same as get_velocity(distance) but for the angular velocity, using an exponential function for the velocity with respect to rot_y.

- find_closes_gold(): Finds the closest golden token among all the tokens in the world. To do that, it turns counting the golden tokens. Due to the distribution of the world and that the robot is in the middle, if it detects a token closer than the previous and the next one, is directly the closest in all the world. Otherwise, if all the tokens have been seen it stops turning and go directly to the closest one.

- find_token(color, code); This function returns the linear and angular distances and the code of the closest token that the robot can see. To avoid the tokens that it has already manipulated, it checks if the token code is in the array created of ordered tokens (the ones already used). 

- turn(speed, seconds): Sends the angular velocity and the seconds that the robot will turn.

- drive(speed, seconds): Send the linear velocity and the second that the robot will linear move.

Flowchart
----------------------
Flowchart is a diagram that shows each step of the progress of a program in a sequential order. In this case, the flowchart present is the one of the 'assignment.py' file.
![alt text](https://github.com/isacg5/research_track/blob/main/resources/flowchart.png)

Pseudocode
----------------------
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

