# Robot Action Planner

Welcome to the Robot Action Planner project! This project provides a framework to help you plan action scripts for robots to execute tasks. Whether it's controlling a household robot or a laboratory robot, you can generate actionable scripts by adhering to strict rules and limitations based on user intent.

## Prompt
See file [Home robot planner.txt](#)

## Features

- **Role Definitions:** robot controller, allowing for the creation of action scripts.
- **Fundamental Elements:** Encompasses objects, actions, states, and rooms, clarifying the scope of operable elements for the robot.
- **Context Control:** Imposes strict regulations on the use of actions, objects, states, and rooms, ensuring a rational plan.
- **Practical Examples:** Offers real-world scenarios to demonstrate how to convert user intent into action sequences.

## Usage Guide
Copy and paste prompt from [Home robot planner.txt](#) into ChatGPT (GPT4 is recommended). <br>
It will follow the process defined in the prompt
```plaintext
1. Read the above introduction to understand the project's background and functionality.
2. Adhere to the context control rules and limitations, and devise action scripts based on user intent.
3. Review the thinking process behind correctly generating action scripts in the provided examples.
4. Adapt user intent and objects from the examples to create your custom action scripts for your tasks.
5. Employ the generated action scripts to control robots for task execution.
```
Just input what you want the robot to do, and it will output the script that the robot needs to execute
## Examples

Below are two examples showcasing the application of context control and rules to generate action scripts:

**Example 1:** User intent "watch movie"

```plaintext
Think aloud:
- What object can play a movie? Answer: tv
- Where is the TV? Answer: usually in the living room
- Does the robot need to change rooms? Answer: no, it's already in the living room
- What's the first action? Answer: checkstate (standup)
- What's next? Answer: find (tv), switchon (tv), declaredone
Action script:
checkstate (standup)
find (tv)
switchon (tv)
declaredone
```

**Example 2:** User intent "throw away lime"
```plaintext
User intent: throw away lime
Think aloud:
- Where is the lime located? Answer: Assume it's on the kitchen table.
- Is the kitchen table an object in the Object List? Answer: Yes.
- Where is the kitchen table located? Answer: In the kitchen.
- Where can the robot throw away the lime? Answer: In the garbage can, which is an object in the Object List.
- Where is the garbage can located? Answer: Also in the kitchen.
- Does the robot need to change rooms? Answer: Yes, from the bedroom to the kitchen.
- What action should the robot do first? Answer: checkstate (standup).
- What action can move the robot from one room to another? Answer: moveto (room).
- What is the target room? Answer: Kitchen, so moveto (kitchen).
- What is the next action the robot should do? Answer: find (lime).
- Is find (object) a legitimate action in Action Primitives? Answer: Yes, it can be applied to lime (an object in the Object List).
- What action should the robot do next? Answer: grab (lime), which is a legitimate action applicable to lime.
- What is the next action the robot should perform? Answer: find (garbagecan), which is a valid action in Action Primitives and is applicable to the garbage can.
- Does the garbage can have a lid? Answer: Yes.
- What action should the robot do next? Answer: open (garbagecan), and it is in Action Primitives.
- Is open (object) applicable to the garbage can? Answer: Yes, the garbage can is a valid object in the Object List.
- What action to do next? Answer: Apply putin (object, object) to lime and the garbage can, so the action is putin (lime, garbagecan).
- What action should the robot remember? Answer: close (garbagecan).
- Finally, what last action should the robot do? Answer: declaredone.
Action script:
checkstate (standup)
moveto (kitchen)
find (lime)
grab (lime)
find (garbagecan)
open (garbagecan)
putin (lime, garbagecan)
close (garbagecan)
declaredone
```

## Troubleshooting

If you're unable to generate valid scripts due to missing objects, actions, rooms, etc., carefully review the context control rules and limitations, ensuring alignment with the provided thinking process.
