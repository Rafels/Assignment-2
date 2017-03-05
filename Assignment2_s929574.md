#Assignment 2

##Problem 1
####Write a C++ program to sort an array of numbers in an ascending order and descending order based on user’s choice and display them.

In order to solve this problem, the program makes use of the *Algorithm* library wich provides the functions *sort* and *reverse*.
The *sort* function is quite handy as it sorts all the values in an ascending order, ether it being characters or integer values. The *reverse* function then reverses the order, wich comes in hand when the program orders the values in a descending order.
In the start of the program prompts the user to enter the ten integer values, it then displays the values and asks the user in which order the values will be sorted.
The result is then displayed. If the user enters a charachter the program will allert the user of a wrong input and quit.

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
##Problem 2
###Write a C++ program to sort string (name) in an alphabetical order. For example if a user enters a string "bye", then the 
###output of the program will be "bey".

This program uses the *string* and *algorithm* libraries in order to easily get the inputed string and then sort the charachters in ascending order. The *getline()* function uses an input, in this case *cin* and then gives the line to 

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
**Results:**
```
Please enter you sentence.
Hello, how are you?
Hello, how are you?
   ,?Haeehlloooruwy
```

##Problem 3
###Allocation and deallocation of mono-dimensional and bi-dimensional arrays represented by pointers.
##a)
###Declare and implement a function CreateArray(...) that returns a pointer to an array of n integers.

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
##b)
###Declare and implement a function DeleteArray(...) that takes and deletes an array of integers.

**The Code**
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
##c)
###Declare and implement a function CreateMatrix(...) that returns a pointer to an array of arrays of n × m floats.

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
##d)
###Declare and implement a function Deletematrix(...) that takes and deletes this kind of matrix.

**The Code**
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
##e)
###Declare and implement  a  function  DisplayMatrix(...)  that  displays  the  address  of  the matrix of floats in the memory and all its elements.

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
	std::cout<<"The size of your Matrix is: "<<n<<" X "<<m<<" and the address of the first place is: "<<arrayP<<std::endl;

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
##Problem 4
##a)
###Declare and implement a function DisplayPointerInfo(...) which displays on screen the address of the first element of an array represented by a pointer. If multiple elements of the array exist, then display the address of all the values represented by a pointer.

**The code**
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
	std::cout<<"The size of your Matrix is: "<<n<<" X "<<m<<" and the address of the first place is: "<<arrayP<<std::endl;

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
##b)
###To test the DisplayPointerInfo(...)function, declare two integer pointers a and b to dynamically allocate arrays of integers for n elements (n should be an input from the user).
###Array a will be filled with even numbers, and array b will be filled with odd numbers.

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
##Problem 5
###Define an int* pointer variable a. Then:
##a)
###Use new to make a point to a dynamic array of 5 cells of type int.
##b)
###Write a loop to fill a with values 5, 7, 16, 12, 15.
##c)
###Using Hex, print the pointer address stored in a.
##d)
###Write a loop to print the values in a with one cell per line.
##e)
###Delete the dynamic memory allocated to a using delete [ ].
**The Code:**
```c++
#include <iostream>

using namespace std;

int main()
{
	int* a;
	a = new int[5];

	for (int i = 0; i < 5; ++i)
	{
		switch(i)
		{
			case 0:
				a[i] = 5;
				break;
			case 1:
				a[i] = 7;
				break;
			case 2:
				a[i] = 16;
				break;
			case 3:
				a[i] = 12;
				break;
			case 4:
				a[i] = 15;
				break;
		}
	}
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

##Problem 6
###Define a struct named Date to keep track of dates. Provide functions that read dates from an input and finally display dates as an output.

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

##Problem 7
###Write a C++ program with a class having two private variables and one member function which will return the area of a triangle.

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
##Problem 8
###Write a C++ program with a class that takes 10 input integers in the main function and pass them to the default constructor of the class. 
Finally, your program should return (display)the sum of the 10 input numbers.

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
##Problem 9
###Perform addition operation on complex data using class and object. 
###The program should ask for real and imaginary part of two complex numbers, and display the real and imaginary parts of their sum.
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

	cout<<"Enter you 1st number."<<endl;
	number1.setNumbers();

	cout<<"Enter you 2nd number."<<endl;
	number2.setNumbers();
	result = number1.add(number2);

	cout<<"The sum of the numbers equal: ";
	result.printnumber();

	return 0;
}

```
##Problem 10
###Write the definition for a class called Distance that has data member feet as integer and inches as float. The class has the following member functions:
###void set(int, float) to give value to object void disp() to display distance in feet and inches Distance add(distance) to sum two distances & return distance
###Write a main function to create three distance objects. Set the value in two objects and call add() to calculate sum and assign it in the third object. 
###Finally, display all distances.

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
