Stacks are a type of container adaptor, specifically designed to operate in a LIFO context (last-in first-out), where elements are inserted and extracted only from one end of the container.

Elements are _pushed_/_popped_ from the _"back"_ of the specific container, which is known as the _top_ of the stack.

```
// header
#include <stack>

// declaration
stack<Type> nom_de_la_pile;

// add items
maPile.push(items);

// go to the top : Returns a reference to the most recent item.
cout << maPile.top();

// Remove top (pop) : Removes the element at the top (there is no value return)
maPile.pop();

// Check if empty
if (!maPile.empty()) {
    cout << maPile.top();
}

// size 
cout << maPile.size();
```