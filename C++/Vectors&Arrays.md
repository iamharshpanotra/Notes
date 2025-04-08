✅ What is a vector?
A vector is a dynamic array from the Standard Template Library (STL) in C++. It can automatically resize itself to accommodate more elements.
✅ What is an array?
An array is a fixed-size data structure that stores elements of the same type in contiguous memory. Its size must be known at compile-time.

🔄 Key Differences
Feature	                array	                vector (STL)
Size	                Fixed	                Dynamic (can grow/shrink)
Syntax	                int arr[5];	            std::vector<int> v;
Memory	Stack           (usually)	            Heap
Flexibility	            Low	                    High
Functions	        None (manual handling)	    Rich functions (push_back, size, etc.)
Bounds Checking	    No (arr[5] is unsafe)	    Yes (use v.at(5) safely)

💡 When to use what?
    • Use array when:
        ○ You know the size in advance.
        ○ Memory or performance is extremely critical.
    • Use vector when:
        ○ You don’t know the size in advance.
        ○ You need to add or remove elements during runtime.
        ○ You want built-in methods for convenience.

🛠 Example
Array:
int arr[3] = {10, 20, 30};
for (int i = 0; i < 3; i++) {
    std::cout << arr[i] << " ";
}
Vector:
#include <vector>
std::vector<int> v;
v.push_back(10);
v.push_back(20);
v.push_back(30);
for (int i = 0; i < v.size(); i++) {
    std::cout << v[i] << " ";
}

✨ Conclusion:
    A vector is like a dynamic array — it does the same basic job as an array but offers more power, flexibility, and safety. It's the modern C++ way to handle collections of data when size may change at runtime.


### 💾 **What is "Contiguous Memory"?**

**Contiguous memory** means all the elements are stored **next to each other in memory** — like rooms in a row in a hotel.

#### Example:
If you have this vector or array:
```cpp
int arr[3] = {10, 20, 30};
```

The memory might look like this:

| Address   | Value |
|-----------|--------|
| 0x1000    | 10     |
| 0x1004    | 20     |
| 0x1008    | 30     |

All values are stored **back-to-back** in memory. This helps with fast access using indexes (like `arr[2]`) because the computer knows where each item lives.

---

### 📦 **What is `std::vector<int> v`?**

This is how you declare a **vector of integers** in C++ using the Standard Template Library (STL):

```cpp
std::vector<int> v;
```

- `std::` means we’re using the **standard namespace**.
- `vector<int>` means we're making a **vector that stores integers**.
- `v` is the name of the vector (just like a variable).

You can add data like this:
```cpp
v.push_back(5);
v.push_back(10);
```

Now `v` contains `[5, 10]`.

---

### 🧠 **What is "Heap" Memory?**

In C++, memory is mainly divided into two types:

| Memory Area | Description |
|-------------|-------------|
| **Stack**   | Small, fast memory. Used for fixed-size variables (like regular arrays). Automatically managed. |
| **Heap**    | Large, dynamic memory. Used when size is not known at compile-time (like `vector`). Manually or automatically managed. |

#### ✅ `vector` uses heap memory:
When you write:
```cpp
std::vector<int> v;
```
C++ internally allocates memory **on the heap** so that it can **grow and shrink** as needed. You don’t need to manage it yourself — `vector` handles it!

---

### 🔁 Quick Recap:

- `Contiguous memory`: Elements are stored one after another.
- `std::vector<int> v`: A dynamic array (vector) of integers.
- Heap: Where `vector` stores its data (so it can grow).

---

Want a little visual diagram or animation to make this even clearer?