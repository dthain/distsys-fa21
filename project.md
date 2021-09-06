---
layout: default
title: Course Project
---

# Course Project for Distributed Systems

## Requirements

The final project in this course will be open ended.  You will propose, carry out, and report upon a project in groups of **two*** students.
Projects must have the following elements:

- **Build a System** - Your project must involve constructing a system of some complexity
that deals with some of the challenging problems of distributed systems, such as reliability, consistency,
replication, and so forth. If you make use of existing software or packages, then you must build something
substantially new on top, and not just plug a few things together. Python is recommended as a starting point, but you may use
another language or environment if there is a strong reason to do so.

- **Evaluate its Performance** - The performance of your system must be evaluated carefully, in
a manner appropriate to the nature of the system.  For example, if your system is designed to be
scalable, then you should evaluate throughput and latency as the number of nodes increases.
Or, if it is designed to be reliable, then you should evaluate its performance when nodes fail.
Or, if it is designed to be consistent, then you should evaluate the latency of update propagation
under various conditions.  Think carefully about the appropriate evaluation for your system.

- **Present it Clearly** - Present your work cogently by writing a paper and making an oral presentation.
The paper should describe the motivation, design, evaluation methods, and quantitative results of your project.
The oral presentation should summarize the most important aspects of the paper and give a demo of how it works,
during the last week of class.

## Project Ideas

Following are some ideas to get you thinking.  You are welcome to modify one of these ideas,
or to pick a different problem, but talk to Prof. Thain first if you have something radically different in mind.

**Peer to Peer Chat System** - Build a system that allows for interactive chat
between many users, without requiring any centralized server.  Each participant
in the system should have their own independent node that passes chat messages
back and forth.  Consider how to discover other nodes, pass messages to the rest
of the system, put messages in a suitable order, and how to deal with disconnections
and outages.  Measure the latency and throughput of message dissemination as
the system grows in size.

**Scalable Filesystem** - Build a file storage system that can scale up to a large
number of nodes.  One approach to this is to create a single "name" node and multiple "storage" nodes.
The name node can keep track of the filesystem tree, file names, and the location of the files on the storage nodes.
To access a file, a client must interact with the name node to locate it, and then the storage node to access it.
Consider how to choose where to put files, where to replicate files, and how to deal with node outages.
Measure both the latency and performance of the system as the number of clients and servers increases.

**Log Oriented Replication** - Build an asynchronous chain-replicated version of your distributed hash table project.
Instead of having each node **wait** for the next node to respond (which would make the system very slow),
make use of the transaction log.  As a single node applies changes to the transaction log, arrange for those
log entries to be passed on to the next system in a row.  Careful: When is it safe for one node to compress
its own log?  Consider how a new node joins the system, and what happens when a node crashes.
Evaluate the throughput and latency of the system as the number of clients and servers increases.

**Distributed Interactive Game** - Create a simple multi-player interactive game, where a centralized
server manages the game and players must interact from client nodes.  The game could be an old-school text
adventure (explore rooms, collect items, etc) or something more graphical if you are so inclined.
Design into the game some actions that are mutually exclusive, requiring the server to perform a total
ordering on the actions and return the results to the client. For example, if user A roasts a marshmallow on a fire,
while user B *concurrently* puts the fire out with water, what's the outcome?

**Peer-to-Peer Hash Table** - Implement a distributed hash table in a circular peer-to-peer fashion,
following the design of Chord, as described in the textbook.  Note that most of the description focuses
on how to **find** items in the system.  This is important, of course, but you must also consider how
nodes enter and leave the system, and arrange for data to be copied and preserved.

**Distributed Data Preservation System** - Design a peer-to-peer preservation system.
Suppose that a user wishes to preserve some document **forever**.  If the user delivers
it to any one node in the system, then that node should take active
steps to communicate with other known peers to make further copies of
the document.  Be careful to ensure that the system can recover from
the loss of multiple nodes, but is also not causing continuous unnecessary network traffic.
You may borrow ideas from other systems such as Gnutella
Freenet, or Chord, provided that you implement the system yourself.
Start by reviewing section 4.5.2 in the textbook.

**Reliable Data Delivery System** - Build a chained message
queueing system like that described in section 4.3.  It should consist
of a message forwarding process that reads files from a directory and then
delivers them to an identical process running on another machine,
which stores them in a directory where could be read by another
forwarding process.  Make sure that your system can handle expected
failure modes such as server crashes, network outages, full disks.
Evaluate the throughput of your system on a large amount of data.

**Distributed Board Game Engine** - Pick a common board game  -- Chess, Othello, Go, etc -- that
has many configurations and is thus computationally difficult for a computer to play effectively.
Take an existing solver for this game that works on a single node, and build a distributed system
that can run it on multiple nodes at the same time, playing against a human user.
In this way, the difficulty of the "computer" player can be expanded to as many nodes as desired.
Measure the time to reach a solution of a given quality, and the amount of the configuration space
that can be explored in a fixed amount of time.

## Milestones

**Project Proposal - Friday, October 15th** -
Turn in a document that describes the overall shape of your project.
This should include the project partners, a high level description
of the goals and structure of the system, identification of the key
"distributed system" problem in the system, 
what languages and resources will be necessary to carry it out,
and your plan for evaluating the system.  The proposal should be
about two full pages of text.  The instructor will follow up with
you to make sure that the project is of appropriate size and difficulty.
**Submit this via the Assignments tab in Sakai.**

**Progess Report - Wednesday, November 17th** - Turn in a two-page
report describing your progress so far.  Include a more detailed
description of your system, including the details of the processes involved,
the messages exchanged, and how the key "distributed systems" problems
will be addressed.  Include a screenshot or other evidence to demonstrate
that the basic technology is setup and working.  Indicate your progress
toward completion and any challenges or problems discovered along the way.
**Submit this via the Assignments tab in Sakai.**

**Class Presentation** - During the penultimate week of class, you
will give a ten minute presentation to the whole class.
(Time may vary once number of projects is known.)
The talk should include an overview of the goal or problem, the structure of your
system, an example of how your system operates, and your results from evaluating
the system so far. Your talk should be accompanied by 5-10 carefully designed
and edited slides.  While this is a short talk, it will require careful preparation
in order to be detailed, informative, and on time.

**Final Submission - Tuesday, December 7th** - Turn in your code and the final paper.
The code should be structured such that the instructor can build and
execute it independently.  The paper should give an overview of the
goal or the problem, a detailed description of the structure of your
system, including a good diagram where appropriate, and an evaluation
of the correctness and performance of the system.  There is no specific
length requirement; the paper should be long enough to explain all
of the necessary details.  The said, anything less than five pages
is probably too short; anything longer than fifteen pages is probably too long.
**Submit your final report as a PDF via the Assignments tab in Sakai,
and your final code into the dropbox directory on the student machines.**


