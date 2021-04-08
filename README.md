# tips_and_tricks


__________________________________________
#  C++

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

