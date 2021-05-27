# Project Overview
Researchers often capture, tag, and release animals to study their environment and movement patterns.  Because the animals can be quite small, the tag includes small sensors that intermittently emit a signal to indicate the animal's current location.  The batteries attached to the animals must also be small, so the sensors' signals may be very weak to save power.  A researcher who has tagged and released an animal typically must go through a laborious manual process to track the animal's movements over time.  This process involves a human lugging around a large antenna while trying to detect the signal from the animal's sensor.  Once a signal is detected, the human moves in that direction, looks for the signal again, and repeats the process until the animal is found.

The Radio Telemetry Tracking (RTT) project intends to optimize this process by deploying drones to detect and track the signals from the animal's sensors instead.  The drone has several sensors of its own on-board that allow it to optimize its flight path to more accurately determine the animal's location.  Because the drone's hardware and scanning tools can be controlled via software, the drone is able to track multiple animals within a single flight, further optimizing the tracking process.  To allow for ease of use and monitoring, the drone transmits its status and tracking information to a system on the ground, allowing the researchers to view the progress in real time.

This repository serves as a collection of information specifically for the Spring 2021 offering of CSE 237D.  To avoid duplicating information, this page presents information specific to my goals for the quarter.  For up-to-date information, please see the content referenced by the [Relevant Links](#relevant-links).  Note that most of the design-level documents are stored in a separate, private Google Drive and are not linked below.

# External Team Members
- Dhiren Lad: I am the only person working on the RTT project this quarter that is also enrolled in CSE 237D.  All goals mentioned below are mine (unless explicitly mentioned that the work is split with another team member).

# Goals for the Quarter
## Simulator
[Link to relevant code commits](https://github.com/UCSD-E4E/radio_collar_tracker_uib/compare/v1.0a_NH1...v1.0a_DL1)

Since the team needs to work remotely while Covid-19 restrictions are in place, the team built a simulator to enable development to continue.  My initial task involved updating the simulator to ensure that it is up-to-date with the drone's specifications, as well as the APIs for the on-board sensors.

## Communication Between OBC and UI Board
[Link to relevant code commits](https://github.com/UCSD-E4E/radio_collar_tracker_uib/compare/v1.0a_NH1...v1.0a_DL0)

The User Interface (UI) board is responsible for reading the data from the sensors while the On Board Computer (OBC) is responsible for taking the data and dispersing it to the parts of the drone and Ground Control System (GCS) that need it.  This task involved implementing communication over the Serial channel from the OBC to the UI board.  This involved both receiving the data packets from the UI board, as well as sending heartbeats containing the drone's status to the UI board.  Since I was working on this task in parallel with other group members, the commits displayed above implement the logic involving parsing and storing the data packets.

## Testing the UI Board Software on the Physical Drone
All of the above work was done in a simulated environment.  The goal of this task is to launch all of the software on the physical drone to verify:
- The UI board can successfully read from all of the sensors
- The UI board can correctly package the data and send it into the Serial channel
- The OBC can receive the information and log it to the screen (since it is not guaranteed that the OBC's functionality will be complete when this task starts)

# Relevant Links
- [RTT E4E page](http://e4e.ucsd.edu/radio-collar-tracker)
- [RTT GitHub](https://github.com/UCSD-E4E?q=radio&type=&language=&sort=)
    - Note that my work is all contained within [radio_collar_tracker_uib](https://github.com/UCSD-E4E/radio_collar_tracker_uib) which holds all code for the UI board
