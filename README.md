# Bully-Algorithm
Election Algorithm

Election Algorithms: The coordinator election problem is to choose a process from among a group of processes on different processors in a distributed system to act as the central coordinator. An election algorithm is an algorithm for solving the coordinator election problem. By the nature of the coordinator election problem, any election algorithm must be a distributed algorithm.
-a group of processes on different machines need to choose a coordinator
-peer to peer communication: every process can send messages to every other process.
-Assume that processes have unique IDs, such that one is highest
-Assume that the priority of process Pi is i

Bully Algorithm
Background: any process Pi sends a message to the current coordinator; if no response in T time units, Pi tries to elect itself as leader. Details follow:

Algorithm for process Pi that detected the lack of coordinator

•	Process Pi sends an “Election” message to every process with higher priority.
•	If no other process responds, process Pi starts the coordinator code running and sends a message to all processes with lower priorities saying “Elected Pi”
•	Else, Pi waits for T’ time units to hear from the new coordinator, and if there is no response à start from step (1) again.
 
Algorithm for other processes (also called Pi)
            If Pi is not the coordinator then Pi may receive either of these messages from Pj

            if Pi sends “Elected Pj”; [this message is only received if  i < j]

                        Pi updates its records to say that Pj is the coordinator.

            Else if Pj sends “election” message (i > j)

                        Pi sends a response to Pj saying it is alive

                        Pi starts an election.
