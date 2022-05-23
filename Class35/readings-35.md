# Class-35 : Graphs


In this file I will be summarizing what I have learnt in class-35 reading notes which included the following resources :
- [Graphs](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/graphs.html).

## Graphs 
***

### Definition :  
A graph is a non-linear data structure that consists of **vertices** and **edges** that connects these vertices together, vertices can be either directed (one way connection) or undirected (two ways connection).
A vertex can have a **neighbor** which is an adjancent vertex that is connected to it by an edge , and vertex also have a **level** , which is nomber of edges connected to that vertex.


**Undirected graph** : 
![undirected graph ](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/UndirectedGraph.PNG)

**Directed graph** :

![directed graph](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/DirectedGraph.PNG)

directed graphs may have cycles, which means that a vertex can find a way to reach itself through other vertices so we call it a **Cyclic graph** otherwise we call it **Acyclic graph**. 
![Acyclic graphs](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/threeAcyclic.png)
from the picture you can find that :
- graph 1 and 3 are acyclic graphs which are also known as **DAG** or also **tree**.
- graph 2 is an undirected graph.  

Following you will find cyclic graphs.  
![cyclic graphs](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/cyclic.PNG)

**Weighted Graphs**  
A weighted graph is a graph with numbers (weight) assigned to its edges.   

![Weighted graphs](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/weightGraph.PNG)

### Types of graphs :

1. Complete Graphs : graphs which all vertices are connected to each other. 

![complete graph](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/CompleteGraph.PNG)

2. Connected Graphs : graphs that all vertices inside it have at least one edge .

![connected graph](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/ConnectedGraph.PNG)

3. Disconnected Graphs :  graphs that some vertices may not have edges so we call them **islands**.

![disconnected graph](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/DisconnectedGraph.PNG)

### Graph Representation
![undirected graph ](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/UndirectedGraph.PNG)

We can represent graphs in two ways :

1. Adjacency Matrix
The matrix representation means that there is an edge connecting x-element with y-element if (x,y) index was 1 and not if it was 0 . 

![Matrix](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/AdjMatrix.PNG)

or you can put its weight instead of putting 1 in case of weighted graphs as follows :

![weighted graphs matrix](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/weightMatrix.PNG)

a *sparse graph* is when there are very few connections. a *dense graph* is when there are many connections

Within an adjacency matrix, an undirected graph will always be symmetric. 

2. Adjacency List
An adjacency list is a collection of linked lists or array that lists all of the other vertices that are connected.

![List](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/AdjList.PNG)

in case of weighted graphs you have to add the weight of the edge with the vertex using a key/value data structure as follows :
![list with weight](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/weightList.PNG)


### Traversals :
There are two ways to traverse through a graph :
1. Breadth First
```
ALGORITHM BreadthFirst(vertex)
    DECLARE nodes <-- new List()
    DECLARE breadth <-- new Queue()
    DECLARE visited <-- new Set()

    breadth.Enqueue(vertex)
    visited.Add(vertex)

    while (breadth is not empty)
        DECLARE front <-- breadth.Dequeue()
        nodes.Add(front)

        for each child in front.Children
            if(child is not visited)
                visited.Add(child)
                breadth.Enqueue(child)

    return nodes;
```
but we should be aware that :
Breadth first only outputs the nodes that are connected in some relation to the root that you pass in.
Depth First, so other islands in the graphs won't be visited. 

2. Depth First

The algorithm for a depth first traversal is as follows:

1. Push the root node into the Stack and mark as visited.
2. Start a while loop that runs as long as the stack is not empty.
3. Pop the top node off of the stack and check its neighbors.
4. If a neighbor hasn’t been visited, push it onto the stack and mark as visited.
5. Repeat until the stack is empty.


### Real World Uses of Graphs:

1. GPS and Mapping
![GPS](https://qph.fs.quoracdn.net/main-qimg-ece3547a5e9c93d7e67abbc919afdf55-pjlq)
2. Driving Directions
![Driving Directions](https://miro.medium.com/max/1400/0*VqG4dM9VTPel3_w3.jpg)
3. Social Networks
![Social Networks](https://i.stack.imgur.com/xWMRJ.jpg)
4. Airline Traffic  
![Airline Traffic](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRu5KYa3O7f8A2a9xjr-dBsx7z8XLBKWelItg&usqp=CAU)

5. Netflix uses graphs for suggestions of products
