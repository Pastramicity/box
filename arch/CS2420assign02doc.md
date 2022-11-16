# Library Analysis

My partner is Liam Astin and I (Chase Yates) submitted the code to Gradescope. I much liked the driver role better as I got to think of ideas and implement them, rather than just thinking of ideas and solving problems, although writing unit tests did degrade from that experience somewhat (I'm not the biggest fan). We implemented pair programming pretty effectively, as having two people very much contributes to higher code quality and stability as someone can call you out on the spot if you make a mistake and vice versa. We developed the program in (mostly) one efficient night of work together, setting up file sharing and other useful tools that we can use going forward as well to assist us on future assignments. I would say we spent between 3-4 hours working on and testing on this assignment, in spite of some technical issues. with Eclipse and Github. I probably would work with my partner again after allowed to switch if I didn't have a few friends in the class I would prefer to work with. They are a bit timid when it came to correcting my mistakes but he still did and was engaged in figuring out the assignment with me.

Java's Comparable interface is most useful when you have access to/defined a class yourself and their is a 'natural order' of that thing. Strings, for example, have a natural alphabetic ordering, dates by how early they are, etc. Comparator, on the other hand, are most useful when their are several different valid orderings, a special case ordering, or you simply do not have access to the class in order to implement Comparable. Comparable is something you extend yourself, whereas Comparator is for extraneous classes with limited functionality. It wouldn't make sense to implement Comparable in place of the Comparator that is used in the LibraryGeneric class, as there are several different valid orderings in the library, including by ISBN, title, and due date. You *could* implement comparable, in which case it would have to choose between one of these ordering types to default to, or you could have some mutable internal state in the class that lets the user of the class choose what ordering to use.

## Library Lookup Runtime Test

In this experiment we will test the runtime performance of the `lookup` method in our Library class. In this experiment we will run some redundant computations to ensure the cpu is ready to run our computation. Then we will start a timer and run our computation several thousands of times to ensure consistency, taking the time it takes each iteration, and increasing the size of the random library that is tested using some helper methods. We will take this average time for each library size (subtracting any overhead time caused by looping or other needed code during the test) and plot it. My hypothesis is that the complexity of this algorithm will be linear, or O(N), as the lookup method must run through the whole list of library books to find the correct one. This graph shows the number of nanoseconds it roughly took on average to run the lookup algorithm on several different sized libraries. The time in nanoseconds is the y-axis and the size of the library in books is on the x-axis.

```plotly
data:
    - x: [1000, 2000,3000,4000,5000,6000,7000,8000,9000,10000]
      y: [2268.3213, 1641.8242, 1972.4255, 3299.3786, 4682.7939, 7225.4215, 5488.87, 10502.1475, 12270.7734, 10404.5949]
```

As we can see (although the chart is very inconsistent in some places), the graph seems to be fairly linear, lending credence to my hypothesis.