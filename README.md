# tips_and_tricks


__________________________________________
#  C++

```ruby

ostringstream ostrfrequency;                                                //@@@declaring output string stream     ---
ostrfrequency << frequency;                                                 //@@@Sending a number as a stream output---
string strfrequency = ostrfrequency.str();                                  //@@@the str() converts number into string-
```
__________________________________________

```ruby

# Read matrix frustration
//@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@---
//@@@                          Read matrix frustration                              //@@@                                   ---
//@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@                                   ---
double** read_initial_2D_double(string Filename, int x,int y)                       //@@@                                   ---
{                                                                                   //@@@                                   ---
    double** data_2D = new double* [x];                                             //@@@                                   ---
    for (int i = 0; i < x; i++)                                                     //@@@                                   ---
        data_2D[i] = new double[y];                                                 //@@@                                   ---
    ifstream file("Input/Frequency=0.1Degree=60.txt");                              //@@@                                   ---
    if (!file)                                                                      //@@@                                   ---
    {                                                                               //@@@                                   ---
        cout << "Matrix file is not here!" << endl;                                 //@@@                                   ---
        return data_2D;                                                             //@@@                                   ---
    }                                                                               //@@@                                   ---
    else                                                                            //@@@                                   ---
    {                                                                               //@@@                                   ---
        for (int i = 0; i < x; i++)                                                 //@@@                                   ---
        {                                                                           //@@@                                   ---
            for (int j = 0; j < y; j++)                                             //@@@                                   ---
            {                                                                       //@@@                                   ---
                double elem = 0.0;                                                  //@@@                                   ---
                file >> elem;                                                       //@@@                                   ---
                data_2D[i][j] = elem;                                               //@@@                                   ---
            }                                                                       //@@@                                   ---
        }                                                                           //@@@                                   ---
    }                                                                               //@@@                                   ---
    cout << Filename + "\t\tloaded" << endl;                                        //@@@                                   ---
    return data_2D;                                                                 //@@@                                   ---
}                                                                                   //@@@                                   ---
//@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@---
```


# count rows file in .txt 
________________________________________
```ruby
#include <tuple>// for tuple
//@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@---
//@@@                               count rows file in .txt                         //@@@                                   ---
//@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@                                   ---
tuple<int, int> count_rows_file(string file1) {                                     //@@@                                   ---
    int rows = 0, cols = 0;                                                         //@@@                                   ---
    string line, item;                                                              //@@@                                   ---
    ifstream file(file1);                                                           //@@@                                   ---
    while (getline(file, line))                                                     //@@@                                   ---
    {                                                                               //@@@                                   ---
        rows++;                                                                     //@@@                                   ---
        if (rows == 1)                                                              //@@@First row only:                    ---
        {                                                                           //@@@determine the number of columns    ---
            stringstream ss(line);                                                  //@@@Set up up a stream from this line  ---
            while (ss >> item) cols++;                                              //@@@Each item delineated by spaces     ---
        }                                                                           //@@@adds one to cols                   ---
    }                                                                               //@@@                                   ---
    file.close();                                                                   //@@@                                   ---
    cout << "\nFile had " << rows << " rows and " << cols << " columns\n" << endl;  //@@@                                   ---
    return {rows,cols};                                                             //@@@                                   ---
}                                                                                   //@@@                                   ---
//@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@---
int main()
{
    int rows, cols;
    tie(rows, cols) = count_rows_file("Input/Frequency=0.1Degree=60.txt"); //tie=constexpr tuple
    cout << rows << ',' << cols << endl;
    return 0;
}
```
or
```ruby
//@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@---
//@@@                               count rows file in .txt                         //@@@                                   ---
//@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@                                   ---
int count_rows_file(string file1)                                                   //@@@                                   ---
{                                                                                   //@@@                                   ---
    int rows = 0, cols = 0;                                                         //@@@                                   ---
    string line, item;                                                              //@@@                                   ---
    ifstream file(file1);                                                           //@@@                                   ---
    while (getline(file, line))                                                     //@@@                                   ---
    {                                                                               //@@@                                   ---
        rows++;                                                                     //@@@                                   ---
        if (rows == 1)                                                              //@@@First row only:                    ---
        {                                                                           //@@@determine the number of columns    ---
            stringstream ss(line);                                                  //@@@Set up up a stream from this line  ---
            while (ss >> item) cols++;                                              //@@@Each item delineated by spaces     ---
        }                                                                           //@@@adds one to cols                   ---
    }                                                                               //@@@                                   ---
    file.close();                                                                   //@@@                                   ---
    cout << "\nFile had " << rows << " rows and " << cols << " columns\n" << endl;  //@@@                                   ---
    return rows;                                                                    //@@@                                   ---
}                                                                                   //@@@                                   ---
//@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@---
``` 

## calculate time run
________________________________________
```ruby
#include<iostream>
  
	clock_t t= clock();                                                                         //start
	cout<<"\nTime taken by program is :\t"<< ((double)clock() - t) / CLOCKS_PER_SEC << " sec\n";//stop
``` 
## 2D array pointer 10*4 With initial values 0
________________________________________
```ruby
#include<iostream>
  
void add(double** a) {
	for (int i = 0; i < 10; i++) {
		for (int j = 0; j< 4; j++) {
			a[i][j] += 2;
		}
	}
}

int main() {

	double** arr = new double* [10];
	for (int i = 0; i < 10; i++) {
		arr[i] = new double[4]{ NULL };
	}
	
	add(arr);
	
	for (int i = 0; i < 10; i++) {
		for (int j = 0; j < 4; j++) {
			cout << arr[i][j] << '\t';
		}
		cout << endl;
	}
}
``` 
## Void pointers
________________________________________
```ruby
#include <iostream>
 
enum class Type
{
    INT,
    FLOAT,
    CSTRING
};
 
void printValue(void *ptr, Type type)
{
    switch (type)
    {
        case Type::INT:
            std::cout << *static_cast<int*>(ptr) << '\n'; // cast to int pointer and perform indirection
            break;
        case Type::FLOAT:
            std::cout << *static_cast<float*>(ptr) << '\n'; // cast to float pointer and perform indirection
            break;
        case Type::CSTRING:
            std::cout << static_cast<char*>(ptr) << '\n'; // cast to char pointer (no indirection)
            // std::cout knows to treat char* as a C-style string
            // if we were to perform indirection through the result, then we'd just print the single char that ptr is pointing to
            break;
    }
}
 
int main()
{
    int nValue{ 5 };
    float fValue{ 7.5f };
    char szValue[]{ "Mollie" };
 
    printValue(&nValue, Type::INT);
    printValue(&fValue, Type::FLOAT);
    printValue(szValue, Type::CSTRING);
 
    return 0;
}
``` 

## read matrix 2d from file .txt in the one vector
________________________________________
```ruby
#include<iostream>
#include"Header.h"
#define size_matrix 200                                                         //size of matrix clom and row
#define address "matrix-SF-DAG1src-13.txt"
using namespace std;

int main() {
    matrix = matrix_vector(size_matrix, szValue);
    return 0;
}
```
### Header.h
```ruby
#include<iostream>                                                              //for cout
#include<vector>                                                                //for vector
#include <fstream>
#include <string>
typedef std::vector<int> vector_1d_int;                                         //define type of vector integer one dimensional
typedef std::vector<vector_1d_int> vector_2d_int;                               //define type of vector integer two dimensional



vector_2d_int matrix_vector(int size_matrix, void* ptr) {

    vector_2d_int matrix_2d;                                                    //create vector integer two dimensional(matrix_2d)
    std::ifstream ifile(static_cast<char*>(ptr));                      //read address of file .txt
    if (ifile.is_open()) {                                                      //if file was available 
        vector_1d_int matrix_1d;                                                //create vector integer one dimensional(matrix_1d)
        int num;                                                                //create integer number(num)
        while (ifile >> num) {                                                  //Set the read number of the file to the defined integer(num)
            matrix_1d.push_back(num);                                           //set defined integer(num) into the One after the last cell vector integer one dimensional(matrix_1d)
            if (matrix_1d.size() == size_matrix) {                              //if size of vector is full
                matrix_2d.push_back(matrix_1d);                                 //set vector integer one dimensional(matrix_1d) into the One after the last cell vector integer tow dimensional(matrix_2d)
                matrix_1d.clear();                                              //clean all cels of vector integer one dimensional(matrix_1d) and delete it
            }
        }
    }
    else {                                                                      //else if file wasn't available
        std::cout << "There was an error opening the input file!\n";            //print "..."
        exit(1);                                                                //means program(process) terminate normally unsuccessfully..
    }

    return   matrix_2d;
    std::cout << matrix_2d[5][4] << std::endl;
    matrix_2d.clear();

}

```
## Calculate different operators on all the arrays of a pointer array
________________________________________
```ruby
#include<iostream>
#define size_matrix 200 

enum class Type
{
    S,
    M,
    C,
    D
};


double* calpoint(double* a, Type type, double b)
{
    double* c = new double[size_matrix] {0};

    switch (type)
    {
    case Type::S:
        for (int i = 0; i < size_matrix; i++) {
            c[i] = a[i] + b;
        }
        break;

    case Type::M:
        for (int i = 0; i < size_matrix; i++) {
            c[i] = a[i] - b;
        }
        break;

    case Type::C:
        for (int i = 0; i < size_matrix; i++) {
            c[i] = a[i] * b;
        }
        break;
    case Type::D:
        for (int i = 0; i < size_matrix; i++) {
            c[i] = a[i] / b;
        }
        break;
    }

    return   c;
}
double* calpoint(double* a, Type type, double* b)
{
    double* c = new double[size_matrix] {0};

    switch (type)
    {
    case Type::S:
        for (int i = 0; i < size_matrix; i++) {
            c[i] = a[i] + b[i];
        }
        break;

    case Type::M:
        for (int i = 0; i < size_matrix; i++) {
            c[i] = a[i] - b[i];
        }
        break;

    case Type::C:
        for (int i = 0; i < size_matrix; i++) {
            c[i] = a[i] * b[i];
        }
        break;
    case Type::D:
        for (int i = 0; i < size_matrix; i++) {
            c[i] = a[i] / b[i];
        }
        break;
    }

    return   c;
}


int main()
{
	double* a = new double[size_matrix] {0};
	double* b = new double[size_matrix] {0};//or double b=5;
	double* c = new double[size_matrix] {0};
	
	c = calpoint(a, Type::S, b);

	
    for (int i = 0; i < size_matrix; i++) {
        cout << c[i] << endl;
    }
}

``` 



__________________________________________
#  MATLAB

## read data 
________________________________________
```ruby
A = fscanf(fopen('Omega.txt','r'),'%f')
``` 
