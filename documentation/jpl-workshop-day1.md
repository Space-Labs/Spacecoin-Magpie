# Introduction to Space Mission Software and conops

## 21 OCT 2024

## Questions
1. CI/CD, good strategy is to have a golden binary stored in redundancy in disk, that the OBFS will revert back to on any reboot loop, or other non recoverable anomoly. This golden binary is never changed and was launched with the spacecraft

2. Rad tolerant, read/write idle task whereby you write bits and read back, and if you see an incorrect bit (non ECC corrected bit flip), revert to a high rad safe mode

3. Unit testing, can developers define expected set of driver inputs/outputs, such as waveforms, as part of testing harness for unit tests? Yep! Unit testing harness of standard drivers are included, and mocked values, signals, etc, can be implemented by the developers to unit test function level behaivior in the Application or Manager layer


## Presentation notes
1. Concept of Hardware [Perhipheral (Payload, Power, Telecom)] <---> [I/O Device] <---> [Processor (Software)]
2. Modularity, Reusability, and Testability
3. Decompose softwae into parts, sep of functions, def of interfaces, behavioral characteristics
  a. rate groups, concurrency, data flow
4. Test at unit level, Ownership
5. COncept of Software: [Application] ---> [Manager] ---> [Driver]
6. You should not be calling up the stack (Driver calling to Manager), really you should only be polling, or registering interrupt callbacks. Tradeoffs of these two strategies will be discussed later.
7. 


## F' Software Architecture
1. Software architecture is the glue / foundation that holds the software together
2. mitigates software chaos
3. F' is an architecture and provides a way of components communicaitng with one another, encapsulates tasks, queues, etc, Pub/Sub, Pipes and filters, client-server, database, etc
4. F' is a component style architecture, this hasn't been the classic JPL architecture in the past. Tyically, it has been multithreaded module based architecture, communicate thru events and queues
5. In a component based architecture, there is a well defined interface with input/output ports. No symbolic dependencies on other components. Components can be loaded, compiled, and executed independantly. Components encapsulate threads, queues, and state machines.
6. Module coupling, the extent that modules (components) are relates to each other, examples of high coupling (bad) control coupling one component controls the flow of another component by passing what-to-do flag. data coupling, components share common state. We want low coupling
7. Portability, software is portable to a desktop workstation. Hide OS adaptation layers.
8. Reuseability, use frameworks, libraries, algos, etc
9. No dynamic mem alloc after init, limit class heierahy, iontegerty asserts, resource constrained performance. if code is ugly its probably wrong
10. port is a small slim header file that describes interface. interface is done only thru the ports.
11. Component is a state machine and the developer is writing the input port handler. All components have queues. So they are statemachines at the end of a queue
12. Requirements are typically layered: mission, project, system, subsystem, flight softwqre, and component requirements. Requirements are traces up and down.
13. Flight software requirements: Concise, unambiguous, testable, and a "shall" statement
    a. help you, the developer, to know WHAT you are implementing. Avoid nasty surprises when your software is devlibered
    b. Example: The FSW shall produce spacecraft health information via telemtry
        -Spacecraft health information consists of the following.... i.e. understand the notion of telemetry
    c. Example: The FSW shall allow ground operators to change parameter values defined in the parameter dictionary
14. Before design and code, first answer: What are we building, WIHTOUT answering the question how do we implement it?
15. If you are doing F', you are signing up for a point to point architecture, not a functional architecture.
  a. Can components have shared or different clock domains, a functional approach gives you immutability
16. Components are input, output, and state, consist of process as a state machine. Boring down deeper, components can have components.
    a. From a cubesat hardware interface diagram, for example, a set of software components can be defined from hardware components
    b. as an example, from drilling into the GNC component,  can be attitude conttrol, state handler, position determination, and input handler
17. data flow diagram DFD specify flight software interfaces, flow of data processes, data stores / state, natural transition to implementation, so for example, you may have a GPSMgr component, RadioMgr component, IMUMgr component, UARTDrv, etc
18. In the end, you want your design to look like a topology diagram, using the FPP modeling langiuage, and can specirfy the whole topology into the F' modeling language
19. For each component create a crisp notion of state with a state-machine that has following identified:
    a. discrete state
    b. signals thats cause state transitions
    c. actions that are invoked on transition
    d. state entry and exit behaivior
20. Encapsulate state maching logic within a _single_ function, or at least single class
21. avoid fuzzy notiuon of state with boolean flags, scattered logic
22. So three different concepts of components: Drivers, Managers, and Application

Quantom Modeler Checker, for state machine. Or specify in PlantUML.
github.com/JLOpenSource/STARS
sepcify your FPP, generates your base class

Capability already exists within F' to determine duty cycle for all rate groups, for hardware compute resource estimation