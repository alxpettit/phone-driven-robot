# Goals

* Build a small LEGO rover that is:
    * Possible to control over WiFi from anywhere in the world
    * Rechargeable
    * Analogous to a robot that could be sold, e.g. as a Kickstarter project.
    * Does not _principally rely_ on expensive parts would increase the manufacturing cost if this were mass produced (with the exception of the phone)

_Learning goal: produce prototype hardware that is durable and represents product ideas that can be scaled to bigger projects._

* The Lego rover is controlled by an Android app that is:
    * Lightweight
    * Able to be run on startup
    * Capable of sending arbitrary commands to an Arduino nano
    * Oriented around basic motor control
    * Simple UI with troubleshooting features -- e.g. manually sending commands to arduino through phone UI, for testing.
    * Modular code separated into classes that makes good use of OOP
        * Strive to avoid monolithic design!

_Learning goal: practice Java, and become comfortable with designing and writing simple Android apps_

* The Android app *Might* also...
    * Include video streaming
    * Include audio streaming
    * Include a programmable autonomous mode of some kind

* The control software is...
    * Written in either Django or Flask (probably Flask).
    * I do not know how to use either one and have very little web coding experience, so this would be a great learning opportunity.

_Learning goal: become competent in very basic web development._

# Technical challenges

### in order of easy to hard

* Design a Lego construct capable of securely mounting in place the required circuitry and moving freely with two motors. (Very easy)


* Build a self-balancing 18650 circuit capable of supplying rail voltage through buck converters (easy)


* Find a robust and low-latency way of controlling an arduino from an unmodified phone (Slightly challenging)
    * Initial idea: build a simple circuit for getting information out via audio channel. I already know enough about line levels and the arduino's precision to know that I could build a very crude serial connection -- could be an interesting challenge to design the protocol to synchronize the data clock on both devices and to get a high-baudrate low latency connection.
        * Drawback: could be cool to use audio channel for microphone so that the robot can react to sounds or relay them to the control app. I am not sure if it's possible to get two audio feeds simultaneously.
    * Alternative: [use OTG circuitry with charging capability](https://www.youtube.com/watch?v=cSSnsCO1xKw) This spares the mic/spk port for future use, and might simplify the project considerably. Another advantage is that this could also provide the option for OTA firmware updates.
        * Drawback: I've never tried this before and it might not work.
        * Drawback: ability to do OTA updates will result in vulnerabilities down the line


* Learn basic Flask or Django programming (probably Flask). Apply this knowledge to produce a cloud-style remote control system designed to interface with our Android app. (challenging)
    * Interface might be ugly -- I don't want to set my standards too high. The important thing is that it's possible to easily control the robot.


* Learn basic Android programming. Apply this knowledge to produce a functional app capable of performing all functions expected (challenging)

# Practical applications

This project could, in the future, be turned into some kind of 3D printable cheap robot base, for making robotics more accessible to people with old Android devices.
