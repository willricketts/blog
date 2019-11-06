---
layout: post
title: Rhea's Galaxy Map
description: Adventures in DAGs, Graph Databases, and 
---

In the [last post](https://willricketts.com/2019/introducing-rhea/), I covered the various game titles and mechanics they utilize that I've drawn inspiraation from for the design of Rhea. In covering Rhea's galactic map, I'd like to focus upon two of them heavily-- Eve Online and Stellaris.

### Inspiration

Eve Online and Stellaris have very similar map systems. Both have solar systems represented in a DAG-like structure. The DAG's nodes represent solar systems. In the case of Eve Online, this structure's edges are representative of Stargates, and in Stellaris, warp lanes between solar systems.

In any case, both systems function in a similar way, in that players and their fleets traverse a large DAG to move around the galaxy.

#### Stellaris

Based on a system of ephemeral matches, Stellaris's game maps are generated uniquely for each. Thus, each time the player creates a new empire or species and starts a game, a new map is generated and configured via the player's selected settings when creating the game.

![](https://s3.amazonaws.com/images.willricketts.com/rhea/stellarismap.jpg)

#### Eve Online

Eve's map is persistent, in that the game has no concept of "rounds" or "matches." The game map, save for additions by their publisher, has and will remain the same since the release of the game in 2003. Being that the intent of Rhea is to be a single persistent game world, this is the path I've elected to follow.

![](https://s3.amazonaws.com/images.willricketts.com/rhea/evemap.png)

### Map Requirements

### Generating the Map

![](https://s3.amazonaws.com/images.willricketts.com/rhea/rheamapsmall.png)

![](https://s3.amazonaws.com/images.willricketts.com/rhea/rheamapclose.png)

#### First Attempts

#### Enter Diffusion Limited Aggregation

### Future Plans

#### Wormholes

#### Tactical Structtures