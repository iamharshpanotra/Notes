🔷 What is an Array?
An array in C++ is a data structure that holds a fixed-size sequential collection of elements of the same data type. Arrays are used when you want to store multiple values of the same type together under a single variable name and access them using an index.

🔷 Why Use Arrays?
Without arrays, you would have to declare individual variables for each value, like this:
int mark1, mark2, mark3, mark4, mark5;
Using an array:
int marks[5]; // Stores 5 integers in one go
Arrays make your code cleaner, shorter, and more efficient, especially when working with loops and large datasets.

🔷 Declaring and Initializing Arrays
✅ Declaration Syntax
datatype arrayName[size];
✅ Example:
int numbers[5];
This creates an array that can store 5 integers.
✅ Initialization:
int numbers[5] = {10, 20, 30, 40, 50};
Or:
int numbers[] = {10, 20, 30}; // Size is inferred as 3
You can also assign values later:
numbers[0] = 10;
numbers[1] = 20;

🔷 Accessing Array Elements
Array elements are accessed using zero-based indexing.
cout << numbers[0]; // Outputs 10
cout << numbers[1]; // Outputs 20
You can also use loops for easier processing:
for (int i = 0; i < 5; i++) {
    cout << numbers[i] << " ";
}

🔷 Memory Representation
Arrays in C++ are stored in contiguous memory locations. For example, for an int numbers[3], the memory layout may look like this:
Index	Address	Value
0	0x100	10
1	0x104	20
2	0x108	30
Each int occupies 4 bytes (may vary depending on system).
This allows constant time access: numbers[i] = Base address + (i * size_of_element)

🔷 Types of Arrays
1. Single-Dimensional Array
int arr[5] = {1, 2, 3, 4, 5};
A simple list of values.
2. Multidimensional Array
Used to store tables or matrices.
int matrix[2][3] = {
    {1, 2, 3},
    {4, 5, 6}
};
Accessing: matrix[1][2] → 6
3. Character Array (Strings)
char name[6] = {'H', 'e', 'l', 'l', 'o', '\0'};
Or simply:
char name[] = "Hello";
C++ treats this as a C-style string.

🔷 Limitations of Arrays
    • Fixed Size: You must know the size at compile time.
    • No Built-in Bounds Checking: Accessing arr[10] in a size 5 array leads to undefined behavior.
    • Not Resizable: Unlike std::vector, arrays can't grow/shrink dynamically.

🔷 C++ Alternatives to Arrays
For more flexibility and safety, C++ offers alternatives:
🔹 std::vector
Dynamic array-like container from the Standard Template Library (STL):
#include <vector>
vector<int> nums = {1, 2, 3, 4};
nums.push_back(5); // Adds 5 to the end
🔹 std::array
Safer and more modern replacement for C-style arrays (since C++11):
#include <array>
array<int, 5> nums = {1, 2, 3, 4, 5};

🔷 Real-Life Use Cases of Arrays
    • Storing scores, prices, names, sensor readings
    • Implementing data structures (stacks, queues, matrices)
    • Handling large datasets in games, simulations, or embedded systems

🔷 Example Program
#include <iostream>
using namespace std;
int main() {
    int marks[5];
cout << "Enter 5 marks:\n";
    for (int i = 0; i < 5; i++) {
        cin >> marks[i];
    }
cout << "You entered:\n";
    for (int i = 0; i < 5; i++) {
        cout << "Mark " << (i+1) << ": " << marks[i] << endl;
    }
return 0;
}
