# Prim's Algorithm

A detailed breakdown of the code, what I do! 


### **HTML Structure**
1. **HTML Boilerplate**:  
   The code begins with the `<!DOCTYPE html>` declaration, followed by the basic structure:
   - `<head>`: Contains the title (`Prim's Algorithm Visualization`) and embedded CSS styles.
   - `<body>`: Hosts the canvas (created dynamically by p5.js) and a **reset button**.

2. **Reset Button**:
   - The button (`<button id="resetButton">Reset</button>`) is positioned at the **bottom-left** of the screen using absolute positioning in CSS.
   - Styling includes padding, rounded corners, and a hover effect for a modern UI feel.


### **CSS Styling**
- **Global Styling**: Removes default browser padding and margins (`* { padding: 0; margin: 0; }`).
- **Body Styling**: Centers content using flexbox and sets a dark background color.
- **Button Styling**:
  - A blue button with rounded corners (`border-radius: 5px`) and a shadow effect (`box-shadow`).
  - On hover, the background becomes darker for better user feedback.


### **JavaScript Functionality**
The code uses the **p5.js library** for graphics and animations. Below is a detailed breakdown:

#### **Setup Phase**
1. **Loading p5.js**:
   - The library is included via a CDN (`cdnjs.cloudflare.com`).

2. **`setup()` Function**:
   - This function is called once at the beginning.
   - Creates a canvas (`createCanvas(windowWidth, windowHeight)`) that fills the browser window.
   - Initializes **20 random vertices** by calling `initializeVertices(20)`.

3. **Reset Button Initialization**:
   - Adds a `click` event listener to the reset button.
   - On clicking, it resets the vertices to a random state by calling `initializeVertices(20)`.

#### **Core Functionality**
1. **`initializeVertices(num)`**:
   - Creates a specified number of random points (`num`) on the canvas.
   - Each point is represented as a `p5.Vector` object, which stores the `x` and `y` coordinates.
   - Resets the **total weight** of the Minimum Spanning Tree (MST) to 0.

2. **`windowResized()`**:
   - Automatically resizes the canvas whenever the browser window is resized.

3. **`mousePressed()`**:
   - Adds a new vertex at the current mouse position (`mouseX, mouseY`) whenever the user clicks on the canvas.


### **Drawing the MST (Prim's Algorithm)**
The **Prim's Algorithm** logic is implemented inside the `draw()` function, which runs in a continuous loop:

1. **Background Update**:
   - Clears the canvas with a dark background color (`background(20)`).

2. **Initialization**:
   - Divides the vertices into two groups:
     - **`reached`**: Contains vertices already included in the MST.
     - **`unreached`**: Vertices not yet connected to the MST.

3. **Starting Point**:
   - The algorithm starts with the first vertex in `unreached` and moves it to `reached`.

4. **Finding the Minimum Edge**:
   - Loops through all pairs of vertices between the `reached` and `unreached` groups.
   - Calculates the Euclidean distance between each pair using `dist()`.
   - Finds the **shortest edge** connecting the two groups:
     - The corresponding indices (`rIndex` for `reached` and `uIndex` for `unreached`) are stored.
     - Updates the **total weight** with the distance of this edge.

5. **Adding the Edge**:
   - Draws the shortest edge using `line()`.
   - Moves the vertex from `unreached` to `reached`.

6. **Vertex Rendering**:
   - Draws each vertex as a white circle (`ellipse()`).

7. **Total Weight Display**:
   - Shows the total weight of the MST at the top-left corner using `text()`.


### **Interactive Features**
1. **Dynamic Canvas**:
   - Automatically resizes to fit the window, ensuring a responsive visualization.

2. **Mouse Interaction**:
   - Users can add custom vertices by clicking on the canvas.

3. **Reset Button**:
   - A stylish button allows users to reset the graph to its original state with 20 random vertices.

4. **Dynamic Updates**:
   - The MST and its total weight are recalculated and displayed in real-time.


### **Visual Effects**
1. **Edges**:
   - Highlighted in green (`stroke(0, 255, 0, 150)`) as they are added to the MST.
   - The edges have a stroke weight of `3` for better visibility.

2. **Vertices**:
   - Represented as small white circles.

3. **Text**:
   - The total weight is displayed in white at the top-left of the screen.


### **What You Can Customize**
1. **Number of Initial Vertices**:
   - Adjust the `initializeVertices(20)` call to increase or decrease the number of random points.

2. **Styling**:
   - Modify the button’s position, color, or size to suit your design.

3. **Edge Highlighting**:
   - Change the color or weight of the edges for a different look.

4. **Additional Features**:
   - Add keyboard shortcuts for functionality like toggling the MST display, or allow users to delete vertices.

---

The **MST** in this context refers to the **Minimum Spanning Tree**. Here's what it means:


### **Minimum Spanning Tree (MST)**

1. **Definition**:  
   An MST is a **subset of edges** in a connected, weighted graph that:
   - Connects all the vertices.
   - Has the minimum possible total edge weight.
   - Does not form any cycles (i.e., it's a tree).

2. **Key Properties**:
   - If the graph has \( V \) vertices, the MST will have exactly \( V - 1 \) edges.
   - There can be multiple MSTs for a graph if there are edges with the same weights.

3. **Real-Life Applications**:
   - **Network Design**: Laying cables (electric, internet) with minimum cost.
   - **Transportation**: Designing efficient road networks.
   - **Clustering**: Grouping data in machine learning.


### **Prim's Algorithm**
The code visualizes **Prim's Algorithm**, one of the ways to compute the MST. Here's how it works:
1. **Start from a Random Vertex**:
   - Add this vertex to a "reached" set.
   
2. **Find the Smallest Edge**:
   - Look for the shortest edge connecting a vertex in the "reached" set to one in the "unreached" set.

3. **Add the Edge to the MST**:
   - Include the vertex on the other end of this edge in the "reached" set.

4. **Repeat**:
   - Continue adding the smallest edge until all vertices are included.

5. **Result**:
   - Once completed, the MST is formed, and the total weight (sum of all the edges in the MST) is calculated.


### **In the Code**:
- **Graph**: The random points (vertices) on the canvas form the graph. The edges are the distances between these points.
- **MST**: The program connects these points with the shortest possible edges, avoiding cycles, to form the MST.
- **Total Weight**: The code keeps a running total of the MST's weight, which is displayed on the canvas.

---

### **MST in details**

#### **Formal Definition**:
Given a connected, weighted, and undirected graph \( G(V, E) \), where:
- \( V \) is the set of vertices.
- \( E \) is the set of edges, each with a positive weight \( w(e) \).

The MST is a subset of edges \( T \subseteq E \) that:
1. **Connects all the vertices** (spanning tree).
2. **Has the minimum total weight**:

   ![Image](https://github.com/user-attachments/assets/23b1d9ed-ccfb-4c73-b2cd-6365a79305a5)

3. **Contains no cycles** (tree property).

#### **Why MST Is Unique**:
- If all edge weights are distinct, the MST is unique.
- If there are duplicate weights, there can be multiple MSTs with the same total weight.


### **Applications of MST**
1. **Network Design**: Build the least expensive network to connect computers, cities, or utilities.
2. **Approximation Algorithms**: Used in problems like the **Traveling Salesman Problem (TSP)**.
3. **Clustering**: Helps divide a set of data points into groups by connecting similar data.


### **Understanding Prim’s Algorithm**
Prim’s algorithm is a **greedy algorithm** to compute the MST. It starts with an arbitrary vertex and grows the MST by adding the shortest edge connecting the tree to a new vertex. Here’s a breakdown:


#### **Step-by-Step Algorithm**
1. **Initialization**:
   - Start with an arbitrary vertex \( s \) (in this code, the first vertex in the array).
   - Create two sets:
     - **Reached (R)**: Vertices already in the MST.
     - **Unreached (U)**: Vertices not yet in the MST.

2. **Iterative Process**:
   - Find the **shortest edge** that connects:
     - A vertex in \( R \) (reached).
     - A vertex in \( U \) (unreached).
   - Add this edge and the corresponding vertex from \( U \) to \( R \).

3. **Repeat**:
   - Continue until all vertices are included in \( R \) (i.e., \( U \) is empty).

4. **Output**:
   - The edges in \( R \) form the MST.
   - The sum of their weights gives the total weight of the MST.


#### **Time Complexity**
1. **Naïve Implementation** (like the one in the code):
   - For \( n \) vertices:
     - **Outer Loop**: Runs \( n - 1 \) times to add \( n - 1 \) edges.
     - **Inner Loops**: Check all pairs of vertices to find the shortest edge.
     - **Overall Complexity**: \( O(n²) \).

2. **Optimized Implementation**:
   - Using **priority queues** (like a min-heap), we can reduce the complexity to \( O(E log V \), where \( E \) is the number of edges.


### **Visualization in the Code**
Let’s map the algorithm to the code:

#### **1. Initializing Vertices**
- Vertices are represented as points on the canvas using `p5.Vector` objects, randomly positioned:
  ```javascript
  vertices.push(createVector(random(width), random(height)));
  ```
- `vertices` is the array of all points in the graph.

#### **2. Reached and Unreached Sets**
- Two sets:
  - `reached`: Initially contains one vertex.
  - `unreached`: Contains the rest.

#### **3. Finding the Shortest Edge**
- The algorithm loops through all pairs of vertices between `reached` and `unreached` to find the shortest edge:
  ```javascript
  for (let i = 0; i < reached.length; i++) {
    for (let j = 0; j < unreached.length; j++) {
      let d = dist(v1.x, v1.y, v2.x, v2.y);
      if (d < record) {
        record = d;
        rIndex = i;
        uIndex = j;
      }
    }
  }
  ```
- `dist()` calculates the Euclidean distance between two points.

#### **4. Adding the Edge to MST**
- Once the shortest edge is found:
  - It’s drawn on the canvas using:
    ```javascript
    line(reached[rIndex].x, reached[rIndex].y, unreached[uIndex].x, unreached[uIndex].y);
    ```
  - The corresponding vertex from `unreached` is added to `reached`.

#### **5. Visualizing Vertices**
- Each vertex is drawn as a circle on the canvas:
  ```javascript
  ellipse(vertices[i].x, vertices[i].y, 16, 16);
  ```

#### **6. Calculating Total Weight**
- The weights of the edges (distances) are summed up in the variable `totalWeight`.


### **Algorithm Limitations in the Code**
1. **Inefficient Implementation**:
   - The double loop to find the shortest edge makes it \( O(n^2) \), which isn’t scalable for large graphs.
   - Can be improved using a **priority queue**.

2. **Static Graph**:
   - The graph is undirected and unweighted except for distance, which is fixed.

3. **No Edge Removal**:
   - You can add vertices but not remove them.
