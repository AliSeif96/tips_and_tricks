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


