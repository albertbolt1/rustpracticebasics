cpp knowledge acquired by learning rust 

```
#include <iostream>
using namespace std;

struct Counter {
    int value;

    void inc() {
        value++;
    }

    void print() {
        cout << value << endl;
    }
};


int main() {
    Counter a{10};
    Counter* p = &a;
    
    p->print();
    (*p).print();

    return 0;
}
```
when we do Counter* p =&a;
here p holds the address of a so when we do p->print() 
here p is the address so we should not be able to do p->print() but this translates to (*p).print() which is like accessing method in an object.

