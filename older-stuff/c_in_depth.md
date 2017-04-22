#C In Depth

##Pointers and Addresses

A pointer is a variable that contains the address of a variable. Pointers and arrays are closely related. 

A typical machine has an array of consecutively numbered or addressed memory cells that may be manipulated individually or in contiguous groups. One common situation is that any byte can be a char, a pair of one-byte cells can be treated as a short integer, and four adjacent bytes form a long.

A pointer is a group of cells (often two or four) that can hold an address.

A pointer is constrained to point to a particular kind of object: every pointer points to a specific data type. (There is one exception: a 'pointer to void' is used to hold any type of pointer but cannot be dereferenced itself.)

##The `&` Operator

The unary operator & gives the address of an object, so the statement













I.e. If `x` points to the integer `a`, then `*x` can occur in any context where `a` could. E.g.

	(*x)++;
	++*x;	





##Pointers and Functions Arguments

Since C passes arguments to functions by value, there is no direct way for the called function to alter a variable in the calling function.

Pointer arguments enable a function to access and change objects in the function that called it (e.g. main).


##Pointers and Arrays

In C, there is a strong relationship between pointers and arrays. Any operation that can be achieved by array subscripting can also be done with pointers. The pointer version will in general be faster but, at least to the uninitiated, somewhat harder to understand. 

	int a[10], *x;
	x = &a[0];

This means that `x` points to `a[0]`, so using `*x` will change `a[0]`.

Furthermore, `*(x+1)` refers to the contents of `a[1]`, so `x+i` is the address of `a[i]`, and `*(x+i)` is the contents of `a[i]`.

The correspondence between indexing and pointer arithmetic is very close. By definition, the value of a variable or expression of type array is the address of element zero of the array. So:

	x = &a[0];

can also be written as
	
	x = a;

Even more surprising is that `a[i]` can also be written as `*(a+i)`. In evaluating a[i], C converts it to *(a+i) immediately. So `&a[i]` and `a+i` are identical.

Conversely, if `x` is a pointer to `a[i]` as above, `x[i]` is identical to `*(x+i)`.

In short, an array-and-index expression is equivalent to one written as a pointer and offset.

There is one difference between an array name and a pointer that must be kept in mind. A pointer is a variable, so pa=a and pa++ are legal. But an array name is not a variable; constructions like a=pa and a++ are illegal.

When an array name is passed to a function, what is passed is the location of the initial element. Within the called function, this argument is a local variable, and so an array name parameter is a pointer, that is, a variable containing an address. 

As formal parameters in a function definition, `char s[]` and `char *s` are equivalent. 

It is possible to pass part of an array to a function, by passing a pointer to the beginning of the subarray. For example, if a is an array, `f(&a[2])` and `f(a+2)` both pass to the function f the address of the subarray that starts at `a[2]`. 

Within `f`, the parameter declaration can read

	f(int arr[]) { ... }













`d[]` is an array that contains the string

`*s` is a pointer that points to a string

To mess around with the strings via pointers, use:
	
	while (*s != '\0') {
		printf("%c", *s);
		s++;
	}
	
Using `*s` in the `printf` statement means that you're targeting the contents of the specific character or array index that `s` is currently pointing to.

Conversely, `s` is the pointer to the beginning of the string, so if you just wanted to print out the string without a loop, you'd need to use `s` without the `*`, like so:

	printf("%s", s);

You could also try to write the above loop as:
	
	while (*s++ != '\0')
		printf("%c", s)			#will start 1 letter after 1st

Since we're using `*s++`, and not `++(*s)`, the value of `*s` is retrieved first, and THEN it is incremented. BUT... because the `*s++` is executed in the test before we perform the first `printf` statement, it means that `*s` already points to the second position in the string by the time you read the `printf` statement.

You could also omit the `= '\0'` since it is essentially redundant, because loops test for zero as a failure, so you could just rewrite the loop as:

	while (*s) {
		printf("%c", *s);
		s++;
	}

Other ways to write loops using pointers and arrays:

	 for ( ; *s == *t; s++, t++)
	 for (i = 0; s[i] == t[i]; i++)


##Pointer Arrays; Pointers to Pointers



		"ben",
		"bob",
		"shamir",
		"ralph"
	};

Since the size of the array name is not specified, the compiler counts the initializers and fills in the correct number.




	int days[2][5];			#declaration
	days[1][5] = 22;		#initialization


##The difference between pointer arrays and multi-dimensional arrays

The important advantage of the pointer array over a regular multi-dimensional array is that the rows of the array may be of different lengths. That is, each element of `a` need not point to a twenty-element vector; some may point to two elements, some to fifty, and some to none at all.

	//Declare variables
	char *a[] = {
		"hello there",
		"how are you today",
		"what is your name"
	};

	printf("\nanswer: %c\n", a[1][2]);

The difference is that you can't set a mult-dimensional array like we do above, so that it expands to fit each string in a new array position, and each letter of each string in a sub-array position automatically. I.e. you can't do:

	a[][] = {
		"hello",
		"how are you",
		"nice tie"
	};

##Command-line Arguments





When you have `void *` as a parameter, it will take any datatype.

`*` is a prefix operator and it has lower precedence than `()`, so parentheses are necessary to force the proper association.	

##Structures (precursor to objects?)

A structure is a collection of one or more variables, possibly of different types, grouped together under a single name for convenient handling. Structures help to organize complicated data, particularly in large programs, because they permit a group of related variables to be treated as a unit instead of as separate entities.

One traditional example of a structure is the payroll record: an employee is described by a set of attributes such as name, address, social security number, salary, etc. Some of these in turn could be structures: a name has several components, as does an address and even a salary.

Structures may be copied and assigned to, passed to functions, and returned by functions.

To declare a structure

	struct point {
	};

The keyword struct introduces a structure declaration, which is a list of declarations enclosed in braces. An optional name called a **structure tag** may follow the word struct (as with `point` here).

The variables named in a structure are called members. A structure member or tag and an ordinary (i.e., non-member) variable can have the same name without conflict, since they can always be distinguished by context. Furthermore, the same member names may occur in different structures, although as a matter of style one would normally use the same names only for closely related objects.

A struct declaration defines a type. The right brace that terminates the list of members may be followed by a list of variables, just as for any basic type. That is,



	struct maxpt = { 320, 200 };

A member of a particular structure is referred to in an expression by a construction of the form


	
	screen.pt1.x


##Structures and Functions







`makepoint` can now be used to initialize any structure dynamically

##Structures and Pointers

If a large structure is to be passed to a function, it is generally more efficient to pass a pointer than to copy the whole structure. Structure pointers are just like pointers to ordinary variables. E.g.
	pp = &origin;
	




	rp->pt1.x
	(r.pt1).x
	(rp->pt1).x



The structure declaration:

	};



		char *word;
		int count;
	} keytab[] = {
		"auto", 0,
		"break", 0,
		"case", 0,
		"char", 0
	}

The initializers are listed in pairs corresponding to the structure members. It would be more precise to enclose the initializers for each "row" or structure in braces, as in


##Self-referential Structures

We will use a data structure called a binary tree.



To find out whether a new word is already in the tree, start at the root and compare the new word to the word stored at that node. If they match, the question is answered affirmatively. If the new record is less than the tree word, continue searching at the left child, otherwise at the right child. If there is no child in the required direction, the new word is not in the tree, and in fact the empty slot is the proper place to add the new word. This process is recursive, since the search from any node uses a search from one of its children. Accordingly, recursive routines for insertion and printing will be most natural.

Going back to the description of a node, it is most conveniently represented as a structure with four components:

	struct tnode {				#the tree node
		char *word;				#points to the text
		int count; 				#number of occurances
		struct tnode *left;		#left child
		struct tnode *right;	#right child
	};













		struct nlist *next;		#next entry in chain
		char *name;				#defined name
		char *defn;				#replacement text
	};

	#define HASHSIZE 101

		return hashval % HASHSIZE;


















	if (utype == STRING)

















----------	| -------------------------
d 			| decimal integer; int *
i			| integer; int *. The integer may be in octal (leading 0) or hexadecimal (leading 0x or 0X).
c			| characters; char *. The next input characters (default 1) are placed at the indicated spot. The normal skip-over white space is suppressed; to read the next non-white space character, use %1s
s			| character string (not quoted); char *, pointing to an array of characters long enough for the string and a terminating '\0' that will be added.

	scanf("%d %s %d", &day, monthname, &year);

No & is used with monthname, since an array name is a pointer.

scanf ignores blanks and tabs in its format string. Furthermore, it skips over white space (blanks, tabs, newlines, etc.) as it looks for input values. 

##File Access

The next step is to write a program that accesses a file that is not already connected to the program. 

The rules are simple. Before it can be read or written, a file has to be opened by the library function fopen. fopen takes an external name like x.c or y.c, does some housekeeping and negotiation with the operating system (details of which needn't concern us), and returns a pointer to be used in subsequent reads or writes of the file.

This pointer, called the file pointer, points to a structure that contains information about the file, such as the location of a buffer, the current character position in the buffer, whether the file is being read or written, and whether errors or end of file have occurred. 

Users don't need to know the details, because the definitions obtained from <stdio.h> include a structure declaration called FILE.

The only declaration needed for a file pointer is exemplified by


##Line Input and Output


strchr(s,c)















Whenever input or output is to be done on the file, the file descriptor is used instead of the name to identify the file.

(A file descriptor is analogous to the file pointer used by the standard library, or to the file handle of MS-DOS.) All information about an open file is maintained by the system; the user program refers to the file only by the file descriptor.

