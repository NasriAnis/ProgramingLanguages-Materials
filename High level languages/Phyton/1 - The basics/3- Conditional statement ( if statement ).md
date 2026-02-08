For conditional we use ==if statement== that executes a block of code if a condition is met.
![[t.78f3bacaa261 1.png]]
example :
```
>>> x = 3
>>> if x == 1:
...     print('foo')
...     print('bar')
...     print('baz')
... elif x == 2:
...     print('qux')
...     print('quux')
... else:
...     print('corge')
...     print('grault')
...
corge
grault
```

Another way to write if statement in one line :
```
<expr1> if <conditional_expr> else <expr2>
```

In if statement the conditional is tested one by one.