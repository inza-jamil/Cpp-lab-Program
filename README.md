<img width="438" height="191" alt="Screenshot 2026-09-25 071408" src="https://github.com/user-attachments/assets/aa7342be-96ad-4125-b0c9-15027b070a83" /># Cpp-lab-Program

A collection of C++ programming lab tasks, practice programs, and projects developed during my learning journey. This repository includes programs based on basic programming concepts, problem-solving, loops, arrays, functions, and other C++ concepts.

---

##  Program 1: Hello World

###  Code
```cpp
#include <iostream>
using namespace std;

int main() {
    cout << "Hello, World!" << endl;
    cout << "Every expert was once a beginner." << endl;
    cout << "This is my first step into the world of C++." << endl;
    cout << "The journey of a thousand miles begins with a single line of code." << endl;
    return 0;
}
---

## Program 2: Sum of Squares (∑X²)

 ```cpp
#include <iostream>
using namespace std;

int main() {
    int start, stop;
    int sum = 0;

    cout << "Enter starting value: ";
    cin >> start;

    cout << "Enter stopping value: ";
    cin >> stop;

    for (int x = start; x <= stop; x++) {
        sum = sum + (x * x);
    }

    cout << "Sum of squares = " << sum << endl;
    return 0;
}

<img width="438" height="191" alt="output Program 01" src="https://github.com/user-attachments/assets/1b151a19-b07b-484d-ae2f-f9d09d243687" />

---

## Program 03 ArrayList with 8 Functions

```cpp
#include <iostream>
using namespace std;

const int CAPACITY = 20;

struct ArrayList {
    int data[CAPACITY];
    int size = 0;
};

// ==================== INSERT FUNCTIONS ====================

// 1. Insert at end
bool insertEnd(ArrayList &list, int value) {
    if (list.size >= CAPACITY) {
        return false;
    }
    list.data[list.size] = value;
    list.size++;
    return true;
}

// 2. Insert at start
bool insertStart(ArrayList &list, int value) {
    if (list.size >= CAPACITY) {
        return false;
    }
    for (int i = list.size; i > 0; i--) {
        list.data[i] = list.data[i-1];
    }
    list.data[0] = value;
    list.size++;
    return true;
}

// 3. Insert after specific value
bool insertAfter(ArrayList &list, int target, int value) {
    if (list.size >= CAPACITY) {
        return false;
    }
    int pos = -1;
    for (int i = 0; i < list.size; i++) {
        if (list.data[i] == target) {
            pos = i;
            break;
        }
    }
    if (pos == -1) {
        return false;
    }
    for (int i = list.size; i > pos + 1; i--) {
        list.data[i] = list.data[i-1];
    }
    list.data[pos + 1] = value;
    list.size++;
    return true;
}

// 4. Insert before specific value
bool insertBefore(ArrayList &list, int target, int value) {
    if (list.size >= CAPACITY) {
        return false;
    }
    int pos = -1;
    for (int i = 0; i < list.size; i++) {
        if (list.data[i] == target) {
            pos = i;
            break;
        }
    }
    if (pos == -1) {
        return false;
    }
    for (int i = list.size; i > pos; i--) {
        list.data[i] = list.data[i-1];
    }
    list.data[pos] = value;
    list.size++;
    return true;
}

// 5. Display the list
void displayList(const ArrayList &list) {
    cout << "List: ";
    for (int i = 0; i < list.size; i++) {
        cout << list.data[i] << " ";
    }
    cout << endl;
}

// ==================== DELETE FUNCTIONS ====================

// 6. Delete from end
bool deleteEnd(ArrayList &list) {
    if (list.size == 0) {
        return false;
    }
    list.size--;
    return true;
}

// 7. Delete from start
bool deleteStart(ArrayList &list) {
    if (list.size == 0) {
        return false;
    }
    for (int i = 0; i < list.size - 1; i++) {
        list.data[i] = list.data[i+1];
    }
    list.size--;
    return true;
}

// 8. Delete specific value
bool deleteValue(ArrayList &list, int value) {
    int pos = -1;
    for (int i = 0; i < list.size; i++) {
        if (list.data[i] == value) {
            pos = i;
            break;
        }
    }
    if (pos == -1) {
        return false;
    }
    for (int i = pos; i < list.size - 1; i++) {
        list.data[i] = list.data[i+1];
    }
    list.size--;
    return true;
}

// ==================== MAIN ====================

int main() {
    ArrayList list;

    // 1. Insert at end
    insertEnd(list, 10);
    insertEnd(list, 20);
    insertEnd(list, 30);
    cout << "After insertEnd(10, 20, 30): ";
    displayList(list);

    // 2. Insert at start
    insertStart(list, 5);
    cout << "After insertStart(5): ";
    displayList(list);

    // 3. Insert after specific value
    insertAfter(list, 20, 25);
    cout << "After insertAfter(20, 25): ";
    displayList(list);

    // 4. Insert before specific value
    insertBefore(list, 30, 28);
    cout << "After insertBefore(30, 28): ";
    displayList(list);

    // 6. Delete from end
    deleteEnd(list);
    cout << "After deleteEnd(): ";
    displayList(list);

    // 7. Delete from start
    deleteStart(list);
    cout << "After deleteStart(): ";
    displayList(list);

    // 8. Delete specific value
    deleteValue(list, 25);
    cout << "After deleteValue(25): ";
    displayList(list);

    return 0;
}

###OUTPUT

After insertEnd(10, 20, 30): List: 10 20 30
After insertStart(5): List: 5 10 20 30
After insertAfter(20, 25): List: 5 10 20 25 30
After insertBefore(30, 28): List: 5 10 20 25 28 30
After deleteEnd(): List: 5 10 20 25 28
After deleteStart(): List: 10 20 25 28
After deleteValue(25): List: 10 20 28

---

 ## PROGRAM 04

**Linear Search Using While Loop**

```cpp
#include <iostream>
using namespace std;

const int CAPACITY = 20;

struct ArrayList {
    int data[CAPACITY];
    int size = 0;
};

// ==================== INSERT FUNCTIONS ====================

// 1. Insert at end
bool insertEnd(ArrayList &list, int value) {
    if (list.size >= CAPACITY) {
        return false;
    }
    list.data[list.size] = value;
    list.size++;
    return true;
}

// 2. Insert at start
bool insertStart(ArrayList &list, int value) {
    if (list.size >= CAPACITY) {
        return false;
    }
    for (int i = list.size; i > 0; i--) {
        list.data[i] = list.data[i-1];
    }
    list.data[0] = value;
    list.size++;
    return true;
}

// 3. Insert after specific value
bool insertAfter(ArrayList &list, int target, int value) {
    if (list.size >= CAPACITY) {
        return false;
    }
    int pos = -1;
    for (int i = 0; i < list.size; i++) {
        if (list.data[i] == target) {
            pos = i;
            break;
        }
    }
    if (pos == -1) {
        return false;
    }
    for (int i = list.size; i > pos + 1; i--) {
        list.data[i] = list.data[i-1];
    }
    list.data[pos + 1] = value;
    list.size++;
    return true;
}

// 4. Insert before specific value
bool insertBefore(ArrayList &list, int target, int value) {
    if (list.size >= CAPACITY) {
        return false;
    }
    int pos = -1;
    for (int i = 0; i < list.size; i++) {
        if (list.data[i] == target) {
            pos = i;
            break;
        }
    }
    if (pos == -1) {
        return false;
    }
    for (int i = list.size; i > pos; i--) {
        list.data[i] = list.data[i-1];
    }
    list.data[pos] = value;
    list.size++;
    return true;
}

// 5. Display the list
void displayList(const ArrayList &list) {
    cout << "List: ";
    for (int i = 0; i < list.size; i++) {
        cout << list.data[i] << " ";
    }
    cout << endl;
}

// ==================== DELETE FUNCTIONS ====================

// 6. Delete from end
bool deleteEnd(ArrayList &list) {
    if (list.size == 0) {
        return false;
    }
    list.size--;
    return true;
}

// 7. Delete from start
bool deleteStart(ArrayList &list) {
    if (list.size == 0) {
        return false;
    }
    for (int i = 0; i < list.size - 1; i++) {
        list.data[i] = list.data[i+1];
    }
    list.size--;
    return true;
}

// 8. Delete specific value
bool deleteValue(ArrayList &list, int value) {
    int pos = -1;
    for (int i = 0; i < list.size; i++) {
        if (list.data[i] == value) {
            pos = i;
            break;
        }
    }
    if (pos == -1) {
        return false;
    }
    for (int i = pos; i < list.size - 1; i++) {
        list.data[i] = list.data[i+1];
    }
    list.size--;
    return true;
}

// ==================== LAB TASK 3: LINEAR SEARCH ====================

int linearSearch(ArrayList &list, int target) {
    int i = 0;
    while (i < list.size) {
        if (list.data[i] == target) {
            return i;    
        }
        i++;
    }
    return -1;    
}

// ==================== MAIN ====================

int main() {
    ArrayList list;

  
    insertEnd(list, 10);
    insertEnd(list, 20);
    insertEnd(list, 30);
    insertEnd(list, 40);
    insertEnd(list, 50);

    cout << "=== ArrayList ===" << endl;
    displayList(list);

    // Lab Task 3: Linear Search
    cout << "\n=== Linear Search ===" << endl;

    int target;
    cout << "Enter value to search: ";
    cin >> target;

    int pos = linearSearch(list, target);

    if (pos != -1) {
        cout << "Value " << target << " found at position " << pos << endl;
    } else {
        cout << "Value " << target << " not found" << endl;
    }

    return 0;
}

###Output

=== ArrayList ===
List: 10 20 30 40 50

=== Linear Search ===
Enter value to search: 30
Value 30 found at position 2

---

# Lab 02

## Singly Linked List
This lab teaches you the following topics:
• Creation of singly linked list
• Insertion in singly linked list
• Deletion from singly linked list
• Traversal of all nodes
Useful Concepts
A list is a finite ordered set of elements of a certain type. The elements of the list are called cells or nodes.
A list can be represented statically, using arrays or, more often, dynamically, by allocating and releasing 
memory as needed. In the case of static lists, the ordering is given implicitly by the one-dimension
array. In the case of dynamic lists, the order of nodes is set by pointers. In this case, the cells are
allocated dynamically in the heap of the program. Dynamic lists are typically called linked lists, and they
can be singly- or doubly-linked.
The structure of a node may be:
struct Nodetype
{
 int data; /* an optional f i e l d */
. . . /* other useful data fi e l ds */
 Nodetype *next=NULL; /* link to next node, assigned NULL so that should not point garbage*/
};
Nodetype *first=NULL, *last=NULL; /* first and last pointers are global and point first and last node */

## Lab Task 1: Display Linked List in Reverse (Loop + Recursion)

```cpp
#include <iostream>
using namespace std;

// Node structure - each node has data and a pointer to next node
struct Node {
    int data;       // Stores the value
    Node* next;     // Points to the next node in the list
};

// Global head pointer - points to the first node of the list
Node* head = NULL;

// ==================== INSERT FUNCTION ====================

// Insert a new node at the end of the linked list
void insertEnd(int value) {
    Node* newNode = new Node;      // Create a new node in memory
    newNode->data = value;         // Store the value in the new node
    newNode->next = NULL;          // New node's next is NULL (it's the last node)

    // If the list is empty, make the new node the head
    if (head == NULL) {
        head = newNode;
        return;
    }

    // Otherwise, traverse to the last node
    Node* temp = head;
    while (temp->next != NULL) {   // Keep moving until we reach the last node
        temp = temp->next;
    }
    temp->next = newNode;          // Link the last node to the new node
}

// ==================== NORMAL DISPLAY ====================

// Display the linked list in normal (forward) order
void display(Node* h) {
    Node* temp = h;                // Start from the head
    while (temp != NULL) {         // Loop until we reach the end
        cout << temp->data << " -> ";   // Print current node's data
        temp = temp->next;         // Move to the next node
    }
    cout << "NULL" << endl;        // End of list
}

// ==================== LAB TASK 1: REVERSE USING LOOP ====================

// Display the linked list in reverse order using a loop
// Logic: Store all values in an array, then print the array backwards
void displayReverseLoop() {
    int arr[100];                  // Array to store all values
    int count = 0;                 // Counter to track number of elements

    Node* temp = head;             // Start from head
    while (temp != NULL) {         // Traverse the entire list
        arr[count] = temp->data;   // Store each value in the array
        count++;                   // Increment counter
        temp = temp->next;         // Move to next node
    }

    cout << "Reverse (Loop): ";
    // Print the array from the last index to the first
    for (int i = count - 1; i >= 0; i--) {
        cout << arr[i] << " -> ";
    }
    cout << "NULL" << endl;
}

// ==================== LAB TASK 1: REVERSE USING RECURSION ====================

// Display the linked list in reverse order using recursion
// Logic: Go to the end of the list first, then print while coming back
void displayReverseRecursion(Node* temp) {
    // Base case: if we reach the end of the list, stop
    if (temp == NULL) {
        return;
    }

    // Recursive call: go to the next node first
    displayReverseRecursion(temp->next);

    // Print the current node's data AFTER the recursive call returns
    // This prints in reverse order
    cout << temp->data << " -> ";
}

// ==================== MAIN FUNCTION ====================

int main() {
    // Insert values into the linked list
    insertEnd(10);
    insertEnd(20);
    insertEnd(30);
    insertEnd(40);

    // Display the list in normal order
    cout << "Original List: ";
    display(head);

    // Display in reverse using loop
    displayReverseLoop();

    // Display in reverse using recursion
    cout << "Reverse (Recursion): ";
    displayReverseRecursion(head);
    cout << "NULL" << endl;

    return 0;
}

<img width="598" height="217" alt="Screenshot 2026-09-26 095759" src="https://github.com/user-attachments/assets/47612f2c-636d-49ac-ab4d-5f391514c9e3" />

---

# Lab Task 2: Merge Two Linked Lists

```cpp
#include <iostream>
using namespace std;

// Node structure
struct Node {
    int data;       // Value
    Node* next;     // Pointer to next node
};

// ==================== INSERT FUNCTION ====================

// Insert at end (takes head by reference so we can modify it)
void insertEnd(Node* &head, int value) {
    Node* newNode = new Node;
    newNode->data = value;
    newNode->next = NULL;

    if (head == NULL) {
        head = newNode;
        return;
    }

    Node* temp = head;
    while (temp->next != NULL) {
        temp = temp->next;
    }
    temp->next = newNode;
}

// ==================== DISPLAY FUNCTION ====================

void display(Node* h) {
    Node* temp = h;
    while (temp != NULL) {
        cout << temp->data << " -> ";
        temp = temp->next;
    }
    cout << "NULL" << endl;
}

// ==================== LAB TASK 2: MERGE LISTS ====================

// Merge two linked lists into a new third linked list
// Takes two heads as parameters, returns the head of the new merged list
Node* mergeLists(Node* list1, Node* list2) {
    Node* newHead = NULL;      // Head of the new merged list
    Node* newTail = NULL;      // Tail of the new merged list

    // ---------- Copy all nodes from list1 ----------
    Node* temp = list1;
    while (temp != NULL) {
        Node* newNode = new Node;       // Create a new node
        newNode->data = temp->data;     // Copy the value
        newNode->next = NULL;

        // If new list is empty, make this the head
        if (newHead == NULL) {
            newHead = newNode;
            newTail = newNode;
        } else {
            // Otherwise, add to the end
            newTail->next = newNode;
            newTail = newNode;
        }
        temp = temp->next;              // Move to next node in list1
    }

    // ---------- Copy all nodes from list2 ----------
    temp = list2;
    while (temp != NULL) {
        Node* newNode = new Node;
        newNode->data = temp->data;
        newNode->next = NULL;

        if (newHead == NULL) {
            newHead = newNode;
            newTail = newNode;
        } else {
            newTail->next = newNode;
            newTail = newNode;
        }
        temp = temp->next;
    }

    return newHead;    // Return the head of the new merged list
}

// ==================== MAIN FUNCTION ====================

int main() {
    Node* list1 = NULL;
    Node* list2 = NULL;

    // Create first list: 1 -> 3 -> 5
    insertEnd(list1, 1);
    insertEnd(list1, 3);
    insertEnd(list1, 5);

    // Create second list: 2 -> 4 -> 6
    insertEnd(list2, 2);
    insertEnd(list2, 4);
    insertEnd(list2, 6);

    cout << "List 1: ";
    display(list1);

    cout << "List 2: ";
    display(list2);

    // Merge both lists
    Node* merged = mergeLists(list1, list2);

    cout << "Merged List: ";
    display(merged);

    return 0;
}

<img width="516" height="196" alt="Screenshot 2026-09-26 095931" src="https://github.com/user-attachments/assets/d4f3e486-1e7b-40bd-89ad-f90f4bfdbd06" />

---

# Lab Task 3: Find Multiple Occurrences

```cpp
#include <iostream>
using namespace std;

// Node structure
struct Node {
    int data;
    Node* next;
};

// Global head pointer
Node* head = NULL;

// ==================== INSERT FUNCTION ====================

void insertEnd(int value) {
    Node* newNode = new Node;
    newNode->data = value;
    newNode->next = NULL;

    if (head == NULL) {
        head = newNode;
        return;
    }

    Node* temp = head;
    while (temp->next != NULL) {
        temp = temp->next;
    }
    temp->next = newNode;
}

// ==================== DISPLAY FUNCTION ====================

void display(Node* h) {
    Node* temp = h;
    while (temp != NULL) {
        cout << temp->data << " -> ";
        temp = temp->next;
    }
    cout << "NULL" << endl;
}

// ==================== LAB TASK 3: FIND OCCURRENCES ====================

// Find all positions where a specific value appears in the list
void findOccurrences(Node* head, int value) {
    Node* temp = head;         // Start from head
    int position = 0;          // Track current position (0-based)
    int count = 0;             // Count total occurrences
    bool found = false;        // Flag to check if value was found

    cout << "Value " << value << " found at positions: ";

    // Traverse the entire list
    while (temp != NULL) {
        // Check if current node's data matches the target value
        if (temp->data == value) {
            cout << position << " ";    // Print the position
            count++;                    // Increment occurrence count
            found = true;               // Mark as found
        }
        position++;             // Move to next position
        temp = temp->next;      // Move to next node
    }

    // If value was never found
    if (!found) {
        cout << "Not found";
    } else {
        cout << "\nTotal occurrences: " << count;
    }
    cout << endl;
}

// ==================== MAIN FUNCTION ====================

int main() {
    // Create list: 10 -> 20 -> 10 -> 30 -> 10 -> 40
    insertEnd(10);
    insertEnd(20);
    insertEnd(10);
    insertEnd(30);
    insertEnd(10);
    insertEnd(40);

    cout << "List: ";
    display(head);

    // Find occurrences of different values
    findOccurrences(head, 10);
    findOccurrences(head, 20);
    findOccurrences(head, 99);

    return 0;
}

<img width="544" height="286" alt="Screenshot 2026-09-26 100106" src="https://github.com/user-attachments/assets/740fc58c-2501-4acb-b833-0fa2c076daad" />

---

### Lab Task 1: Reverse Linked List (Loop + Recursion)

 *Important Points*
Singly Linked List is a data structure where each node points to the next node only in one direction.
Reverse display means printing the list from last node to first node.
Two approaches are used for reverse display: Loop and Recursion.
Loop approach uses an array to store all values first, then prints the array backwards.
Why array in loop? Because a singly linked list can only be traversed in one direction (head to tail). To print in reverse, we must store values first.
Recursion approach uses the call stack to achieve reverse printing.
How recursion works: The function calls itself to go to the end of the list first, then prints values while returning back.
Base case in recursion: When temp == NULL, the function returns (stops).
displayReverseRecursion(temp->next) is called first, then cout << temp->data is executed
Both approaches produce the same output but use different techniques.
Time Complexity: O(n) for both approaches.
Space Complexity: O(n) for both (array in loop, call stack in recursion).

## Lab Task 2: Merge Two Linked Lists**

 *Important Points*
Merge means combining two linked lists into a third new linked list.

Original lists are not modified. Only copies of their nodes are made.

The function takes two parameters (two heads) and returns the head of the new merged list.

newHead points to the first node of the new list.

newTail points to the last node of the new list. It helps in adding new nodes in O(1) time without traversing from the beginning.

Two separate loops are used: one for list1 and one for list2.

First loop copies all nodes from list1 into the new list.

Second loop copies all nodes from list2 into the new list.

Copying a node means creating a new node with the same data value.

Why copy instead of linking? Because the assignment requires a third new linked list, and the original lists must remain intact.

Condition if (newHead == NULL) checks if the new list is empty (first node).

If new list is empty: The new node becomes both head and tail.

If new list is not empty: The new node is added after the tail, and tail is updated.

Time Complexity: O(n + m), where n and m are the sizes of the two lists.

Space Complexity: O(n + m) for the new list.

## Lab Task 3: Find Multiple Occurrences**

*Important Points*
Multiple occurrences means finding all positions where a specific value appears in the list.

The function takes two parameters: the head of the list and the value to search.

position variable tracks the current index (0-based indexing).

count variable counts the total number of occurrences.

found is a boolean flag that indicates whether the value was found at least once.

0-based indexing means the first node is at position 0.

The function traverses the entire list from head to NULL.

At each node, it checks if (temp->data == value).

If match found: Prints the position, increments count, sets found to true.

position++ is done for every node, whether it matches or not.

temp = temp->next moves to the next node.

After traversal: If found is false, prints "Not found".

If found: Prints total occurrences count.

Multiple positions are printed separated by spaces.

Time Complexity: O(n), where n is the number of nodes.

Space Complexity: O(1), because no extra data structure is used.

# Assignment 01 — ArrayList, Pointer Traversal & Problem Solving

### Problem Statement

A short description of what the assignment is about.

## Parts Overview

| Part     |     Description   
| Part A   | Create and Populate the ArrayList 
| Part B   | Pointer Traversal, Sum, Minimum and Maximum 
| Part C   | Find the Median 
| Part D   | Two Averages and Closest Value 
| Part E   | Final Calculations and ArrayList Modification

##CODE

```cpp
#include <iostream>
using namespace std;

// ==================== GLOBAL CONSTANTS ====================

// Maximum capacity of the ArrayList (fixed, cannot be changed)
const int CAPACITY = 20;

// ==================== ARRAYLIST STRUCTURE ====================

// ArrayList structure with fixed array and logical size
struct ArrayList {
    int data[CAPACITY];    // Fixed array of 20 integers
    int size = 0;          // Logical size (how many elements are actually stored)
};

// Global ArrayList object
ArrayList list;

// Pointer used to traverse the ArrayList (starts at first element)
int *ptr = list.data;

// ==================== GLOBAL VARIABLES FOR CALCULATIONS ====================

int minimum;              // Stores the smallest value
int maximum;              // Stores the largest value
int median;               // Stores the middle value
int closestValue;         // Stores the value closest to special average
int closestPosition;      // Stores the position of closest value
int sum = 0;              // Stores the sum of all elements

double generalAverage;    // Sum / size
double specialAverage;    // (min + median + max) / 3
double averageDifference; // |general - special|
double finalScore;        // Final calculated score

// ==================== FUNCTIONS ====================

// Insert a value at the end of the ArrayList
bool insertEnd(ArrayList &list, int value) {
    // Check if list is full
    if (list.size >= CAPACITY) {
        return false;      // Cannot insert, list is full
    }
    list.data[list.size] = value;   // Place value at next available position
    list.size++;                    // Increment logical size
    return true;                    // Insertion successful
}

// Insert a value at the beginning of the ArrayList
bool insertAtBeginning(ArrayList &list, int value) {
    // Check if list is full
    if (list.size >= CAPACITY) {
        return false;
    }
    // Shift all elements one position to the right (from end to start)
    for (int i = list.size; i > 0; i--) {
        list.data[i] = list.data[i-1];
    }
    list.data[0] = value;   // Place value at first position
    list.size++;            // Increment logical size
    return true;
}

// Delete a value at a specific position
bool deleteAtPosition(ArrayList &list, int position) {
    // Check if position is valid
    if (position < 0 || position >= list.size) {
        return false;
    }
    // Shift all elements after position one step to the left
    for (int i = position; i < list.size - 1; i++) {
        list.data[i] = list.data[i+1];
    }
    list.size--;            // Decrement logical size
    return true;
}

// Display all logical elements of the ArrayList
void displayList(const ArrayList &list) {
    for (int i = 0; i < list.size; i++) {
        cout << list.data[i] << " ";
    }
    cout << endl;
}

// ==================== MAIN FUNCTION ====================

int main() {

    // ==================== PART A: Create and Populate ====================
    // Insert 9 values using insertEnd()
    insertEnd(list, 18);
    insertEnd(list, 7);
    insertEnd(list, 45);
    insertEnd(list, 11);
    insertEnd(list, 36);
    insertEnd(list, 31);   // Reg No (last two digits of FA25-BCS-031)
    insertEnd(list, 21);
    insertEnd(list, 13);
    insertEnd(list, 29);

    cout << "Initial ArrayList: ";
    displayList(list);

    // ==================== PART B: Pointer Traversal, Sum, Min, Max ====================
    ptr = list.data;        // Reset pointer to first element
    sum = 0;
    minimum = *ptr;         // Assume first element is minimum
    maximum = *ptr;         // Assume first element is maximum

    // Single traversal: calculate sum, min, max together
    for (int i = 0; i < list.size; i++) {
        sum += *ptr;                          // Add current value to sum
        if (*ptr < minimum) minimum = *ptr;   // Update minimum if smaller
        if (*ptr > maximum) maximum = *ptr;   // Update maximum if larger
        ptr++;                                // Move to next element
    }

    cout << "Minimum Value: " << minimum << endl;
    cout << "Maximum Value: " << maximum << endl;
    cout << "Sum: " << sum << endl;

    // ==================== PART C: Median with Temp Array ====================
    // Create a temporary array (original list must not be rearranged)
    int temp[CAPACITY];

    // Copy logical elements into temp array
    for (int i = 0; i < list.size; i++) {
        temp[i] = list.data[i];
    }

    // Bubble Sort (manual, STL not allowed)
    for (int i = 0; i < list.size - 1; i++) {
        for (int j = 0; j < list.size - i - 1; j++) {
            if (temp[j] > temp[j+1]) {
                int t = temp[j];
                temp[j] = temp[j+1];
                temp[j+1] = t;
            }
        }
    }

    // Median is the middle element (size = 9, so index 4)
    median = temp[list.size / 2];
    cout << "Median Value: " << median << endl;

    // ==================== PART D: Two Averages and Closest Value ====================
    // General Average = Sum / size
    generalAverage = (double)sum / list.size;

    // Special Average = (Min + Median + Max) / 3
    specialAverage = (double)(minimum + median + maximum) / 3;

    ptr = list.data;              // Reset pointer
    double minDistance = 999999;  // Large initial value
    closestPosition = 0;

    // Traverse to find closest value to specialAverage
    for (int i = 0; i < list.size; i++) {
        double distance = *ptr - specialAverage;
        if (distance < 0) distance = -distance;   // Absolute value

        // If this distance is smaller, update closest
        if (distance < minDistance) {
            minDistance = distance;
            closestValue = *ptr;
            closestPosition = i;
        }
        ptr++;                    // Move to next element
    }

    cout << "General Average: " << generalAverage << endl;
    cout << "Special Average: " << specialAverage << endl;
    cout << "Closest Value: " << closestValue << endl;
    cout << "Position of Closest Value: " << closestPosition << endl;

    // ==================== PART E: Final Calculations and Modification ====================
    // Average Difference = |General - Special|
    averageDifference = generalAverage - specialAverage;
    if (averageDifference < 0) averageDifference = -averageDifference;

    // Final Score = |Closest - General| + |Closest - Special| + Average Difference
    double d1 = closestValue - generalAverage;
    if (d1 < 0) d1 = -d1;

    double d2 = closestValue - specialAverage;
    if (d2 < 0) d2 = -d2;

    finalScore = d1 + d2 + averageDifference;

    cout << "Difference Between Averages: " << averageDifference << endl;
    cout << "Final Score: " << finalScore << endl;

    // Delete the closest value from the list
    deleteAtPosition(list, closestPosition);
    cout << "ArrayList After Deletion: ";
    displayList(list);

    // Round specialAverage to nearest integer and insert at beginning
    int roundedSpecial = (int)(specialAverage + 0.5);
    insertAtBeginning(list, roundedSpecial);
    cout << "Final ArrayList After Insertion: ";
    displayList(list);

    return 0;
}

<img width="962" height="592" alt="Screenshot 2026-09-26 101216" src="https://github.com/user-attachments/assets/90117215-a485-4e2a-a459-214151e41fec" />

---

## 👩‍💻 Author

**Inza Bibi**
Registration No: FA25-BCS-031
