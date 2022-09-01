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

- Note on generics:
	- ArrayList<Triangle> IS NOT ArrayList<Shape> even though Triangle IS a Shape
	- To get around this use wildcards
		- <? extends Shape> refers to Shape or anything that extends it
		- <? extends T> can also work on interfaces (don't have to use 'implements')

- 



## Algorithms



## Data Structures

