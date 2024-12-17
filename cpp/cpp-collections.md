## `array<T> <array>`

Array is a collection where the size of the collection is fixed.

```cpp
```

## `deque<T> <deque>`

Deque is a double-ended queue where data can be added to the front or the back of the queue.

```cpp
```

## `vector<T> <vector>`

Vector is similar to an array but a vector can grow and shrink as needed.

```cpp
```

## `list<T> <list>`

List is a double linked list.

```cpp
list<customer> customers;
typedef list<customer>::const_iterator LI;

customer dsi(1, "DSI");
customers.push_back(dsi);
customer amazon(2, "Amazon");
customers.push_back(amazon);
customer microsoft(3, "Microsoft");
customers.push_back(microsoft);

for(LI idx = customers.begin(); idx != customers.end(); ++idx) {
    customer cust = *idx;
    cout << cust.id << " | " << cust.name << endl;
}
```

## `forward_list <forward_list>`

```cpp
```

## `map <map>`

map<TK, TV> is a dictionary.

```cpp
map<int, customer> custMap;
customer dsi(1, "DSI");
customer amaz(2, "Amazon");
customer bbuy(3, "BestBuy");

custMap[dsi.id] = dsi;
custMap[amaz.id] = amaz;
custMap[bbuy.id] = bbuy;

for(auto idx = 1; idx <= 3; idx++) {
    auto cust = custMap[idx];
    cout << cust.id << " | " << cust.name << endl;
}
```