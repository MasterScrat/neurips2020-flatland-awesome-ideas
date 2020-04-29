[**Zoom recording**](https://zoom.us/rec/play/vMclI-ChrzI3SdTH5ASDVKQsW47pL6yshCFKqPRfyBq8W3JXNQelbuBEZePOTRQ6jgkDzSDIx1Lf9JE-) - see below for timestamps

60:00 - Adrian: Flatland intro, time-expanded graph, Cooperative A*
66:00 - Guillaume: centralised vs distributed vs decentralised
* Centralised: performance guarantess but complexity explodes, provably unmanageable at large scale
* Decentralised: scalable, but may not be optimal
1:16:00 - 

![](imgs/Screenshot%202020-04-19%20at%2015.31.31.png)

1:19:00 - MAPF.
* Naïve centralized A*: exponential growth, doesn’t scale!
* Ok up to 5-10. Reasonable planning time usually considered at ~5min
* Decoupled approaches. Velocity planner: plan for all, then only adapt speeds. May lead to suboptimal solutions or even deadlocks. Not “complete” - may not find a solution even though one exists!
* Centralized and decoupled are two extremes - each with major problems.
* In the middle: dynamically-coupled approaches. Intuition: naïve approach works in most cases, except when it doesn’t. So: plan naïvely but fix the plan in smarter way when collision would happen. eg M*, CBS (SotA).
* CBS: creates 2 subproblems for each collision.
1:30 
* Dynamically-coupled: possible to specify a hard limit on how suboptimal results will be. In general those limits are never reached (by far) except in custom-made adversarial cases.

![](imgs/Screenshot%202020-04-19%20at%2019.32.50.png)

* But still around 150-170 agents! CBS a bit more but not much. That’s how far conventional planners work. Will never be able to do >500 agents for sure.
* "Given 10x for computing power, may be able to do 5 more agents 😞” exponential problem, Moore’s law won’t save us
* But already far far ahead what A* would do.
1:35
* Idea: “symmetric policies”, use standard RL learned state -> action mapping for each agent. One policy for all!
* Goes well with A3C: instead of running multiple envs, run a single env but consider the experiences of each agent!

![](imgs/Screenshot%202020-04-25%20at%2014.36.33.png)

1:41
* Uses field of view (= local) observations + compass + distance to goal
* Means agents don’t get exhaustive information, but fixed size is easier to handle for DL
* Also does 50% imitation learning

![](imgs/Screenshot%202020-04-25%20at%2015.55.00.png)

* Agent specifically learn to go out of the way when need be.

1:51
* Comparison with other methods given limited time

![](imgs/Screenshot%202020-04-25%20at%2016.37.28.png)

* M* suffers a lot with low density of obstacle, as any agent can collide with any other agent


























