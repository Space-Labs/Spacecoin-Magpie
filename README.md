![Magie logo](https://github.com/Space-Labs/Magpie/blob/main/documentation/Magpie-logo-200px.png?raw=true)
# Magpie: Autonomous Onboard Flight Software for Space Network's CTC Satellites

Property of Space Telecommunications, Inc, 2024, No Public License, at this time.
Not Export Controlled (EAR-99)

### Introduction
Magpie is an open-source onboard flight software designed to control the key operational aspects of CTC (Creditcoin) satellites as part of Space Network's 5G-NTN global constealltion. Its core functionality includes managing various "flight modes," automating satellite maneuvers, and enabling seamless integration with the decentralized Spacecoin network for a trustless space economy.

### Key Features
- Flight Mode Control: Magpie governs the satellite's flight modes, determining when and where to point its antenna, adjust solar panels, and activate/deactivate payloads such as radios and amplifiers based on mission needs.

- Autonomous Orbital Monitoring: The software continuously monitors the satellite's orbital elements and state vector, such as altitude, velocity, and relative position to co-orbiting satellites—and determines when to execute fuel-efficient delta-V maneuvers to optimize the satellite's altitude for the entire plane or ring.

- Future Blockchain Integration: Magpie is designed to interface with the Spacecoin blockchain, allowing satellites to gain network-wide, trustless context. In this future version, satellites will autonomously bid for airtime and coordinate with the network in a decentralized manner.

### Built on NASA's F Prime Framework
F´ (F Prime) is a component-driven framework that enables rapid development and deployment of spaceflight and other embedded software applications.
**Please Visit the F´ Website:** https://fprime.jpl.nasa.gov.

Magpie is built upon NASA's F Prime (F´), a flight software framework developed by the Jet Propulsion Laboratory (JPL) for small-scale space missions. F Prime provides a robust, modular architecture that allows mission developers to quickly assemble and customize flight software for spacecraft. By leveraging this proven framework, Magpie benefits from the following core features of F Prime:
- Component-Based Architecture: F Prime’s component-driven approach enables Magpie to be constructed from reusable, independent software modules. This ensures flexibility and maintainability, allowing the satellite to manage various systems—such as antenna control, power distribution, and payload activation—independently and efficiently.
- Portability and Scalability: F Prime is designed to be lightweight and portable, making it an ideal foundation for Magpie's use in CubeSats and other small satellites. It supports both flight and ground system operations, ensuring that Magpie's functionality can be extended across the satellite constellation with minimal overhead.
- Real-Time Operations and Fault Tolerance: With its real-time operating capabilities, F Prime allows Magpie to monitor the satellite’s orbital dynamics and autonomously adjust its operations. Its built-in fault management system enhances the reliability of the spacecraft by detecting and responding to anomalies, helping maintain mission success in the harsh conditions of space.
- Flight-Proven Heritage: F Prime has been flight-proven on multiple NASA missions, such as the Mars Cube One (MarCO) mission. This heritage gives Magpie a solid foundation, ensuring that it can perform in demanding, real-world space environments.

By building Magpie on top of F Prime, we harness the power of a reliable, extensible, and scalable software framework that is well-suited for managing complex satellite constellations and future integration with decentralized space networks.

