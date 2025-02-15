This C++ program implements an inventory management system with a shop feature, allowing users to add, remove, search, and manage items. It includes object-oriented programming (OOP) principles like inheritance, polymorphism, and dynamic memory management. Below is a breakdown of how it works:
1. Classes and Their Roles
 Item (Base Class)

    Represents a generic item with:
        A name
        A unique ID
        A price
    Has a pure virtual function use(), making it an abstract class (cannot be instantiated directly).
    Provides getters for the name, ID, and price.

 Consumable (Derived Class)

    Inherits from Item and represents one-time-use items.
    Implements use(), which prints that the item is being used.

 Unique (Derived Class)

    Represents non-consumable, single-instance items.
    Implements use() with a custom message.

 Stackable (Derived Class)

    Represents items that can be stored in quantities.
    Includes an extra attribute: quantity.
    Overrides use() to decrement the quantity and remove the item when it reaches zero.

2. Inventory Management
 Inventory Class

    Stores a collection of Item* (pointers to base class items).
    Functions:
        addItem(Item* item): Adds an item to the inventory.
        removeItem(int id): Deletes an item by its ID.
        sortItems(): Sorts items based on their IDs.
        searchItemById(int id): Finds an item by ID.
        searchItemByName(string name): Finds an item by name.
        displayItems(): Prints all items in the inventory.

⚠ Memory Management:
The destructor ~Inventory() ensures that dynamically allocated items are deleted when the inventory is destroyed.
3. Shop System
 Shop Class (Derived from Inventory)

    Acts as a marketplace where players can buy and sell items.
    Functions:
        buyItem(Inventory& inventory, int itemId): Moves an item from the shop to the player's inventory.
        sellItem(Inventory& inventory, int itemId): Moves an item from the player's inventory to the shop.

4. User Interaction - Menu System
 Menu Class

    Provides a text-based user interface.
    Displays a menu with various options and processes user input.
    Handles:
     Adding items
     Using (consuming) items
     Sorting inventory
     Searching for items (by ID or name)
     Discarding items
     Buying/selling items

Each function prompts the user for input and performs the appropriate action.
5. Main Function - Program Execution

int main() {
    Inventory inventory;
    Shop shop;
    Menu menu(inventory, shop);

    menu.displayMenu(); // Show menu
    int choice;
    cin >> choice;
    menu.processChoice(choice); // Process user input

    return 0;
}

    Creates an Inventory and a Shop.
    Displays the menu and waits for user input.
    Processes the user’s choice recursively until they exit.

 Key Features & Concepts Used

 Object-Oriented Programming (OOP) – Uses inheritance, polymorphism, and encapsulation.
 Dynamic Memory Management – Uses new and delete to allocate and free memory.
 Lambdas & Sorting – Uses std::sort() with a lambda function for sorting items by ID.
 User Input Handling – Uses cin to receive user input and process actions.
 Flexibility & Scalability – The program can be extended with more item types or features easily.
 
 Example Run

------ Menu ------
1. Add item to inventory
2. Consume item
3. Order inventory
4. Search item by ID
5. Search item by name
6. Discard item
7. Buy item
8. Sell item
9. Display inventory
0. Exit

    If the user chooses 1 (Add item to inventory):

    Enter item name: Potion
    Enter item ID: 101
    Enter item price: 5.99
    Select item type:
    1. Consumable
    2. Unique
    3. Stackable

    If the user chooses 2 (Consume item) and selects a stackable item, its quantity decreases.
    If an item reaches quantity = 0, it is removed from the inventory.

 Final Thoughts

This code simulates a basic inventory system that can be used in games or e-commerce applications. It provides an interactive way to add, search, buy, and sell items while demonstrating solid OOP principles. 🚀
