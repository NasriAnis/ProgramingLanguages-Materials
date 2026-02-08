syntax:
```
struct [structure tag] {
	member definition;
	member definition;
	...
} [one or more structure variables];

# declaration
struct [structure tag] [declared tag];

# appen definition to memeber of a declared tag
[declared tag].[member] = [definiton]
```

# Structures as function arguments
example:
```
#include <iostream> 
#include <cstring> u

sing namespace std; 

void printBook( struct Books book ); 

struct Books { char title[50]; 
	char author[50]; 
	char subject[100]; 
	int book_id; 
}; 

int main() { 
	struct Books Book1; // Declare Book1 of type Book 
	struct Books Book2; // Declare Book2 of type Book 
	
	// book 1 specification 
	strcpy( Book1.title, "Learn C++ Programming"); 
	strcpy( Book1.author, "Chand Miyan"); 
	strcpy( Book1.subject, "C++ Programming"); 
	Book1.book_id = 6495407; 
	
	// book 2 specification 
	strcpy( Book2.title, "Telecom Billing"); 
	strcpy( Book2.author, "Yakit Singha"); 
	strcpy( Book2.subject, "Telecom"); 
	Book2.book_id = 6495700; 
	
	// Print Book1 info 
	printBook( Book1 ); 
	
	// Print Book2 info 
	printBook( Book2 ); 
	
	return 0; 
} 

void printBook( struct Books book ) { 
	cout << "Book title : " << book.title <<endl; 
	cout << "Book author : " << book.author <<endl; 
	cout << "Book subject : " << book.subject <<endl; 
	cout << "Book id : " << book.book_id <<endl; 
}

```
# Pointers to structures
to define a pointer to a structure we use the syntax:
`struct Books *struct_pointer;`

Now, you can store the address of a structure variable in the above defined pointer variable. To find the address of a structure variable, place the & operator before the structure's name as follows:
`struct_pointer = &Book1;`

To access the members of a structure using a pointer to that structure, you must use the -> operator as follows:
`struct_pointer->title;`
# typedef keyword
There is an easier way to define structs or you could "alias" types you create.

```
typedef struct { 
	char title[50]; 
	char author[50]; 
	char subject[100]; 
	int book_id; 
} Books;
```

`Books Book1, Book2;`

You can use **typedef** keyword for non-structs as well as follows:
```
typedef long int *pint32; 
pint32 x, y, z;
```