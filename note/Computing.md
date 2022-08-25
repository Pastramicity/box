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
- 