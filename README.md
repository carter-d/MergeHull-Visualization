# MergeHull-Visualization
A visualization of the Mergesort algorithm for computing convex hulls.
The live visualization can be found here:


https://carter-d.github.io

![Visualization running on basic set of 6 points](https://github.com/carter-d/MergeHull-Visualization/raw/master/img/basic_example.gif)
The visualization running on basic set of 6 points.

![Visualization running on a set of 100 random points](https://github.com/carter-d/MergeHull-Visualization/raw/master/img/many_points_3.gif)
The visualization running on a larger set of random points.


## Background
One of the most well known techniques for computing the convex hull of a set of points is the Divide-and-Conquer technique (sometimes referred to as MergeHull because of its similarity to the MergeSort algorithm). It is an *O(nlogn)* algorithm that sorts points by x-coordinate, recursively divides the point set in half, then recursively computes the convex hull for each half.

This visualization specifically highlights the tangent "walking" process between two vertically separated convex hulls. This "walking" process is what enables the merging of convex hulls within the *O(nlogn)* bound of the algorithm. In the visualization, the lower tangent during the "walking" process is represented by a yellow line. The upper tangent during the "walking" process is represented by an orange line. After the final tangent (either upper or lower) between two convex hulls is found, its color changes to green. After the final convex hull is found, it is highlighted in green and the initial base case hulls (the white lines / triangles) are removed.

This implementation is dependent on points being in general position. In order to overcome this limitation, an extremely small random value is added to each point before computing the convex hull. This makes the possibility of colinear points unlikely (but technically possible). In addition, the visualization has some difficulty rendering extremely large sets of points.

This project was completed as an extra credit assignment for CSE546 (Computational Geometry) at Washington University in St. Louis.

## Use
Points can be placed by clicking anywhere within the canvas (the black rectangle). Once points have been placed in their desired locations, the visualization/animation is started by clicking the "merge hull" button. Points can be placed randomly around the canvas (with a buffer around edges) by clicking the "place points randomly" button. To remove points (or a completed hull) from the canvas, click the "clear points" button. 

The settings window be accessed by clicking the button with a wrench icon. Within the settings window, the following parameters for the visualization can be changed:
* Animation speed (how fast the tangent "walking" is)
* Point radius
* Line weight
* Number of random points (how many points are added when the random points button is clicked)


## References
This code relies heavily on the pseudo-code provided in [David Mount's lecture notes](http://www.cs.umd.edu/~mount/754/Lects/754lects.pdf). I also used the description / pseudo-code in Joseph O' Rourke's book *Computational Geometry in C*. Specific information/functionality for the tangent "walking" process (the functions upperTangent and lowerTangent) is largely from this [online resource](http://geomalgorithms.com/a15-_tangents.html#Tangents-Polygon-to-Polygon).

This visualization was built using [p5.js](https://p5js.org/), a JavaScript port of processing. This library allows for allows for basic drawing (e.g. of shapes, lines, etc.) and animation.

## Known bugs
Occasionally the program fails to highlight the completed hull in green at the termination of the algorithm. If this occurs, refresh the page and re-run.

In some cases the upper tangent between two sub-hulls is not deleted properly which results in a floating tangent line within a hull until the animation terminates.

