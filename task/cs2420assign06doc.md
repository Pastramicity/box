# Assignment 6

I (Chase Yates) and Liam Astin worked on this assignment. Liam submitted it to Gradescope

## Question 1

We spent probably 4-5 hours working on the assignment. I'll probably switch partners next time. Liam was fine, just want a change of pace.

## Question 2

First up is the push method. This one had pretty standard results. See for yourself:

![[a6c1.png]]

As you can see both times were linear, with one large spike in the linked list stack at one point. This may have been due to my computer or issues allocating RAM, or something else. all that matters is that this point is an outlier.

Second up is the pop method. For this one, I got some strange (negative) times. Not sure why this happened, I triple checked my timing code. Maybe the small times and error contributed, or my computer just didn't want to spend so many resources on running an empty loop doing nothing, but here were the results in graph form:

![[a6c2.png]]

As you can see, the overall trend was linear, with the linked list taking the top spot for least time by breaking the space-time-continuum by reaching the fabled O(-1) time. I'm just joking, but the trend shows them both as constant.

Last up is peek, let's take a peek at the results:

![[a6c3.png]]

Here you can see both graphs as completely flat-lined and constant after a rough start. Both stack types seem to have roughly the same constant time and neither takes the cake.

## Question 3

I think overall, the `LinkedListStack` is the winner here. With perhaps slightly slower, but more consistent (for the most part) constant times, and even breaking my timing code to achieve negative results, it comes out on top above the `ArrayStack`, who unfortunately, has a rough time growing up in cases where the backing array is too small to push on any further.
