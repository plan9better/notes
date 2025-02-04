In c++ when a class constructor can take 1 variable, then that constructor is also implicitly used for type casting. e.g.
```cpp
// C++ program to illustrate default
// constructor without 'explicit'
// keyword
#include <iostream>
using namespace std;

class Complex {
private:
	double real;
	double imag;

public:

	// Parameterized constructor
	Complex(double r = 0.0, 
			double i = 0.0) : real(r), 
							imag(i)
	{
	}

	// A method to compare two 
	// Complex numbers
	bool operator == (Complex rhs)
	{
		return (real == rhs.real && 
				imag == rhs.imag);
	}
};

// Driver Code
int main()
{
	// a Complex object
	Complex com1(3.0, 0.0);

	if (com1 == 3.0) // com1 == Complex temp(3.0)
		cout << "Same";
	else
		cout << "Not Same";
	return 0;
}
```

This can be prohibited with the *explicit keyword*
```cpp
// C++ program to illustrate 
// default constructor with 
// 'explicit' keyword
#include <iostream>
using namespace std;

class Complex {
private:
	double real;
	double imag;

public:
	// Default constructor
	explicit Complex(double r = 0.0, 
					double i = 0.0) : 
					real(r), imag(i)
	{
	}

	// A method to compare two 
	// Complex numbers
	bool operator == (Complex rhs)
	{
		return (real == rhs.real && 
				imag == rhs.imag);
	}
};

// Driver Code
int main()
{
	// a Complex object
	Complex com1(3.0, 0.0);

	if (com1 == 3.0)
		cout << "Same";
	else
		cout << "Not Same";
	return 0;
}

```