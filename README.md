# library_management_system
The Library Management System is a Python-based mini project designed to manage library operations through a simple menu-driven interface. It enables users to add, search, display, borrow, return, and delete books efficiently using Python dictionaries and functions. 

# Library Management System (Mini Project)

library = {}

def add_book():
    book_id = input("Enter Book ID: ")

    if book_id in library:
        print("Book ID already exists!")
        return

    title = input("Enter Book Title: ")
    author = input("Enter Author Name: ")

    library[book_id] = {
        "Title": title,
        "Author": author,
        "Status": "Available"
    }

    print("Book added successfully!\n")


def display_books():
    if not library:
        print("Library is empty!\n")
        return

    print("\n-------------------------------")
    print("Library Books")
    print("-------------------------------")

    for book_id, details in library.items():
        print(f"Book ID : {book_id}")
        print(f"Title   : {details['Title']}")
        print(f"Author  : {details['Author']}")
        print(f"Status  : {details['Status']}")
        print("-------------------------------")


def search_book():
    book_id = input("Enter Book ID to search: ")

    if book_id in library:
        details = library[book_id]
        print("\nBook Found")
        print(f"Title  : {details['Title']}")
        print(f"Author : {details['Author']}")
        print(f"Status : {details['Status']}")
    else:
        print("Book not found!")

    print()


def borrow_book():
    book_id = input("Enter Book ID to borrow: ")

    if book_id in library:
        if library[book_id]["Status"] == "Available":
            library[book_id]["Status"] = "Borrowed"
            print("Book borrowed successfully!")
        else:
            print("Book is already borrowed.")
    else:
        print("Book not found!")

    print()


def return_book():
    book_id = input("Enter Book ID to return: ")

    if book_id in library:
        if library[book_id]["Status"] == "Borrowed":
            library[book_id]["Status"] = "Available"
            print("Book returned successfully!")
        else:
            print("Book was not borrowed.")
    else:
        print("Book not found!")

    print()


def delete_book():
    book_id = input("Enter Book ID to delete: ")

    if book_id in library:
        del library[book_id]
        print("Book deleted successfully!")
    else:
        print("Book not found!")

    print()

while True:
    print("\n========== Library Management System ==========")
    print("1. Add Book")
    print("2. Display All Books")
    print("3. Search Book")
    print("4. Borrow Book")
    print("5. Return Book")
    print("6. Delete Book")
    print("7. Exit")

    choice = input("Enter your choice: ")

    if choice == "1":
        add_book()

    elif choice == "2":
        display_books()

    elif choice == "3":
        search_book()

    elif choice == "4":
        borrow_book()

    elif choice == "5":
        return_book()

    elif choice == "6":
        delete_book()

    elif choice == "7":
        print("Thank you for using Library Management System!")
        break

    else:
        print("Invalid choice! Please try again.")
