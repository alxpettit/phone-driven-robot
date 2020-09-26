# Designing a Robust STEM Education Robot

### Project goal summary

This project centers on creating and building a cheap robotics platform that uses a phone as its brain. The long term idea behind this will be to prototype a STEM education system that reuses old android phones as the control system, combining it with a simple 3D printed base. This will be a complex multi-stage process, and I believe the software portion of it is the most important. Thus, for the time being I will be using a Lego kit for the hardware, with some custom parts and additions.

This robot will be designed and built with the potential for providing an introduction to robotics for teaching Science, Technology, Engineering, and Math, to young and old people alike – by providing them with a cost effective solution reusing existing outmoded devices that already exist in most people’s homes. The goal of this in the long run will be to be transparent, open source hardware and software that is hacker-friendly and amenable to customization. This will be primarily a concern of the hardware elements, which is beyond the scope of this quarter.

### Control (client side)

The client side control system consists of a phone (programmed via Java Android app) connected through some sort of serial connection to an Arduino board (programmed via C++)

#### Control (server/user side)

The primary means of control is planned to be WiFi – the first implementation of this is planned to be in Flask. I chose Flask because it seems to require a lot less boilerplate than Django, but it’s still in a language I’m very familiar with – Python. At the same time, I am rusty in HTML and Javascript, and I will likely need to make quite a few templates for both to get a prototype remote control interface. The server backend and frontend will be fairly monolithic, but I will make some effort to have the remote control API separable so that it can be implemented in other systems down the line without too much refactoring or reimplementation.

### Challenges & learning goals

The project will involve making both my first Android SDK app, and my first Flask app. It will require me to design my own protocol for communication between these systems, and design an overarching network of mutually interfacing systems. I am hoping this can be a multi-quarter project as I doubt it all can be finalized within a single quarter.

By the end of this quarter, I believe I will feel comfortable applying the knowledge of Intellij-based IDEs and Java, which I learned in the previous quarter, to Android development. I will have knowledge of Android APIs such as USB access or audio (depending on how I choose to interface the control phone), as well as constructing a basic GUI.

I also will have gained experience writing Flask apps -- I believe the workflow I developed for Java should be even more applicable to Python for preventing runtime errors (e.g., using PyCharm instead of a simpler IDE).

I find in my development process that I rely too much on real-world testing rather than making unit tests for my libraries. I believe the broad span and multiple systems involved in this project will force me to practice designing code that's sufficiently modular and with enough unit tests to be maintainable, despite real-world tests taking so long.

Finally, I will also gain experience in designing protocols for multiple systems. The controller will have to communicate with the phone, which will then have to communicate with the arduino. I will be building my own protocol for each of these connections.

### Software

The software design of this system will stretch through multiple programming languages and systems, and four devices. The devices are:

* Robot-mounted arduino
  * programmed in C++ via Arduino devkit
* Robot-mounted phone
  * programmed in Java via Android SDK
* Cloud control software
  * programmed in Python via Flask
* Client browser controlling the robot
  * via Javascript+HTML

The software information flow chart is basically a straight line through the following systems:

* User control webpage (client machine that the user sits at to control the robot)
* Server GUI (VPS)
* Server API (VPS)
* Client API (robot-mounted phone)
* Robot control logic (robot-mounted phone)
* Serial controller API (robot-mounted phone)
* Serial controlled API (robot-mounted Arduino)
* Motor control wrapper API (robot-mounted Arduino)

Information can in-principle flow in either direction through this list, but I will be focusing on the top-to-bottom flow in my initial design. Sensors will probably be more of a long term goal rather than something I'll do early on in the project.

### Development flow & planning

Since there is so much to this project, I believe a structured plan is very important. Thus, I have decided to work backward, starting from the robot itself. I will begin by building the electrical system for controlling the motors, and the Arduino's code, followed by the Android control app. Working between these two systems, I should be able to devise a protocol for them to communicate. This is one of the trickier parts of the project.

Only after I have a working control system from phone to robot, will I begin working on interfacing the Flask app to the phone itself.

### Research questions

* Will the connection be laggy? How can response time be optimized?
* Can I minimize reliance on polling? Event-driven programming is much more efficient in reducing bandwidth, if possible.
* Can I feasibly leave space in each module for future changes without implementing those changes?
* Can I design unit tests for each module that'll catch most errors before a real-world test encounters them?
* Can I feasibly design a protocol to make serial control of the robot possible without encumbering the phone's audio input jack or preventing the phone from charging?
* Can the code produced from this project eventually be used to make a professional STEM education crowd-funded robotics product?