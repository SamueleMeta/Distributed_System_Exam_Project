# Distributed Job Scheduling

<p align="center">
    <img src="https://i.imgur.com/mPb3Qbd.gif" width="180" alt="Politecnico di Milano"/>
</p>

## Overview
The project about "Distributed Job Scheduling" is related to the Distributed Systems exam at Politecnico di Milano. The aim of the project is to model the following scenario:

* Each client may submit a job to any of the executors and check if the job has been executed, retrieving back the results produced by the job;

* Executors communicate and coordinate among themselves in order to share load. Links are reliable, but processes may fail and resume back, re-joining the system immediately after;

* Stable storage shall be used to cope with failures of executors;

We decided to perform the simulation on OMNeT++, a framework that helps in simulating any sort of network or distributed protocol.

## Job Scheduling

<p align="center">
    <img src="https://media.giphy.com/media/dThgOkLg6xUZWH9CN6/giphy.gif" width="600" alt="Simulation"/>
</p>

The proposed solution is a distributed protocol based on a variable number of client and executor nodes. Each client has a certain number of jobs to submit and each of them may require a different amount of time to process. The client can submit the job to any executor, which will propagate the request to all the executors' cluster. Even if this step involves a lot of messages over the network, its advantage is the achievement of an almost perfect load balancing, because the job will be assigned to the laziest executor. The chosen executor communicates with the client that is in charge to process its job and the client will be able to ping the executor for future updates. If no failure is involved, the client will receive from the executor the result of the computation, otherwise, after a timeout, the job will be considered lost and submitted again to another executor.

## Resources
This repository consists in:
* ```.msg``` files, modelling the main messages which allow clients and executors to exchange information during system execution
* ```schedule.ned```, which describes the network topology
* ```omnetpp.ini```, where the main parameters of the simulations can be easily set up
* the pdf of the presentation describing the main data structures and experiments

## Team
- Alice Casali [[Github](https://github.com/alicecasali)] [[Email](mailto:alice.casali@mail.polimi.it)]
- Samuele Meta [[Github](https://github.com/SamueleMeta)] [[Email](mailto:samuele.meta@mail.polimi.it)]
- Stiven Metaj [[Github](https://github.com/StivenMetaj)] [[Email](mailto:stiven.metaj@mail.polimi.it)]
