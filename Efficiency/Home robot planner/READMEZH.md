# 机器人动作计划器

欢迎来到机器人动作计划器项目！这个项目提供了一个框架，帮助你规划机器人执行任务的动作脚本。无论是控制家务机器人还是实验室机器人，通过遵循严格的规则和限制，就可以根据用户意图生成可操作的脚本。

## 功能特点

- **角色定义：** 机器人控制者制定动作脚本。
- **基本要素：** 包括对象、动作、状态和房间等，明确了机器人可操作的范围。
- **上下文控制：** 严格规定了动作、对象、状态和房间的使用限制，确保合理的计划。
- **实用示例：** 提供实际例子，展示如何根据用户意图生成动作脚本的过程和结果。

## 使用指南
将 [Home robot planner.txt](#) 里的 prompt复制粘贴到ChatGPT中（建议用GPT4)就可以了。<br>
它会按照prompt里定义的流程执行
```plaintext
1. 阅读上述介绍，了解项目的背景和功能。
2. 遵循上下文控制规则和限制，根据用户意图思考并生成动作脚本。
3. 在示例中查看正确生成动作脚本的思考过程。
4. 针对你的任务，替换示例中的用户意图和对象，生成自己的动作脚本。
5. 将生成的动作脚本用于控制机器人执行任务。
```
和它对话只要输入你要让机器人做的事，他就会输出机器人需要执行的脚本
## 示例

以下是两个示例，展示了如何应用上下文控制和规则生成的动作脚本：

**示例 1：** 用户意图 "watch movie"

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

**示例 2：** 用户意图 "throw away lime"
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
## 告知问题

如果由于缺少对象、动作、房间等而无法生成有效的脚本，请仔细检查上下文控制规则和限制，并确保遵循示例中的思考过程，自行添加对象。
