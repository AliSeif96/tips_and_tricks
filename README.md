# tips_and_tricks


__________________________________________
#  C++

## calculate time run

__________________________________________
```ruby
  #include<iostream>
  
	clock_t t;
	t = clock();                                                                                //start
                                                                                                    //run
	cout<<"\nTime taken by program is :\t"<< ((double)clock() - t) / CLOCKS_PER_SEC << " sec\n";//stop
``` 
