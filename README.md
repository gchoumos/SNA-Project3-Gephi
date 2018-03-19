# README #

This repository holds the implementation of the third assignment for the **Social Network Analysis** half-course, which was part of the M.Sc. in Data Science of the Athens University of Economics and Business.

_**IMPORTANT NOTE**_: The original assignment description itself as well as the accompanying files that were given are **NOT** available in this repo. It acts more like a GitHub save of the assignment implementation and it is not supposed to make full sense on its own. I plan to update the repo in the future with the full assignment description as well as the prerequisites.

### Assignment Overview ###
[**_Gephi_**](https://gephi.org/) is an open-source visualisation and exploration software for all kinds of graphs and networks. In this assignment, we import a network into Gephi, measure various statistics, apply transformations on the each with respect to certain characteristics and finally export the network into a web app (Firefox).

The pdf report on the repo is actually a walk through what has been implemented. You can download and see it in it's original form. However a markdown version of it follows at the end of this README file.


### How do I get set up? ###
The prerequisites are the following:

* Have Gephi installed
* Install the _SigmaExplorer_ plugin
* The _facebook.gdf_ file which is **_NOT_** currently available on the repo (I have to get the relevant permission first)
* A compatible browser - I'd recommend Firefox only because I was facing incompatibility issues with Chrome.

# Markdown Version of Assignment Report #

---------------

### Social Network Analysis - Homework 3
### George Choumos

This is the report for the 3 rd assignment in Social Network analysis. It will be more like a walkthrough of the actions that were taken in order to carry out all the tasks and come up with the final deliverables.

I'll write them down as a numbered lists.

### Preparation
1. Installed Gephi on Ubuntu 16.04
2. Installed the _SigmaExplorer_ plugin and restarted the application.
3. Downloaded and imported the **facebook.gdf** file.

### Measuring degrees of all nodes and resize nodes according to their in-degree

1. On the "Appearance" tab, we click on the Nodes option (already selected by default)
2. Then we click the Size icon on its right.
3. We check the Ranking option below
4. Select "Degree" from the dropdown list
5. Chose to set it to 1 as the minimum and 20 as the maximum size.
6. Lastly, click on Apply.

### Find network's diameter
1. On the right side, on the statistics tab, in the Network Overview section
2. Click on the "Run" button next to the Network Diameter line.
3. The value of the **Network Diameter** is **3**

### Find the individual with the largest betweenness centrality
1. Click on the "Data Laboratory" tab
2. Then click on the "Betweenness Centrality" column so that the data are ordered by betweenness centrality in descending order.
3. The individual that we are looking for is the first one on the list.
4. Individual ID: **1150672795** - Label: **Hua Liu**

### Find the communities existing in the Network

1. On the right side, on the Statistics tab, in the Network Overview, we click the Run button next to the modularity entry.
2. A pop up appears where we leave the default values. (Randomise and Resolution to 1.0)
3. It turns out that **there exist 3 communities**.


### Color the Nodes according to the communities you discovered
1. On the left menu, in the Appearance tab, we make sure that Nodes are selected and the colour button next to it.
2. Also, right below, the Partition button should be clicked.
3. From the dropdown list, we select the "Modularity Class"
4. Hit the Apply button
5. We can now see that each of the 3 communities has been assigned with its own colour.

### Select an individual in the network as your best friend
1. I right clicked on the node with the smallest degree and selected it in the Data Laboratory
2. Its id is: **100002888652465**
3. Its name is: **Cheng FU**
4. Its degree (undirected graph): **4**
5. Its PageRank value: **0.004144**
  - We had to hit the Run button next to the PageRank line in the right menu of the Overview tab.
  - The default values were left, so probability: 0.85 and epsilon: 0.001
  - PageRank now became available in the Data Laboratory tab, so were now able to
see it there

**_Note_**: _In order to achieve the different colours for different depths of the ego network, we will follow the hint of the assignment and we will start from the end. So:_

### Apply different colours to the Edges of the remaining Nodes
1. UPDATE: I'll also color the best friend itself, just in order to be even clearer which it is.
2. While on the Data Laboratory
3. Right click on our best friend node and click the Edit Node option
4. From the options that appear on the left, we clicked on the icon next to the Colour option.
5. Chose a dark blue color for the node (3,15,72 in RGB). It is quite tiny though as it is the one with the smallest degree.
6. So as a first step we will apply a color to all the edges of the graph. This is the color that at the end of the execution will only be held by the "edges of the remaining nodes". That's because we are following the HINT given by the assignment.
7. We select the filters tab
8. Expand topology
9. Drag the "Ego Network" filter and drop it below.
10. Input the Node ID of our best friend (**100002888652465**)
11. Select Max as the Depth
12. Leave the "With self" checkbox as is, i.e. checked.
13. Click ok, then Filter button below
14. Now click on the Edges on the left side and click color.
15. I selected a dark red (117,38,40 in RGB)
16. Hit Apply
17. Now the colour has been applied to all the edges!

### Apply different colours to the edges of the nodes in the best friend's ego network with depth 2
1. Update the Depth in the Filter to **2**
2. Leave the "With self" checkbox as is, I.e. checked.
3. Click ok, then the Filter button below.
4. Nodes now visible: **61** (**98.39%**)
5. Edges now visible: **953** (**98.55%**)
6. Now click on the edges on the left side and click colour
7. I selected a yellow one (109,130,62 in RGB)
8. Hit Apply
9. The yellow colour has now been applied to all the edges apart from the few ones that were not caught by the new Depth Filter.

### Apply different colours to the edges of the nodes in the best friend's ego network with depth 1
1. Update the Depth Filter to **1**
2. Leave the "With self" checkbox as is, I.e checked.
3. Click ok, then the Filter button below.
4. Nodes now visible: **5** (**8.06%**)
5. Edges now visible: **10** (**1.03%**)
6. Now click on the edges on the left side and click colour
7. I selected a blue one (35,58,102 in RGB)
8. Hit Apply
9. The blue colour has now been applied to the corresponding edges.

### Apply a new layout that enhances the visualisation of your network
I chose the **Fruchterman Reingold** layout!

### Result
1. Nodes are not overlapping
2. Size of nodes clearly indicates the difference in the degrees
3. Now colours are indeed highly contrasted. However, because of the specific characteristics of this particular network, there are only a few edges that are not yellow. However, zooming in appropriately can make those different colours appear!

As a last step, the network was exported using the _SigmaExporter_ plugin. You can find the corresponding folder in the deliverables of this project!

_Note_: I was having issues as well when trying to open the index file with any browser other than
Firefox. Therefore, Firefox is the only recommended one for this purpose!
