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

One of the major strategies when starting a game of Stellaris is to rapidly expand to claim and build defenses around choke-point systems, or systems that have many connetions as to control the flow of traffic through that portion of the map. This is a side-effect of this glactic map model that I'm intent upon creating.

![](https://s3.amazonaws.com/images.willricketts.com/rhea/stellarismap.jpg)

#### Eve Online

Eve's map is persistent, in that the game has no concept of "rounds" or "matches." The game map, save for additions by their publisher, has and will remain the same since the release of the game in 2003. Being that the intent of Rhea is to be a single persistent game world, this is the path I've elected to follow.

Some very desirable but non-obvious effects arise from this kind of model for a galactic map. With a static map, various regions or sections of it become known within the playerbase for being better or worse to own from a strategic perspective. Eve has regions of the game that are notoriously difficult to invade, and has a few that are notoriously favorable for an invading military to stage their assets.

![](https://s3.amazonaws.com/images.willricketts.com/rhea/evemap.png)

### Generating the Map

Creating a map of this size and detail was a challenging problem to solve, and at the time of this writing, still presents obstacles to overome to achieve an optimal map structure

#### First Attempts

When I first sat down to work on figuring out the most immediate challenges in building Rhea, my intent was to get something simple working and then expand upon the idea later. Upon researching how I would go about generating a map of this nature with DAG-like properties, I found [Astrosynthesis](https://www.nbos.com/products/astrosynthesis), a piece of software used for generating celestial structures primarily for role-playing games and hobbyist world-building. This program had a bunch of great features that'd be super useful for my needs, but two features stood out in particular. Astrosynthesis has a user-created plugin ecosystem and an XML exporter. 

![](https://s3.amazonaws.com/images.willricketts.com/rhea/astrosynthesis.png)

Before long, I had a galaxy containing ~20 solar systems and connections between them, which I exported to a large XML document, which I was able to load into the Elixir-based backend of Rhea with [elixir-xml-to-map](https://github.com/homanchou/elixir-xml-to-map).


#### Using the Data

From this _very_ large map, I perform a series of mutations on the data to order it into a list of Solar Systems and one of Gates. With these lists, I first created a DB record for each of the solar systems within PostgreSQL. With a SolarSystems table populated with data, I would need to represent the data somwhere that graph-oriented data feels right at home. This is where [Neo4j](https://neo4j.com/) comes into play.

If you're unfamiliar, Neo4j is a graph database. This turned out to be the perfect tool for Rhea. It was immediately apparent that its Cypher query language had the features needed to power several in-game systems for Rhea. Namely its ability to find the shortest path between nodes, or in the domain of Rhea, solar systems.

#### Enter Diffusion Limited Aggregation

![](https://s3.amazonaws.com/images.willricketts.com/rhea/rheamapsmall.png)

![](https://s3.amazonaws.com/images.willricketts.com/rhea/rheamapclose.png)

### Future Plans

#### Wormholes

#### Tactical Structtures