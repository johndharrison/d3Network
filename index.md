<title>D3network by christophergandrud</title>

<link rel="stylesheet" href="assets/css/styles.css">

<a href="https://github.com/christophergandrud/d3Network"><img style="position: absolute; top: 0; right: 0; border: 0;" src="https://s3.amazonaws.com/github/ribbons/forkme_right_gray_6d6d6d.png" alt="Fork me on GitHub"></a>

[Christopher Gandrud](http://christophergandrud.blogspot.com/p/biocontact.html)

<section>

# d3Network

### Tools for creating D3 JavaScript directed network graphs from R.

### v0.2


---

<blockquote>Site Under Construction</blockquote>

[Mike Bostock](http://bost.ocks.org/mike/)'s [D3.js](http://d3js.org/) is great for creating [interactive network graphs](http://bl.ocks.org/mbostock/4062045) with JavaScript.  The [d3Network](https://github.com/christophergandrud/d3Network) package makes it easy to create these network graphs from [R](http://www.r-project.org/). The main idea is that you should able to take an R data frame of information about the relationships between members of a network and create full network graphs with one command.

Currently **d3Network** only supports [force directed](http://en.wikipedia.org/wiki/Force-directed_graph_drawing) network graphs. Basically, D3 assigns forces to the nodes and edges (links between the nodes) to arrange their placement and simulate movement. We'll see of examples below that make this concept intuitive sense. 


## Commands

**d3Network** currently has two basic commands for creating network graphs: <a href="#simple"><code>d3SimpleNetwork</code></a> and <a href="#forceDirect"><code>d3ForceDirected</code></a>. 

<h3 id="simple"><code>d3SimpleNetwork</code></h3>

`d3SimpleNetwork` is designed to take a simple data frame that has two columns specifying the *sources* and *targets* of the nodes in a network and turn it into a graph. You can easily customise the look and feel of the graph. Let's do create an example. 

First let's make up some fake data. 


```r
Source <- c("A", "A", "A", "A", "B", "B", "C", "C", "D")
Target <- c("B", "C", "D", "J", "E", "F", "G", "H", "I")
NetworkData <- data.frame(Source, Target)
```


It's important to note that the *Source* variable is the first variable and the *Target* is the second. We can use the `Source` and `Target` arguments to specify which variables are which, if the data is in another order.  

Now we can simply stick the `NetworkData` data frame into `d3SimpleNetwork`:


```r
d3SimpleNetwork(NetworkData, width = 400, height = 250)
```


You'll notice that I added the `width` and `height` arguments. These change the size of the graph area. They are in pixels.

And here is the result:

<iframe src='img/FirstNetwork.html' height=267.5 width=412></iframe>


There are many options for to customising the look and feel of the graph. For example we can change the colour of the links, nodes, and text. We can also change the opacity of the graph elements:


```r
d3SimpleNetwork(NetworkData, width = 400, height = 250, textColour = "orange",
                linkColour = "red", nodeColor = "orange", opacity = 0.9)
```


<iframe src='img/SecondNetwork.html' height=267.5 width=412></iframe>



<h3 id="forceDirect"><code>d3ForceDirected</code><h3>


## d3Network in dynamic reproducible documents

## Installation

You can install **d3Network** using the [devtools](https://github.com/hadley/devtools) package and the following code:


```r
devtools::install_github("d3Network", "christophergandrud")
```


</section>

<script src="assets/js/d3.min.js" type="text/javascript></script>
