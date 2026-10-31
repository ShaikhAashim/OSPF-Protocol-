# OSPF Routing & Network Failure Recovery
A Cisco Packet Tracer project demonstrating OSPF dynamic routing, cost-based path selection, and alternate-route recovery when a network link fails.


## What Is OSPF?

OSPF stands for Open Shortest Path First. It is a dynamic Interior Gateway Protocol (IGP) used to exchange routing information within an autonomous system.

OSPF is a link-state routing protocol. Routers discover neighbouring OSPF routers, exchange link-state information, build a Link-State Database (LSDB), and run the Shortest Path First calculation to determine routes.
How OSPF works
1. Neighbor discovery: OSPF routers send Hello packets to discover and maintain relationships with neighbouring routers.
2. Exchange link-state information: Routers share Link-State Advertisements (LSAs) describing network topology information.
3. Build the LSDB: Routers in the same OSPF area maintain a topology database.
4. Run SPF: Each router uses Dijkstra's algorithm to calculate the shortest/lowest-cost paths.
5. Update the routing table: The best routes are installed in the router's IP routing table.
6. React to topology changes: When a link fails or returns, OSPF updates its topology information and recalculates routes.

## OSPF Link Costs
(values in the yellow box)
### Connection	Cost
 Router0 ↔ Router2	20
 
 Router0 ↔ Router1	50
 
 Router2 ↔ Router3	50
 
 Router1 ↔ Router3	20
 
 Router0 ↔ Router3	25
 

## Example shortest-path calculations
### Router0 to Router1
- Direct: Router0 → Router1 = 50
- Through Router3: Router0 → Router3 → Router1 = 25 + 20 = 45
- OSPF prefers the route through Router3 because 45 is lower than 50.
### Router2 to Router3
- Direct: Router2 → Router3 = 50
- Through Router0: Router2 → Router0 → Router3 = 20 + 25 = 45
- OSPF prefers the route through Router0 because 45 is lower than 50.
### Failure example: Router0 to Router2
- Normal route: Router0 → Router2 = 20
- If the direct Router0–Router2 link fails: Router0 → Router3 → Router2 = 25 + 50 = 75
- After OSPF convergence, the alternate route can be used if all links on it are operational.

## How to Run the Project
1. Install or open Cisco Packet Tracer.
2. Clone or download this GitHub repository.
3. Open the .pkt file in Cisco Packet Tracer.
4. Wait for router interfaces and OSPF adjacencies to become operational.
5. Verify OSPF neighbours with show ip ospf neighbor.
6. Test PC-to-PC connectivity using ping.
7. Shut down the selected Router0–Router2 serial interface to demonstrate failover.
8. Inspect the updated routing table and test connectivity again.
9. Restore the interface with no shutdown.

## Files
- *.pkt — Cisco Packet Tracer project file
- *.png — Network topology screenshot

