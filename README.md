# BloodhoundCypherQueries
A concise collection of BloodHound-compatible Cypher queries created at Penva Security. Use this repo as a library of inspected, annotated queries you can run in BloodHound/Neo4j during engagements or research.

<br>

# Cypher Queries

## **View all GPOs applied to a specific Computer**
**Description:** Find all GPOs that are applied to any specific computer. This query identifies GPOs that are applied at both the Domain Level and the OU level. Replace `COMPUTER_NAME` with the target computer name or a substring. (Make sure to input the exact computer name here, as this is case-sensitive)

**Query:**
```
MATCH (gpo:GPO)-[:GPLink]->(Base)-[:Contains*..]->(c:Computer) WHERE c.name CONTAINS "COMPUTER_NAME"
RETURN gpo
```
**Tested On:** BloodHound v8.1.3/SharpHound v2.7.1
