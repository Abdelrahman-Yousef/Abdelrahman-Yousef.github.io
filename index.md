# **const** :

* ## The const keyword specifies that a variable's value is constant and tells the compiler to prevent the programmer from modifying it.

>Example Code :

int main(){

   const int i = 5;

   i = 10;   // C3892

   i++;   // C210

}

* ## In C++, you can specify the size of an array with a const variable as follows:

// constant_values2.cpp

// compile with: /c

const int maxarray = 255;

char store_char[maxarray];  // allowed in C++; not allowed in C

* ## Const Keyword With Pointer Variables:

1. ### When the pointer variable point to a const value :

Syntax : 

const data_type* var_name;

>Example Code : 

// C++ program to demonstrate the

// above concept

#include \<iostream>

using namespace std;

// Driver Code

int main()
{

	int x{ 10 };
	char y{ 'M' };

	const int* i = &x;
	const char* j = &y;

	// Value of x and y can be altered,
	// they are not constant variables
	x = 9;
	y = 'A';

	// Change of constant values because,
	// i and j are pointing to const-int
	// & const-char type value
	// *i = 6;
	// *j = 7;

	cout << *i << " " << *j;
}

2. ### When the const pointer variable point to the value :

Syntax :

data_type* const var_name;

// C++ program to demonstrate the

// above concept

#include \<iostream>

using namespace std;

// Driver Code

int main()
{

	// x and z non-const var
	int x = 5;
	int z = 6;

	// y and p non-const var
	char y = 'A';
	char p = 'C';

	// const pointer(i) pointing
	// to the var x's location
	int* const i = &x;

	// const pointer(j) pointing
	// to the var y's location
	char* const j = &y;


	// The values that is stored at the memory location can modified
	// even if we modify it through the pointer itself
	// No CTE error
	*i = 10;
	*j = 'D';

	// CTE because pointer variable
	// is const type so the address
	// pointed by the pointer variables
	// can't be changed
	// *i = &z;
	// *j = &p;

	cout << *i << " and " << *j
		<< endl;
	cout << i << " and " << j;

	return 0;
}

3. ### When const pointer pointing to a const variable :

Syntax :

const data_type* const var_name;

// C++ program to demonstrate

// the above concept

#include \<iostream>

using namespace std;

// Driver code

int main()
{

	int x{ 9 };

	const int* const i = &x;

	// *i=10;
	// The above statement will give CTE
	// Once Ptr(*i) value is
	// assigned, later it can't
	// be modified(Error)

	char y{ 'A' };

	const char* const j = &y;

	// *j='B';
	// The above statement will give CTE
	// Once Ptr(*j) value is
	// assigned, later it can't
	// be modified(Error)

	cout << *i << " and " << *j;

	return 0;
}

* ## Constant Function Parameters And Return Type:

A function() parameters and return type of function() can be declared as constant. Constant values cannot be changed as any such attempt will generate a compile-time error.

// C++ program to demonstrate the

// above approach

#include \<iostream>

using namespace std;

// Function foo() with variable

// const int

void foo(const int y)
{

	// y = 6; const value
	// can't be change
	cout << y;
}

// Function foo() with variable int

void foo1(int y)
{

	// Non-const value can be change
	y = 5;
	cout << '\n'
		<< y;
}

// Driver Code

int main()
{

	int x = 9;
	const int z = 10;

	foo(z);
	foo1(x);

	return 0;
}

For const return type: The return type of the function() is const and so it returns a const integer value to us

// C++ program for the above approach

#include \<iostream>

using namespace std;

const int foo(int y)
{

	y--;
	return y;
}

int main()
{

	int x = 9;
	const int z = 10;
	cout << foo(x) << '\n'
		<< foo(z);

	return 0;
}

For const return type and const parameter: Here, both return type and parameter of the function are of const types

// C++ program for the above approach

#include \<iostream>

using namespace std;

const int foo(const int y)
{

	// y = 9; it'll give CTE error as
	// y is const var its value can't
	// be change
	return y;
}

// Driver code

int main()
{

	int x = 9;
	const int z = 10;
	cout << foo(x) << '\n'
		<< foo(z);

	return 0;
}

___
___


# **&** :

* ## Use & to get the address of a variable

std::string mrSamberg("Andy");

std::string* theBoss;

theBoss = &mrSamberg;

* ## Use & to declare a reference to a type

std::string mrSamberg("Andy");

std::string& theBoss = mrSamberg;

* ## Pass by reference (C++ only)

Pass-by-reference means to pass the reference of an argument in the calling function to the corresponding formal parameter of the called function. The called function can modify the value of the argument by using its reference passed in.

#include <stdio.h>

void swapnum(int &i, int &j) {

  int temp = i;

  i = j;

  j = temp;

}

int main(void) {

  int a = 10;

  int b = 20;

  swapnum(a, b);

  printf("A is %d and B is %d\n", a, b);

  return 0;
}


When the function swapnum() is called, the values of the variables a and b are exchanged because they are passed by reference. The output is:

A is 20 and B is 10

* ## In the return type of a function

int g_test = 0;

int& getNumberReference()
{

     return g_test;
}

int getNumberValue()
{
    
     return g_test;
}

int main()
{

    int& n = getNumberReference();
    int m = getNumberValue();
    n = 10;
    cout << g_test << endl; // prints 10
    g_test = 0;
    m = 10;
    cout << g_test << endl; // prints 0
    return 0;
}
