# Library-management
#Keeps track of books issued in a library
class Library:
    def __init__(self,list,name):
        self.bookList=list
        self.name=name
        self.lendDict={}
    def displayBooks(self):
        print(f"We have following books in library: {self.name}")
        for books in self.bookList:
            print(books)

    def lendBook(self,user,book):
        if book not in self.lendDict.keys():
            self.lendDict.update({book:user})
            print("Lender-book database has been updated.You can take the book now")
        else:
            print(f"Book is already being used by {self.lendDict[book]}")

    def addBook(self,book):
        self.bookList.append(book)
        print("The book has been updated in the book list")


    def returnBook(self,book):
        self.lendDict.pop(book)

if __name__ == "__main__":
    harry=Library(['Python','Rich Dad and Poor Dad','Harry Potter','Beauty and Beast','C++ Basics'],
                 "Code with Harry")
    while(True):
        print(f"Welcome to the {harry.name} library.Enter your choice to continue: ")
        print("1. Display Books")
        print("2. Lend a Book")
        print("3. Add a Book")
        print("4. Return a Book")
        user_choice=input()
        if user_choice not in ['1','2','3','4']:
            print("Please enter a valid option: ")
            continue
        else:
            user_choice=int(user_choice)
        if user_choice==1:
            harry.displayBooks()
        elif user_choice==2:
            book=input("Enter the name of book you want to lend:")
            user=input("Enter your name: ")
            harry.lendBook(user,book)

        elif user_choice==3:
            book=input("Enter the name of book you want to add: ")
            harry.addBook(book)

        elif user_choice==4:
            book=input("Enter the name of book you want to return: ")
            harry.returnBook(book)
        else:
            print("Not a valid option")
        
        print("Press Q to Quit and C to continue: ")
        user_choice2=""
        while(user_choice2!="Q" and user_choice2!="C"):
            user_choice2=input()
            
            if user_choice2=="Q":
                exit()
            if user_choice2=="C":
                continue
