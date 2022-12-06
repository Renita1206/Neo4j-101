# Neo4j-101
Introduction to Neo4j  

### Create Nodes and Relationships
- Create a node    
```
CREATE node_name;
```  
- Create a node with a label  
```
CREATE (node:label)  
```
- Create node with properties
```
CREATE (node:label { key1: value, key2: value,....})
```  
- Create a relationships  
```
CREATE (node1)-[:RelationshipType]->(node2)
MATCH (a:Actors), (b:Movies) WHERE a.name = 
"Tom Hanks" AND b.name = "Forrest Gump" CREATE (a)-
[:ACTED_IN]->(b) RETURN a,b
```
### Match
- Return all nodes
```
match(n) return n
```
- Return nodes based on condition
```
match(n) where n.property='value' return n
```

### Merge    
- Merge is a combination of create and match. It searches for a given pattern in the graph. It creates new node/relationship if it doesn't already exist.  
- Merge a node
```
MERGE (node: label {properties . . . . . . . }) return node
```
- Merge relationship
```
MATCH (a:Node1), (b:Node2)  
MERGE (a)-[r:RELATION]->(b)
RETURN a,b  
```

### SET  
- SET is used to create a new property for existing nodes  
- Set new properties for node
```
MATCH (node:label{properties...}) 
SET node.property1 = value1, node.property2 = value2 
RETURN node
```
- Set new label for node
```
MATCH (node:label{properties...}) 
SET node: new_label
RETURN node
```
- Remove property for node
```
MATCH (node:label{properties...}) 
SET node.property1 = null
RETURN node
```
### Delete and remove  
- Delete is used to delete nodes and relationships whereas remove is used to remove labels and properties
- Delete all nodes and relationships
```
match(n) detach delete n
```
- Remove property of  node
```
MATCH (node:label{}) 
REMOVE node.property 
RETURN node
```  
- Remove label of a node  
```
MATCH (node:label) 
REMOVE node:label 
RETURN node
```


### Some other useful clauses:  
- Order by - used to sort data  
```
MATCH (n)  
RETURN n  
ORDER BY n.property [DESC]
```
- Limit - to limit number of rows in output 
```
MATCH (n)  
RETURN n LIMIT 5
```
- Skip -  to skip initial few rows in result
```
MATCH (n)  
RETURN n SKIP 5
```
- With - used for chain queries  
- Unwind - turn a list into individual rows  
```
UNWIND [a, b, c, d] AS x 
RETURN x
```
- Count - count number of instances
```
MATCH (n:label)
RETURN count(*)
```
- Max - find maximum
```
MATCH (n:label)
RETURN MAX(n.property)
```
- Min - find minimum
```
MATCH (n:label)
RETURN MIN(n.property)
```
- Sum - finds sum of values
```
MATCH (n:label)
RETURN SUM(n.property)
```
- Avg - find average
```
MATCH (n:label)
RETURN AVG(n.property)
```



### Example Project  
<a href="https://github.com/Renita1206/Synthetic-Music-Dataset">Click here</a> for an example application of Neo4j

