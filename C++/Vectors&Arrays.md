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
