# Assignment 2

## Problem 1
#### Write a C++ program to sort an array of numbers in an ascending order and descending order based on user’s choice and display them.

To solve this problem, the program makes use of the *Algorithm* library which provides the functions *sort* and *reverse*.
The *sort* function is quite handy as it sorts all the values in an ascending order, ether it being characters or integer values. The *reverse* function then reverses the order, which comes in handy when the program orders the values in a descending order.
In the start of the program prompts the user to enter the ten integer values, it then displays the values and asks the user in which order the values will be sorted.
The result is then displayed. If the user enters a character the program will alert the user of a wrong input and quit.

**The Code:**
```c++
#include <iostream>
#include <algorithm>
using namespace std; 

int main()
{
	int thisArray[10] = {0};
	int i,j,store;
	char choice;
	cout<<"Please input 10 integers.\n";
	for (i = 0; i < 10; ++i)
	{
		cin>>thisArray[i];
	}
	cout<<"Your input was: ";
	for (i = 0; i < 10; ++i)
	{
		cout<<thisArray[i]<<" ";
	}
	cout<<"\nIf you wish to sort your numbers in ascending order press ""a""\n";
	cout<<"If you wish to sort your numbers in descending order press ""d""\n";
	cin>>choice;
	if (choice == 'a')
	{
		sort(thisArray,thisArray + 10);
	} else
	if (choice == 'd')
	{
		sort(thisArray,thisArray + 10);
		reverse(thisArray,thisArray + 10);
	}else
	{
		cout<<"Not a valid choice.";
	}
	cout<<"Your array is now: ";
	for (i = 0; i < 10; ++i)
	{
		cout<<thisArray[i]<<" ";
	}

	return 0;
}
```
**Results:**

```
Please input 10 integers.
2
5
4
7
8
9
10
3
6
1
Your input was: 2 5 4 7 8 9 10 3 6 1
If you wish to sort your numbers in ascending order press a
If you wish to sort your numbers in descending order press d
d
Your array is now: 10 9 8 7 6 5 4 3 2 1
```
**Alternative Results:**
```
a
Your array is now: 1 2 3 4 5 6 7 8 9 10
```
## Problem 2 ##
#### Write a C++ program to sort string (name) in an alphabetical order. For example if a user enters a string "bye", then the output of the program will be "bey".

This program uses the *string* and *algorithm* libraries to easily get the inputted string and then sort the characters in ascending order. The *getline()* function uses an input, in this case *cin* and then gives the line to the string *Word*. By using the *.begin()* and *.end()* functions the *sort* function can determine the start and end of the line that will be sorted.

**The Code:**
```c++
#include <iostream>
#include <string>
#include <algorithm>

int main()
{
	std::cout<<"Please enter you sentence."<<std::endl;
	std::string Word;
	std::getline(std::cin, Word);
	std::cout<<Word<<std::endl;
	std::sort(Word.begin(),Word.end());
	std::cout<<Word;
	return 0;
}

```
**The Results:**
```
Please enter you sentence.
Hello, how are you?
Hello, how are you?
   ,?Haeehlloooruwy
```

## Problem 3
#### Allocation and deallocation of mono-dimensional and bi-dimensional arrays represented by pointers.
## a)
#### Declare and implement a function CreateArray(...) that returns a pointer to an array of n integers.

To solve this problem, the program uses a function which creates a pointer to an array. The array is created by using the *new* function, which will allocate several spaces for integer values, the created pointer will then point to the first address of the array before being returned. The size of the array is determined by the user and used as an input when calling the function *CreateArray*. The output is only there to check if the input is correct and that the function has been called successfully.

**The Code:**
```c++
#include <iostream>

int* CreateArray(int n);

int main()
{	
	int n;
	int* arrayP;
	std::cout<<"Enter the number of spaces for your array"<<std::endl;
	std::cin>>n;
	arrayP = CreateArray(n);
	std::cout<<"The size of your array is: "<<n<<" and the address of the first place is: "<<arrayP;

	return 0;
}

int* CreateArray(int n)
{
	int* pArray = new int[n];
	return pArray;
}

```
**The results:**
```
Enter the number of spaces for your array

5
The size of your array is: 5 and the address of the first place is: 0x741958
```
## b)
#### Declare and implement a function DeleteArray(...) that takes and deletes an array of integers.

This program creates first a pointer *A* to an array of type int and size 10, using the *new* function. It then uses that pointer as an input when calling the *DeleteArray* function. The *DeleteArray* function uses the *delete[]* function on the pointer, by using brackets([]) one tells the *delete* function to delete an array of pointers. The value and address is printed out before and after the use of *DeleteArray*, it shows the same value and address, but the memory is now de-allocated. 


**The Code:**
```c++
#include <iostream>

void DeleteArray(int* array);

int main()
{	
	int* A = new int[10];

	std::cout<<"Your first value is: "<<A[0]<<std::endl;
	std::cout<<"The address of the first value is: "<<A<<std::endl;

	DeleteArray(A);
	
	std::cout<<"The first value is now: "<<A[0]<<std::endl;
	std::cout<<"The address of the first value is now: "<<A<<std::endl;

	return 0;
}

void DeleteArray(int* array)
{
	delete[] array;
}

```
**The Results:**
```
Your first value is: 6952504
The address of the first value is: 0x6a1958
The first value is now: 6952504
The address of the first value is now: 0x6a1958

```
## c)
#### Declare and implement a function CreateMatrix(...) that returns a pointer to an array of arrays of n × m floats.

This problem is solved by using the *new* function with a pointer to a pointer *pArray* to create an array of n-pointers. The array is then run through a for-loop which creates an array of m-values for each of the pointer, this is also achieved by using the *new* function. The n x m size is determined and inputted by the user, and then used as an input when calling the *CreateMatrix* function.

**The Code:**
```c++
#include <iostream>

float** CreateMatrix(int n, int m);

int main()
{	
	int n;
	int m;
	float** arrayP;
	std::cout<<"Enter the number of Rows for your Matrix"<<std::endl;
	std::cin>>n;
	std::cout<<"Enter the number of Coloumns for your Matrix"<<std::endl;
	std::cin>>m;
	arrayP = CreateMatrix(n,m);
	std::cout<<"The size of your Matrix is: "<<n<<" X "<<m<<" and the address of the first place is: "<<arrayP;

	return 0;
}

float** CreateMatrix(int n, int m)
{
	float** pArray = new float*[n];
	for (int i = 0; i < n; ++i)
	{
		pArray[i] = new float[m];
	}
	return pArray;
}
```
**The Result:**
```
Enter the number of Rows for your Matrix
5
Enter the number of Coloumns for your Matrix
5
The size of your Matrix is: 5 X 5 and the address of the first place is: 0xf81958
```

## d)
#### Declare and implement a function Deletematrix(...) that takes and deletes this kind of matrix.

To solve this problem, the program first creates a 10x10 matrix in the same manner as the previous problem. The matrix is then used as an input in the *DeleteMatrix* function. The *DeleteMatrix* function uses a for-loop to delete each of the ten arrays in the matrix, it then uses the *delete* function on the pointer array. No result is printed as there is no way of showing the memory de-allocation.


**The Code:**
```c++
#include <iostream>

void DeleteMatrix(float** matrix);

int main()
{	
	float** matrix = new float*[10];

	for (int i = 0; i < 10; ++i)
	{
		matrix[i] = new float[10];
	}

	DeleteMatrix(matrix);

	return 0;
}

void DeleteMatrix(float** matrix)
{
	for (int i = 0; i < 10; ++i)
	{
		delete[] matrix[i];
	}
	
	delete[] matrix;
}
```
## e)
#### Declare and implement  a  function  DisplayMatrix(...)  that  displays  the  address  of  the matrix of floats in the memory and all its elements.

This program uses the *CreateMatrix* function from the previous 3c problem. It uses the result plus the n x m size as inputs for using the *DisplayMatrix* function. The function uses two for-loops with *i* and *j* as iterators, it then prints out each of the address in the matrix by using the iterators in the matrix. When each row has been printed out, the line ends to have a cleaner output.

**The Code:**
```c++
#include <iostream>

float** CreateMatrix(int n, int m);
void displayMatrix(float** Matrix, int n, int m);

int main()
{	
	int n;
	int m;
	float** arrayP;
	std::cout<<"Enter the number of Rows for your Matrix"<<std::endl;
	std::cin>>n;
	std::cout<<"Enter the number of Coloumns for your Matrix"<<std::endl;
	std::cin>>m;
	arrayP = CreateMatrix(n,m);
	std::cout<<"The size of your Matrix is: "<<n<<" X "<<m<<std::endl;
	std::cout<<"The address of the Matrix are:"<<std::endl;

	displayMatrix(arrayP, n, m);

	return 0;
}

float** CreateMatrix(int n, int m)
{
	float** pArray = new float*[n];
	for (int i = 0; i < n; ++i)
	{
		pArray[i] = new float[m];
	}
	return pArray;
}

void displayMatrix(float** Matrix, int n, int m)
{
	for (int i = 0; i < n; ++i)
	{
		for (int j = 0; j < m; ++j)
		{
			std::cout<<&Matrix[i][j]<<" ";
		}
		std::cout<<std::endl;
	}

}
```
**The Results:**
```
Enter the number of Rows for your Matrix
5
Enter the number of Coloumns for your Matrix
5
The size of your Matrix is: 5 X 5
The address of the Matrix are:
0x791978 0x79197c 0x791980 0x791984 0x791988
0x791638 0x79163c 0x791640 0x791644 0x791648
0x791658 0x79165c 0x791660 0x791664 0x791668
0x791678 0x79167c 0x791680 0x791684 0x791688
0x791698 0x79169c 0x7916a0 0x7916a4 0x7916a8
```

## Problem 4
## a)
#### Declare and implement a function DisplayPointerInfo(...) which displays on screen the address of the first element of an array represented by a pointer. If multiple elements of the array exist, then display the address of all the values represented by a pointer.

This program lets the user choose the size of the array, the size is then used to create an array which points to the pointer *A*. The pointer and the size are then used as the input when calling the *DisplayPointerInfo* function. The function displays the address of the first element in the array. Tt then runs through a for-loop, which uses the size as the limit, if the size is greater than one it will print out the remaining elements.


**The code**
```c++
#include <iostream>

using namespace std;

void DisplayPointerInfo(int* arrayP, int m);

int main()
{
	int n;
	int* A;

	cout<<"Please enter the size of your array"<<endl;
	cin>>n;

	A = new int[n];

	DisplayPointerInfo(A,n);


	
	return 0;
}

void DisplayPointerInfo(int* arrayP, int m)
{
	cout<<"The Address of the first pointer is:";
	cout<<&arrayP[0];
	cout<<endl;
	cout<<"The Address of the remaining pointers are:"<<endl;
	for (int i = 1; i < m; ++i)
	{
		cout<<&arrayP[i]<<" ";
	}
	cout<<endl;
}
```
## b)
#### To test the DisplayPointerInfo(...)function, declare two integer pointers a and b to dynamically allocate arrays of integers for n elements (n should be an input from the user). Array a will be filled with even numbers, and array b will be filled with odd numbers.

This program uses the *DisplayPointerInfo* function and a new function *DisplayArrayValue* to check if the values are correct. 
First the two pointers are created and an array is created for each of them with the same size, which has been given by the user. The *cstdlib* library is included in this program in order to use the *rand()*function, which will fill the arrays with even and odd numbers. A while-loop is used for each array, they run until the size of the array has been reached. For each iteration, a random value is created and checked if it is either even or odd. If the if-statement is true, then *i* is added one and the loop looks for the next value. The arrays address and values are then displayed. The *DisplayArrayValue* uses a simple for-loop to run through the array elements and display their values.


**The code:**
```c++
#include <iostream>
#include <cstdlib>

using namespace std;

void DisplayPointerInfo(int* arrayP, int m);
void DisplayArrayValue(int* arrayP, int m);

int main()
{
	int n;
	int* a;
	int* b;

	cout<<"Please enter the size of your array"<<endl;
	cin>>n;
	a = new int[n];
	b = new int[n];
	int i = 0;
	int x = 0;

	while(i != n)
	{
		x = rand();
		if (x%2 == 0)
		{
			a[i] = x;
			i++;
		}
	}
	i = 0;
	while(i != n)
	{
		x = rand();
		if (x%2 != 0)
		{
			b[i] = x;
			i++;
		}
	}
	cout<<"Array a."<<endl;
	DisplayPointerInfo(a,n);
	DisplayArrayValue(a,n);
	cout<<"Array b."<<endl;
	DisplayPointerInfo(b,n);
	DisplayArrayValue(b,n);


	
	return 0;
}
void DisplayArrayValue(int* arrayP, int m)
{
	cout<<"The values of the array are:"<<endl;
	for (int i = 0; i < m; ++i)
	{
		cout<<arrayP[i]<<" ";
	}
	cout<<endl;
}

void DisplayPointerInfo(int* arrayP, int m)
{
	cout<<"The Address of the first pointer is:";
	cout<<&arrayP[0];
	cout<<endl;
	cout<<"The Address of the remaining pointers are:"<<endl;
	for (int i = 1; i < m; ++i)
	{
		cout<<&arrayP[i]<<" ";
	}
	cout<<endl;
}
```
**The Results:**
```
Please enter the size of your array
5
Array a.
The Address of the first pointer is:0x1041958
The Address of the remaining pointers are:
0x104195c 0x1041960 0x1041964 0x1041968
The values of the array are:
6334 26500 15724 11478 29358
Array b.
The Address of the first pointer is:0x1041978
The Address of the remaining pointers are:
0x104197c 0x1041980 0x1041984 0x1041988
The values of the array are:
5705 28145 23281 16827 9961
```
## Problem 5
#### Define an int* pointer variable a. Then:
## a) 
#### Use new to make a point to a dynamic array of 5 cells of type int.
## b)
#### Write a loop to fill a with values 5, 7, 16, 12, 15.
## c)
#### Using Hex, print the pointer address stored in a.
## d)
#### Write a loop to print the values in a with one cell per line.
## e)
#### Delete the dynamic memory allocated to a using delete [ ].

This problem is quite simply to do as I only followed the instructions given. In the first line inside main, the pointer is declared, in the next line the dynamic array is created with a size of 5. Then the values are given to each of the array elements. A for-loop is then used to print out the address of the elements, and converted using the *hex* function. The array is then deleted by using the *delete[]* function on the pointer.


**The Code:**
```c++
#include <iostream>

using namespace std;

int main()
{
	int* a;
	a = new int[5];
	
	a[0] = 5;
	a[1] = 7;
	a[2] = 16;
	a[3] = 12;
	a[4] = 15;

	for (int i = 0; i < 5; ++i)
	{
		cout<<hex<<&a[i]<<endl;
	}
	cout<<"The stored values are:"<<endl;
	for (int i = 0; i < 5; ++i)
	{
		cout<<a[i]<<endl;
	}

	delete[] a;


	return 0;
}
```
**The Results:**
```
0xf71958
0xf7195c
0xf71960
0xf71964
0xf71968
The stored values are:
5
7
16
12
15
```

## Problem 6
#### Define a struct named Date to keep track of dates. Provide functions that read dates from an input and finally display dates as an output.

The struct *Date* is declared before main and is given to integer variables and one string variable, the struct variable is called *myDate*. The user is then prompted to input the day, month and year, the values are fed to *myDate* in to the right variables.  
This program is quite simple and may be prone to errors as the program does not check if the input days are correct per the given month or even if the string given is a valid month.


**The Code:**
```C++
#include <iostream>
#include <string>

struct Date
{
	int day;
	std::string month;
	int year;
} myDate;

void printDate(Date yourDate);

int main()
{
	std::cout<<"Enter day:";
	std::cin>>myDate.day;
	std::cout<<std::endl;
	std::cout<<"Enter the month:"<<std::endl;
	std::cin>>myDate.month;
	std::cout<<std::endl;
	std::cout<<"Enter Year:";
	std::cin>>myDate.year;
	std::cout<<std::endl;

	printDate(myDate);

	return 0;
}

void printDate(Date yourDate)
{
	std::cout<<"You entered the following date:"<<yourDate.day<<"/"<<yourDate.month<<"/"<<yourDate.year<<std::endl;
}

```
**The Results:**
```
Enter day:15

Enter the month:
January

Enter Year:2017

You entered the following date:15/January/2017
```

## Problem 7
#### Write a C++ program with a class having two private variables and one member function which will return the area of a triangle.

The Class is initialized with two private variables *height* and *length* and two public member functions. The *set_values* function is used to access the private variables in the class and assign them values. The *triangleArea* takes the *length* and *height* multiplies them and divides them by 2, the function returns the area.
In main, the variables are declared and the values are inputted by the user. The object triangle of type triangleArea i declared and the values of the triangle are set by using the function *set_values*, the area is calculated and printed out.


**The Code:**
```C++
#include <iostream>

using namespace std;

class triangleArea 
{
private:
	int height, length;
public:
	void set_values(int,int);
	float area();
};

void triangleArea::set_values(int x, int y)
{
	height = x;
	length = y;
}
float triangleArea::area(void)
{
	float a;
	a = (height*length)/2;
	return a;
}

int main()
{
	int l,h;
	cout<<"Enter the length of the triangle:"<<endl;
	cin>>l;
	cout<<"Enter the height of the triangle:"<<endl;
	cin>>h;

	triangleArea triangle;
	triangle.set_values(l,h);
	cout<<"The area of the triangle is:"<<triangle.area();
	return 0;
}

```
**The Results:**
```
Enter the length of the triangle:
15
Enter the height of the triangle:
10
The area of the triangle is:75
```
## Problem 8
#### Write a C++ program with a class that takes 10 input integers in the main function and pass them to the default constructor of the class. Finally, your program should return (display)the sum of the 10 input numbers.

The class Array is used to collect the values and calculate the sum. The class has one private variable of type int array with a set number of elements, and three member functions *Array()*, *setValues()* and *addValues*. The *Array()* is actually a constructor and is used to fill the array with zero's and tell the user that the object has been created. The *setValues* function uses a for-loop to fill the array elements, it takes an integer values as input and fills the elements using the variable. When the values are filled, the *addValues* function is used to calculate the sum of all the array elements and return the sum.

**The Code:**
```C++
#include <iostream>

using namespace std;

class Array
{
private:
	int input[10];
public:
	Array();
	void setValues(int v);
	int addValues();
};

Array::Array(void)
{
	for (int i = 0; i < 10; ++i)
	{
		input[i] = 0;
	}
	cout<<"Object created and initialized to zero."<<endl;

}

void Array::setValues(int v)
{
	for (int i = 0; i < 10; ++i)
	{
		cin>>v;
		input[i] = v;
	}
}
int Array::addValues()
{
	int sum = 0;
	for (int i = 0; i < 10; ++i)
	{
		sum = sum + input[i];
	}
	return sum;
}

int main()
{
	int mySum;
	int input = 0;

	Array myValues;
	cout<<"Please input 10 integer values:"<<endl;
	myValues.setValues(input);

	mySum = myValues.addValues();

	cout<<"The sum of the values are = "<<mySum;
	


	return 0;
}
```
**The Results**
```
Object created and initialized to zero.
Please input 10 integer values:
12
14
23
43
54
3
476
34
76
13
The sum of the values are = 748
```

## Problem 9
#### Perform addition operation on complex data using class and object. The program should ask for real and imaginary part of two complex numbers, and display the real and imaginary parts of their sum.

The program uses a Class called imNumber which has two private double variables, one public constructor and three public member functions. The constructor sets the img and real variables to zero and assigns *r* to *real* and *i* to *img*. The *setNumber* function is used to set the real and imaginary values of the complex number, it prompts the user to input the real and imaginary number and uses the *this* function to achieve this.
The *add* function uses an object to collect the sum of the imaginary number and the real number, the object is then return when the sum has been added up. This is done by using the *this* function which gets the value of the object and sums it with the second function. The final function *printNumber* displays the value of the complex number. In the main function three object are declared, two for the complex numbers and one for the results. The values are set, the numbers are added and then displayed using the class functions.


**The Code:**
```C++
#include <iostream>
#include <complex>

using namespace std;

class imNumber
{
private:
	double img,real;
public:
	imNumber(double r = 0, double i = 0):real(r), img(i) {};

	void setNumbers(void)
	{
		cout<<"Enter the real value: ";
		cin>> this->real;
		cout<<"Enter the imaginary value: ";
		cin>> this->img;
	}
	imNumber add(const imNumber& c)
	{
		imNumber comp;
		comp.real = this->real + c.real;
		comp.img = this->img + c.img;
		return comp;
	}
	void printnumber(void)
	{
		cout<<this->real<<" + "<<this->img<<"j"<<endl;
	}
};

int main()
{
	imNumber number1;
	imNumber number2;
	imNumber result;

	cout<<"Enter your 1st number."<<endl;
	number1.setNumbers();

	cout<<"Enter your 2nd number."<<endl;
	number2.setNumbers();
	result = number1.add(number2);

	cout<<"The sum of the numbers equal: ";
	result.printnumber();

	return 0;
}

```
**The Results:**
```
Enter you 1st number.
Enter the real value: 12
Enter the imaginary value: 5
Enter you 2nd number.
Enter the real value: 14
Enter the imaginary value: 3
The sum of the numbers equal: 26 + 8j
```
## Problem 10
#### Write the definition for a class called Distance that has data member feet as integer and inches as float. The class has the following member functions: void set(int, float) to give value to object void disp() to display distance in feet and inches Distance add(distance) to sum two distances & return distance. Write a main function to create three distance objects. Set the value in two objects and call add() to calculate sum and assign it in the third object. Finally, display all distances.

The Class Distance uses two private variables *feet* and *inches* and three member functions called *set*, *disp* and *add*. The *set* function sets the feet and inches. The add function returns an object and calculates the sum between the object and the input object. If the inches are more than 12 then feet are added one. The *disp* function prints out the objects *feet* and *inches* variables. In the main three objects are created, two for the values and one for the sum. The values are then printed by using the *disp* function.

**The Code:**
```C++
#include <iostream>

using namespace std;

class Distance
{
private:
	int feet;
	float inches;
public:
	void set(int ft,float in)
	{
		feet = ft;
		inches = in;
	}
	void disp();
	Distance add(Distance);	
};

Distance Distance::add(Distance D)
{
	Distance t;
	t.inches = inches + D.inches;
	t.feet = 0;
	if (t.inches >= 12.0)
	{
		t.inches= t.inches - 12.0;
		t.feet++;
	}
	t.feet += feet + D.feet;
	return t;
}

void Distance::disp()
{
	cout<<feet<<"\'"<<inches<<"\" ";
}

int main()
{
	Distance dist1,dist2,dist3;
	dist1.set(9,5.7);
	dist2.set(15,7.7);
	dist3 = dist1.add(dist2);

	cout<<"The first distance is = ";
	dist1.disp();
	cout<<endl;
	cout<<"The second distance is = ";
	dist2.disp();
	cout<<endl;
	cout<<"The sum of the distances are = ";
	dist3.disp();
	cout<<endl;
	return 0;
}

```
**The Results:**
```
The first distance is = 9'5.7"
The second distance is = 15'7.7"
The sum of the distances are = 25'1.4"
```
