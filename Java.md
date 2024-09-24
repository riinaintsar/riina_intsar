# Examples of different Java projects 

## 1. Book managing application
### Using ArrayList. The user can add, remove and search for a book from list. 

### Main.java: 

```java
import java.util.Scanner;

public class Main { 

    public static BookManager bookManager = new BookManager();

    public static void main(String[] args) {
        
        Scanner scanner = new Scanner(System.in);
        while(true){
            System.out.println("Press 1 to add a book");
            System.out.println("Press 2 to show the list of books");
            System.out.println("Press 3 to remove a book");
            System.out.println("Press x to exit");
            var userInput = scanner.nextLine();
            if(userInput.equals("1")){
                addBook();
            }else if(userInput.equals("2")){
                getBooks();
            }else if(userInput.equals("3")){
                System.out.println("Enter the name of the book to be removed: ");
                var bookName = scanner.nextLine();
                removeBook(bookName);
            }else if(userInput.equalsIgnoreCase("x")){
                break;
            }else{
                System.out.println("Invalid input, please try again.");
            }
        }
        scanner.close();
    }

    public static void addBook(){
        Scanner scanner = new Scanner(System.in);
        System.out.println("Please enter the name of the book: ");
        var name = scanner.nextLine();
        System.out.println("Please enter the author of the book: ");
        var author = scanner.nextLine();

        var book = new Book(name, author);
        bookManager.addBook(book);
    }

    public static void getBooks(){
        var books = bookManager.getBooks();
        if (books.isEmpty()) {
            System.out.println("No books in the list.");
        } else {
            System.out.println("The books in the list are:");
            for(var book : books){
                System.out.println("Book Name: " + book.name + ", author: " + book.author);
            }
        }
    }

    public static void removeBook(String bookName){
        if (bookManager.removeBook(bookName)) {
            System.out.println("Book removed successfully.");
        } else {
            System.out.println("Book not found.");
        }
    }
}
```

### Book.java
```java
public class Book {
    private String name;
    private String author;

    public Book(String name, String author) {
        this.name = name;
        this.author = author;
    }

    public String getName() {
        return name;
    }

    public String getAuthor() {
        return author;
    }

    @Override
    public String toString() {
        return "Book{" +
                "name='" + name + '\'' +
                ", author='" + author + '\'' +
                '}';
    }
}
```

### BookManager.java: 
```java
import java.util.ArrayList;

public class BookManager {

    private ArrayList<Book> books = new ArrayList<>();

    // Add a book to the list
    public void addBook(Book book) {
        books.add(book);
    }

    // Remove a book by name
    public boolean removeBook(String name) {
        for (Book book : books) {
            if (book.getName().equalsIgnoreCase(name)) {
                books.remove(book);
                return true;
            }
        }
        return false;
    }

    // Search for a book by name or author
    public Book searchBook(String search) {
        for (Book book : books) {
            if (book.getName().equalsIgnoreCase(search) || book.getAuthor().equalsIgnoreCase(search)) {
                return book;
            }
        }
        return null;
    }

    // Get all books
    public ArrayList<Book> getBooks() {
        return books;
    }
}
```

## Tic-tac-toe game

```java
import java.util.Scanner;

class Main {
    public static void main(String[] args) {

        // Create game grid 3x3 with 2D array
        char[][] board = new char[3][3];

        // Initialize empty game board
        for (int i = 0; i < board.length; i++) {
            for (int j = 0; j < board[i].length; j++) {
                board[i][j] = ' ';
            }
        }

        // Create a scanner for user input
        char player = 'X';
        boolean gameOver = false;
        Scanner scanner = new Scanner(System.in);

        // While loop to keep the game running until the game is over
        while (!gameOver) {
            printBoard(board);
            System.out.print("Player " + player + ", enter your first move in row and then column (1 -> 2 -> 3): ");
            int i = scanner.nextInt() - 1;
            int j = scanner.nextInt() - 1;
            System.out.println();

            // If statement to check if the move is valid, if not, ask for a new move
            if (i >= 0 && i < 3 && j >= 0 && j < 3 && board[i][j] == ' ') {
                board[i][j] = player;
                if (haveWon(board, player)) {
                    printBoard(board);
                    System.out.println("Player " + player + " has won!");
                    gameOver = true;
                } else if (isBoardFull(board)) {
                    printBoard(board);
                    System.out.println("It's a tie!");
                    gameOver = true;
                } else {
                    player = (player == 'X') ? 'O' : 'X';
                }
            } else {
                System.out.println("Invalid move. Try again.");
            }
        }
    }

    // Method to check rows, columns, diagonals 
    public static boolean haveWon(char[][] board, char player) {
        // Rows
        for (int i = 0; i < board.length; i++) {
            if (board[i][0] == player && board[i][1] == player && board[i][2] == player) {
                return true;
            }
        }

        // Columns
        for (int j = 0; j < board[0].length; j++) {
            if (board[0][j] == player && board[1][j] == player && board[2][j] == player) {
                return true;
            }
        }

        // Diagonals
        if (board[0][0] == player && board[1][1] == player && board[2][2] == player) {
            return true;
        }

        if (board[0][2] == player && board[1][1] == player && board[2][0] == player) {
            return true;
        }
        return false;
    }

    // Method to check if the board is full
    public static boolean isBoardFull(char[][] board) {
        for (int i = 0; i < board.length; i++) {
            for (int j = 0; j < board[i].length; j++) {
                if (board[i][j] == ' ') {
                    return false;
                }
            }
        }
        return true;
    }

    // Method to print the game board
    public static void printBoard(char[][] board) {
        for (int i = 0; i < board.length; i++) {
            for (int j = 0; j < board[i].length; j++) {
                System.out.print(board[i][j]);
                if (j < board[i].length - 1) {
                    System.out.print(" | ");
                }
            }
            System.out.println();
            if (i < board.length - 1) {
                System.out.println("---------");
            }
        }
    }
}

```

![Kuvatõmmis 2024-09-24 114036](https://github.com/user-attachments/assets/484abdb1-bf99-4793-b1ea-059e554abe94)

