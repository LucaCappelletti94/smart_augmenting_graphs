# Adigraph
[Adigraph](https://ctan.org/pkg/adigraph) is a pure latex library for drawing directed graphs and augmenting directed graphs, and to draw cuts over them. It DOES NOT require external libraries such as Graphviz or DOT. 

It handles automatically the positioning of labels, with the exception of the horizontal position, and the inclinations of cuts.

**This library is released under MIT license (Copyright 2018 Luca Cappelletti)**.

##Documentation
For more information, you can read the documentation available [here](https://github.com/LucaCappelletti94/adigraph/blob/master/documentation.pdf)

##Basic setup
### Installing the package
If you are on Linux or macOs you can run the following.
```bash
sudo tlmgr install fp etoolbox adigraph
```

Otherwise install the packages with the package manager of your choice.

### Requiring the package in the document
Remember to require the package in the document.

```latex
\usepackage{adigraph}
```

##Basic example
More examples and step by step explanation is available in the [documentation](https://github.com/LucaCappelletti94/adigraph/blob/master/documentation.pdf).

Suppose you want to create a graph as the following, with an augmenting path highlighted and a couple of cuts:

<p align="center">
  ![alt text][graph2]
</p>


We start by defining a new graph, called *myAdigraph*:

```latex
\NewAdigraph{myAdigraph}{
    s:0,0;
    1:2,2;
    3:2,-2;
    2:6,2;
    4:6,-2;
    t:8,0;
}{
    s,1:25;
    s,3:25;
    3,4:25;
    1,2:35;
    2,t:20;
    4,t:30;
    3,1:10;
    4,2:10;
    2,3:15::near start;
    4,1:5::near start;
}
```

At this point the output is the following:

```latex
\myAdigraph{}
```

<p align="center">
  ![alt text][graph0]
</p>

Then we can add the augmenting path as follows:

```latex
\myAdigraph{
    s,3,4,2,t:5;
}
```

<p align="center">
  ![alt text][graph1]
</p>


And the cuts (remember that the paths from previous steps are memorized by the library) are added as follows:

```latex
\myAdigraph{}{
    2,t,red;
    3,4,blue;
}
```

The result with the cuts is the following:

<p align="center">
  ![alt text][graph2]
</p>


You can add both cuts and paths at the same time to keep the latest path highlighted:

```latex
\myAdigraph{
    s,3,4,2,t:5;
}{
    2,t,red;
    3,4,blue;
}
```

<p align="center">
  ![alt text][graph3]
</p>


Have a nice day!

**Luca Cappelletti**

[graph0]: https://github.com/LucaCappelletti94/adigraph/blob/master/img_examples/example_0.jpg?raw=true "Graph example, basic"
[graph1]: https://github.com/LucaCappelletti94/adigraph/blob/master/img_examples/example_1.jpg?raw=true "Graph example, with augmenting path"
[graph2]: https://github.com/LucaCappelletti94/adigraph/blob/master/img_examples/example_2.jpg?raw=true "Graph example, with cuts"
[graph3]: https://github.com/LucaCappelletti94/adigraph/blob/master/img_examples/example_3.jpg?raw=true "Graph example, with path highlighted"
