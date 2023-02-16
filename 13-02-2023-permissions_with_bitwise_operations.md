> NOTE: values can be wrong

looking on the sqlite3 source code I discover a new way to manage permissions on a software using the bitwise operators,
more precisely the left shift operation

let's say that - as common - in your application you have some categories of permissions, e.g: 

```
- admin
- employee
- user
```

for each category is attributed a value

```
- admin = 1
- employee = 2
- user = 3
```

for each category will exists sub-categories related with this principal category, like:

```
- admin
    - a1
    - a2
- employee
    - e1
    - e2
- user
    - u1
    - u2
```

until here nothing different, but how can be possible to assign the correct value of this sub-category without values
duplication for perssitency in a database, for instance?

for this it's possible to assign the correct value without duplication supposing that is reserved 64-bits to represent
the permission:

```
main category value | (sub-category code << quantity of bits reserved only for the main category)
```

suppossing that we need to calculate the correct value to represent the category `admin > a1`

```
1 | 1 << 8 (1 byte for the main category representation, that's the value max value of 256) = 257
```

now the sub-category `admin > a1` is equals the value 257 for representation

```
- admin
    - a1 = 257
    - a2
```

this method can represents `(2 ** (64 - 8)) / (2 ** 8)` sub-categories

- need to exclude the main categories representation (1 byte) from the total of bytes to all available space (8 bytes)
- need to divide the total by the numbers of principal categories

