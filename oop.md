Objects encapsulate state and to interact with this state you send messages to object's api, object in turn can comunicate with other objects. OOP is a graph of objects, that comunicate with each other by sending messages. Objects are state. Sending messages ~ calling methods.  
When building new system be careful with imposing structure early on. Better to start out with a free-form absence of structure than impose a structure that will likely turn out to not realy fit problem. Bad structure makes harder to implement code, hinders (meshat') change and makes code more confusing.  
Graphs:
- inheritance hierarchy
- composition graph
- data flows between the objects
- call graph  

Procedural:
- call graph
- how data is structured and how it flows, is being transformed  

Abstraction: simplified interface over complex inner workings.  
1. Parametrize
2. Bundle globals into types, structs (classes).
3. Favor pure functions. https://en.wikipedia.org/wiki/Pure_function   

Idea: Module is a namespace and it has state and api.

