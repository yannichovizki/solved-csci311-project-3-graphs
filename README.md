Download Link: https://assignmentchef.com/product/solved-csci311-project-3-graphs
<br>
In this project you will implement an <u>undirected</u> graph that is represented as an Adjacency Lists (implemented as vector&lt;vector&lt; edge &gt; &gt; Adj). You will use <em>struct <strong>edge </strong></em>that contains two data members: an integer <em>neighbor </em>and an integer <em>w.</em>

<strong>Step 1. </strong>Implement a class Ugraph (stands for <em>undirected graph</em>). You need to write two files: <em>ugraph.h </em>and <em>ugraph.cpp.</em>

Inside <em>ugraph.h</em>, declare and define <em>struct <strong>edge</strong></em>:

<table width="0">

 <tbody>

  <tr>

   <td width="294">struct <em>edge</em>{int neighbor; // adjacent nodeint w; //keeps auxiliary informationedge(){                  neighbor = 0;w = 0;};edge(int i, int j){neighbor = i;w = j;};};</td>

  </tr>

 </tbody>

</table>

Class <em>Ugraph </em>will have the following data members and constructors (and other member functions):

<table width="0">

 <tbody>

  <tr>

   <td width="593">//private data members vector&lt;vector&lt;<em>edge</em>&gt; &gt; Adj; vector&lt;int&gt; parents; vector&lt;int&gt; distance; vector&lt;char&gt; colors; vector&lt;TimeStamp&gt; stamps;//public constructor and member functionsUgraph(int N); void addEdge(int u, int v); void removeEdge(int u, int v);</td>

  </tr>

 </tbody>

</table>







<strong>Constructor. </strong>The constructor of the class takes a single parameter, an integer N, and resizes <em>Adj, parents, stamps, distance </em>and <em>colors </em>to the size N. Initialize <em>parents </em>array: parent of a vertex v is equal to v. Initialize <em>distance</em> array with INT_MAX. Initialize <em>colors </em>with ‘W’ (stands for White).




<strong>void addEdge(int u, int v): </strong>This member function inserts a new edge between the existing vertices u and v in the graph. Since this is an undirected graph, this function must add <em>edge</em>(v, 0) to Adj[u] and add <em>edge</em>(u, 0) to Adj[v], where 0 is used to initialize <em>w </em>data member of an <em>edge</em>.




<strong>void removeEdge(int u, int v): </strong>This function will remove edge (u, v) from a graph. Since this is an undirected graph, two Adjacency lists must be modified: one of u and another of v. Here is how the removal must be implemented:

<ul>

 <li>In Adj[u], find an <em>edge</em> with <em>neighbor </em>equal to v, assume that it is found at index</li>

 <li>Copy the last <em>edge </em>in Adj[u] into <em>j-th </em>entry of Adj[u] (hence, <em>edge </em>with v becomes overwritten).</li>

 <li>Resize Adj[u] to (Adj[u].size() – 1) size.</li>

</ul>

Repeat the same steps for Adj[v] and <em>edge </em>with <em>neighbor </em>equal to u.




<strong>BFS and DFS.</strong> You will need to implement BFS and DFS member functions (just as you did in Assignment 10).




<strong>printGraph. </strong>Write a public member function <strong><em>printGraph </em></strong>that prints Adjacency lists in the order: all nodes in the Adj[0], then all nodes in the Adj[1], and so on. This function will not print out <em>w </em>of each <em>edge, </em>only <em>neighbor.</em> Print out <strong><em>endl </em></strong>after each Adjacency list, and a space after each node (neighbor).

<em> </em>

<strong>Step 2. </strong>Solve the following problems using Ugraph. You may add any member functions to class Ugraph to solve these problems. You may use <em>w </em>of struct <em>edge </em>to hold any information at each edge to help you to solve a problem. Your member functions may NOT change <em>Adj </em>(you may modify <em>w </em>at each edge, but you cannot remove or add edges of <em>Adj</em>), i.e. if you need to modify <em>Adj</em>, simply make a copy of <em>Adj </em>and pass this copy by reference to your member functions.




<strong>Important: </strong>All of these problems must be solved in O(V + E)-time unless stated otherwise. In other words if you need a few functions to accomplish a task (to solve a problem), then all of these functions must run in O(V + E)-time.




<strong>                 </strong>

<strong>Problem 1.</strong> Given an undirected graph G and two vertices <em>u </em>and <em>v </em>of G, design an algorithm that will return <em>true </em>if there are two distinct paths from <em>u </em>to <em>v </em>in G and will print these two paths; otherwise, it will return <em>false</em> and will not print anything.




Your functions must run in O(V + E)-time.




<em>Definition: </em>two paths in an undirected graph G are <strong><em>distinct </em></strong>if they do not share any edges.




For example, given an undirected graph G in Figure below, and two vertices u = 0 and v = 2, there are two distinct paths from 0 to 2: (1) 0, 1, 2 and (2) 0, 2. So your program will print them in this format:

&lt;node&gt;&lt;space&gt;&lt;node&gt;&lt;space&gt;…&lt;endl&gt;

Each path will be printed out on a separate line. The output for this example will be this:

0 1 2 0 2

However, if we give two other vertices u = 1 and v = 3, then two paths (1) 1, 2, 0, 3 and (2) 1, 0, 3 are not distinct because they share edge (0, 3). So, there are no two distinct paths in this graph for vertices 1 and 3. Your program will return false and will not print anything.










You will need to write the following public member function (with exact name, parameters, return type): bool <strong><em>distinctPaths</em></strong>(int u, int v).

You may write any other member functions to solve this problem, but these functions must be called from <em>distinctPaths</em>.







<strong>Problem 2.</strong> Given an undirected connected graph G, find and print all <strong><em>bridge </em></strong>edges of G.




Your functions must run in O(V + E)-time.




<em>Definition: </em>in undirected connected graph G, an edge is called <strong><em>bridge</em></strong> if removal of this edge will disconnect G.

For example, in the graph on Figure to the left, edge (1, 5) is a bridge edge because if we remove this edge from the graph, the graph becomes not connected. Edge (6, 9) is not a bridge edge, because if is removed from the graph, the graph will remain connected.




You will need to write the following public member function:

<h1>void printBridges()</h1>

You may write any member functions in addition to <em>printBridges</em> to solve this problem, but these functions must be called from <em>printBridges</em>.




Output format: as soon as an edge (u, v) has been identified as a bridge, print it in the format &lt;u&gt;&lt;space&gt;&lt;v&gt;&lt;endl&gt;







<strong>                 </strong>

<strong>Problem 3.</strong> Given an undirected graph G, find all connected components of G and print out the vertices in each component on a separate line. The order of printing is the following: all vertices in Connected Component with ID 0 on the first line, nodes in Connected Component with ID 1 on the second line, and so on.




Your functions must run in O(V + E)-time.




<em>Definition: </em>A <strong>connected component</strong> of an undirected graph G is a subgraph H of G such that H is connected (i.e. any two vertices in H are connected via a path in H).




For example, on given the graph on Figure to the left, your program will print out:

<ul>

 <li>8 9</li>

 <li>5 6 7</li>

 <li>3 4</li>

</ul>

<strong> </strong>




You need to write the following public member function:

<h1>void printCC()</h1>




You may write any member functions in addition to this function, but they must be called from <em>printCC</em>. Output format of a single line:

&lt;node&gt;&lt;space&gt;…&lt;node&gt;&lt;space&gt;&lt;endl&gt;







<strong>Problem 4.</strong> Given an undirected connected graph G, design an algorithm that returns <em>true</em> if it is possible to color all vertices of G in two colors, Red and Blue, such that if there is an edge (u, v) in G, then u and v must be colored with different colors.




To solve this problem, time complexity is <strong><u>not</u></strong> restricted to O(V + E)-time. Your functions may use O(VE)time.




Note that if an undirected connected graph has an odd-length cycle, then this coloring is impossible. So, your program needs to check if there is an odd-length cycle in the graph, and if so, then it will return <em>false</em>. Otherwise, it will return <em>true.</em>




For example graph G below does not have an odd-length cycle, so it is possible to color G using two colors so that the adjacent vertices are colored with different colors, but graph H has an odd cycle, so this coloring is impossible.







Your program must contain the following member function:

<h1>bool twoColoring()</h1>




You may write any other member functions to accomplish this task, but they must be called from <em>twoColoring. </em>

<em> </em>