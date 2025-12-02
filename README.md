🛒 Shopping List App — README
* Overview 

This project implements a simple Shopping List console application using the custom ListInterface<T> provided in class. The goal of the assignment is not just to manage items in a list, but to demonstrate the importance of:
Programming to an interface
Using the List ADT as an abstraction
Hiding implementation details
Maintaining sorted data using a custom comparison

The app allows users to:
- Add items (automatically inserted in sorted order)
- View the current shopping list
- “Shop” the next item (remove the smallest/first item)
- Exit the program
- Each shopping item consists of an aisle and an item name, and items are always kept sorted by aisle and then alphabetically by name.

✔ Key Concepts Demonstrated
1. Programming to an Interface

Throughout the application, the list is declared using:
ListInterface<ShoppingItem> shoppingList;
Rather than using a concrete implementation such as ArrayBasedList or LinkedBasedList.
This means the program depends only on the behavior defined by the interface, not on the internal details of storage. Because of this design, switching implementations is as easy as changing ONE line:
shoppingList = new ArrayBasedList<>();
// OR
shoppingList = new LinkedBasedList<>();
Nothing else in the program needs to change.

Why this matters:
- Promotes flexibility and modularity
- Makes the program easier to maintain
- Allows replacing data structures without rewriting application logic
- Supports unit testing with multiple list implementations
This assignment clearly shows the power of decoupling the app logic from the underlying data structure.

2. Using the List ADT as an Abstraction

An Abstract Data Type (ADT) focuses on what operations are supported — not how they are implemented.

The List ADT in this project supports:
- add(index, item)
- get(index)
- remove(index)
- size()
- 
The ShoppingListApp relies ONLY on these methods. It does not care whether the list is backed by:
an array, a linked list, or something else entirely.

Because we rely strictly on the List ADT, the same methods correctly handle:
sorted insertion, retrieving items, removing the next item, and printing the list.
This abstraction frees the application from implementation concerns.

3. Sorted Insertion Using compareTo()

Items are always kept in sorted order based on the rules defined in ShoppingItem.compareTo():
- Aisle (ascending)
- Name (alphabetical) when aisles match

The insertSorted helper method scans through the list and uses:
item.compareTo(current) to determine where the new item should be inserted.

This demonstrates:
- how custom comparison logic controls structured ordering
- how sorted lists work in practice
- how the List ADT can be used to maintain order without direct array/linked list manipulation

4. Hiding Implementation Details

The assignment reinforces encapsulation and information hiding:
- The user interface doesn’t know or care how the list stores data.
- The ShoppingItem class encapsulates aisle/name fields and comparison logic.
- The application uses iteration (either index-based or iterator-based) without exposing node pointers or array indices.
- This matches real-world software design where data structures are hidden behind well-defined APIs.

🧪 Testing

The provided JUnit tests verify that:
- Sorted insertion works correctly
- The list remains ordered across both implementations
- shopNext() removes items in the proper order
- The application properly handles edge cases (empty list, etc.)
Both ArrayBasedList and LinkedBasedList must pass the same test suite, proving that the app truly depends on the interface, not the concrete implementation.

🚀 Conclusion

This assignment demonstrates the practical benefits of:
- Programming to an interface
- Relying on the List ADT instead of specific implementations
- Using abstraction to hide data structure details
- Maintaining sorted data with a clean comparison model

By completing this project, we see how flexible and powerful software becomes when implementation details are hidden and replaced with high-level abstractions.