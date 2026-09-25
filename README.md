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
 Program 2: Sum of Squares (∑X²)
 Code
cpp
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

**Program 03 ArrayList with 8 Functions**
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

**Linear Search Using While Loop**
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
            return i;    // Value mil gayi, position return
        }
        i++;
    }
    return -1;    // Value nahi mili
}

// ==================== MAIN ====================

int main() {
    ArrayList list;

    // Lab Task 2 ke functions use karein
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
