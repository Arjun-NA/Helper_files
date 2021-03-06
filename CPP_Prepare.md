### Vectors

``` 
#include <bits/stdc++.h>
using namespace std;
int main()
{
	vector<int> v = {1,2,3,4,5,6,7};
	v.push_back(8);
	v.push_back(9);
	v.push_back(10);
	v.push_back(11);
	cout<<v.size()<<endl;
	vector<int>::iterator ptr;
	for(ptr=v.begin();ptr<v.end();ptr++)
		cout<<*ptr<< " ";
	return 0;
}
```

### Sorting
```
#include <bits/stdc++.h
sort(arr, arr + n);
sort(v.begin(), v.end());    // for sorting the above vector
```
