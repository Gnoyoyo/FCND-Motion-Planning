# FCND - 3D Motion Planning

## Writeup / README

### 1. Provide a Writeup / README that includes all the rubric points and how you addressed each one.  You can submit your writeup as markdown or pdf

You're reading it! Below I describe how I addressed each rubric point and where in my code each point is handled.

### Explain the Starter Code

#### 1. Explain the functionality of what's provided in `motion_planning.py` and `planning_utils.py`

##### Test that `motion_planning.py` is a modified version of `backyard_flyer_solution.py` for simple path planning. Verify that both scripts work. Then, compare them side by side and describe in words how each of the modifications implemented in `motion_planning.py` is functioning

`motion_planning.py` and `backyard_flyer_solution.py` are both state machine, the main difference will be the state both are using.  
The state of the `backyard_flyer_solution.py` are the folowing.

- Arming
- Takeoff
- Waypoint
- Landing
- Disarming
- Manual

For the `motion_planning.py` the state will be the same as `backyard_flyer_solution.py` but the difference is there is Planning state added in between Arming and Takeoff as shown in the diagram.

![Diagram Image](./misc/diagram/diagram.png)

![Code Image](./misc/code/backyard_and_motion.PNG)

As seen below in `state_callback` after the drone is armed. It will call `plan_path()` which is responsible for planning by calculating waypoint for the drone before takeoff.

![Plan Pth](./misc/code/plan_path.PNG)

The `plan_path` method will do the following.

- Set the state to Planning
- Set Target Altitude and Safety Distance
- Load obstacle
- Create safty grid for our target altitude and safty distance by using `crete grid` method which provided in `planning_utils.py`
- Define start point
- Define Goal point
- Find a pathway by using `a_star` method which provided in `planning_utils.py`.
- Convert path to waypoint
- Set calculated waypoint

The `planning_utils.py` are consist of

- create grid
  - This will create grid with obstacles
  - The path way will be clear for safty fistance and altitude that we have set
- valid action
  - return list of action that the drone can go in the current node
- a star
  - Find a pathway
- heuristic
  - Find the cost of each cell position.

### Implementing Your Path Planning Algorithm

#### 1. Set your global home position

#### 2. Set your current local position

#### 3. Set grid start position from local position

#### 4. Set grid goal position from geodetic coords

#### 5. Modify A* to include diagonal motion (or replace A* altogether)

#### 6. Cull waypoints

### Execute the flight

#### 1. Does it work ?

It works!