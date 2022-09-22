# Computing

## Java

- Objects passed by reference
- no reference is null
- new returns reference
- == & != compares references and primitive types
- .equals() to compare by value
- . accesses member fields or methods
	- doesn't work on null references
- String is reference but built in
- has + and += overloaded
- many string methods
- arrays are like objects, array variable is a reference
- 0 indexed
- auto bounds checking
```java
double[] primArray = new double[5];
Student[] refArray = new Student[10];
```
- this example does not create any Students, only null references
```java
int arr[][] = new int[2][3];
arr = {
	{1,2,3},
	{4,5,6}
};
```
- example:
```java
int arr[][] = {
	{1,2,3,4},
	{5,6,7,8},
	{9,10,11,12}
};

// TODO: Print 2nd row
for(int i = 0; i < 4; i++)
	System.out.print(arr[1][i] + " ");

// TODO: Print 1st column
for(int i = 0; i < 3; i++)
	System.out.println(arr[i][0]);

// TODO: Print all
for(int i = 0; i < 4; i++)
{
	for(int j = 0; j < 3; j++)
		{
			System.out.print(arr[j][i] + " ");
		}
	System.out.println("");
}
```

- Unary have highest precedence
- ++x increments first, x++ increments after (evaluation)
- logical precedence:
	- > < >= <=
	- == !=
	- &&
	- ||

### Passing Arguments

- Pass by value
	- method gets a copy of a value (usually on primitives)
- Pass by reference
	- method gets a reference to a value (usually on objects)

- Java only uses pass by value (technically)

### OOP

- 'extends' to inherit
- derived classes extend from base classes
- @Override to override functionality (not needed but best practice)
- You don't need a keyword like 'virtual' from c#
- keyword 'super' to refer to this object through the lens of the base class
- run base class constructor with super(...)
- super constructor must be run first
- object's types change based on what is needed at runtime (Polymorphism)
- Interfaces are purely abstract, only have common methods/functionality
- Interfaces can only contain fields of type public static final
- 'implements' keyword for interfaces
- you can implement multiple interfaces, as opposed to classes
- one common example of an interface in java is the Comparable interface

```java
public interface Comparable<T>{
	public int compareTo(T item);// -1 means this is before, 0 is the same, 1 means this is after
}
```
```

- Note on generics:
	- ArrayList<Triangle> IS NOT ArrayList<Shape> even though Triangle IS a Shape
	- To get around this use wildcards
		- Question-mark == ?
		- <Question-mark extends Shape> refers to Shape or anything that extends it
		- <Question-mark extends T> can also work on interfaces (don't have to use 'implements')
		- <Question-mark super T> incoudes everything above, including Object
	- Primitives don't work in generics
		- 'wrapper' classes
			- Integer, Float, Double
		- autoboxing and unboxing to remedy this
	- Static methods can use generics
	- example: public static <T> boolean doWork(...)
	- sometimes you need to pass a function into another function, such as to explain how to use the less than symbol in a generic method, this is called a function object, or a functor
	- Comparator has compare

```

## Data Structures

- Different than an abstract data type (ADT)
	- non-specific model for storing and accessing data
	- broadly defines operations on the data
- A data structure is a concrete implementation of an ADT
- stores data and can manipulate it
- implementation exists as *source code*
- Examples:
	- List is an ADT
	- list data structures include arraylist, linkedlist, etc.
- A Collection is an ADT that holds items (unspecific)
	- Collection is an interface in java
	- ArrayCollection
		- items stored in the order they are inserted
		- no duplicates
		- adding
			- keep track of size
			- if size is less than the allocated space, put new data at index size
			- otherwise make new temp array that is bigger
			- copy data to temp
			- set data reference to temp
			- growing is O(N)
			- How much to grow?
				- usually double the length
				- growth will be rare
		- shrinking
			- should we even shrink?
				- usually no, unless space is a concern
			- how to remove?
				- remove(item)
				- move subsequent items back by one
				- adjust size variable accordingly
				- finding the item is O(N)
				- filling the gap is O(N)
				- the whole operation is O(N)
	- many collections cannot be indexed with the [] operator
		- trees for example
	- collection's implementation should be private
	- iterators solve this problem
		- an iterator's job is to get items out of a collection one at a time
		- Collection has a method called iterator()
		- iterator gives limited access to private internals
		- iterator has public standard methods
		- methods:
			- hasNext
				- determines if iteration is complete
			- next
				- gets the next item
			- remove
				- removes the last seen item(returned by next)

```java
Iterator<String> itr = stringCol.iterator()

while(itr.hasNext())
	System.out.println(itr.next());
```

- Iterators Cont'd.
	- remove removes the last seen item, so if nothing is seen then it throws an exception
	- you also cannot call remove multiple times before running next again
	- Nested Private Class
		- put a class inside another class, this class will have access to the private internals of the outer class
		- to the outside, the iterator nested private class is just seen as an iterator

### Arrays

Arrays are *random access* which means getting an element takes constant time.

### Linked Structures

Nodes point to other Nodes. Nodes hold data. Adding and removing is constant due to this.

#### Linked List

Every node has a value and a link to the next node.

Last element points to null/nothing.

Linked List holds a pointer to the first node.

## Algorithms

### Complexity

- quadratic (N^2)
- linear (N)
- logarithmic (logN)
- constant (1)
- ...

The primary factor of a program's performance is the algorithmic complexity. Secondary factors are things like code quality, computer speed, optimization, your OS, etc.

The class of complexity an algorithm is in is solely determined by the most dominant term of N

Before optimizing code, pick the right algorithm

#### Big O Notation

- O(complexity)
- pronounced 'order complexity'



### Complexity Cont'd

Some algorithms have different cases

- worst case
- average case
- best case

best case is the least useful

average case is the most useful

### Sorting Algorithms

Sorting itself usually isn't the goal, it is to allow other algorithms to run or run faster.

Naive sorting algorithms are O(N^2)

NlogN is the fastest for comparison-based sorting

#### Inversion

If you check an item in an array, how many elements in the rest of the array are in the wrong place relative to it. Count how many unique inversions for the whole array, that is the array's *unsortedness* (I)

The more inversions removed per step is how efficient a sorting algorithm is

average num inversions = num_pairs/2 = (N^2-N)/2/2=(N^2-N)/4

#### Insertion

Put element at the end of an array and swap with previous element until in the correct position

O(N)

#### Insertion Sort

Algorithm of choice for small arrays
Use [[#Insertion]] repeatedly on list, pushing a pointer for what part of the array is sorted to the right until finished

W - O(N^2)
A - O(N^2)
B - O(N)

#### Selection Sort

Find the smallest value and swap its place with the first, the continue with the remaining array until you reach the end.

O(N^2)

#### Merge Sort

Cut array in half, **sort** either half (Recursive!), merge the two sorted halves
Make temporary array for merge sort in driver method (size N). Initialize method with right space, for loop putting null in all slots.

O(NlogN)

Often times when we get down to small arrays in merge sort we run insertion sort on that small array and continue with merge sort. This doesn't change the complexity as long as the threshold for insertion sorting is not related to N.

##### Merge

To merge to sorted arrays, grab a pointer at the start of both arrays, take the lesser and move that pointer forward. Continue comparing and taking until one pointer reaches the end of an array and add the rest of the other array.

#### Quicksort

any pivot works, however median is best.
finding median is costly so we take a sample of the first, middle and last and find the median of those, or a random index, etc. The performance and quality is a tradeoff, so make the best judgement.

O(NlogN) if best partitioning, O(N^2) if worst partitioning

W - O(N^2)
A - O()
B - O(NlogN)

##### Out of place

Pick a pivot (usually the median), put all smaller values in a left partition and larger values in a right partition, run quicksort on the partitions until finished.

##### In Place

Pick pivot and swap it to the end. Keep two indices, left and right (right is just to the left of the pivot at the end), move L (left) to the right until something bigger than the pivot is found, and move R to the left until something smaller is found. Once both are found, swap them. Continue until L is past R. Then swap the pivot at the end with what is at L. Quicksort everything to the left of the new pivot location and the same on the right.

### Search Algorithms

#### Binary Search

O(logN)

start in the middle if it is less/greater, cut away the unimportant section (half) and repeat until one left, check and return if found

### Recursion

Calling a function within itself.

Finding a smaller version of the problem over and over again until the problem can get no smaller/you find a special case.

Recursive calls must move towards a solution
Their must be a case that does not run a recursive call

Often times recursive methods need extra parameters that the user shouldn't have to fill in, so we make a *Driver Method* which passes in the correct starting parameters and streamlines use for users. The Driver Method should not be recursive. Driver Methods can also allow for error checking that isn't recursive.





