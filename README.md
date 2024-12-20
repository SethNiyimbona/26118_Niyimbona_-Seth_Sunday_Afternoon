
Java Exception Handling Examples
Objective
This project provides practical examples of handling exceptions in Java. Each example triggers a specific exception and demonstrates how to catch and handle it using try-catch blocks. Detailed explanations accompany each code snippet to enhance understanding.

Checked Exceptions
1. IOException
Scenario: Attempting to read from a non-existent file.

java
Copy code
import java.io.*;

public class IOExceptionExample {
    public static void main(String[] args) {
        try {
            FileReader reader = new FileReader("nonexistent_file.txt");
        } catch (IOException e) {
            System.out.println("IOException caught: " + e.getMessage());
        }
    }
}
Explanation: This exception occurs when input/output operations fail, such as trying to read a file that doesn't exist.

2. FileNotFoundException
Scenario: Trying to open a file that doesn't exist.

java
Copy code
import java.io.*;

public class FileNotFoundExceptionExample {
    public static void main(String[] args) {
        try {
            FileInputStream file = new FileInputStream("nonexistent_file.txt");
        } catch (FileNotFoundException e) {
            System.out.println("FileNotFoundException caught: " + e.getMessage());
        }
    }
}
Explanation: A subclass of IOException that specifically handles missing files.

3. EOFException
Scenario: Reading beyond the content of a file.

java
Copy code
import java.io.*;

public class EOFExceptionExample {
    public static void main(String[] args) {
        try (ObjectInputStream ois = new ObjectInputStream(new FileInputStream("data.txt"))) {
            while (true) {
                System.out.println(ois.readObject());
            }
        } catch (EOFException e) {
            System.out.println("EOFException caught: End of file reached.");
        } catch (IOException | ClassNotFoundException e) {
            System.out.println("Exception caught: " + e.getMessage());
        }
    }
}
Explanation: This exception is triggered when attempting to read past the end of a file.

4. SQLException
Scenario: Connecting to a non-existent database.

java
Copy code
import java.sql.*;

public class SQLExceptionExample {
    public static void main(String[] args) {
        try {
            Connection connection = DriverManager.getConnection("jdbc:mysql://localhost:3306/nonexistentdb", "user", "password");
        } catch (SQLException e) {
            System.out.println("SQLException caught: " + e.getMessage());
        }
    }
}
Explanation: This exception indicates issues during database access.

5. ClassNotFoundException
Scenario: Attempting to load a non-existent class.

java
Copy code
public class ClassNotFoundExceptionExample {
    public static void main(String[] args) {
        try {
            Class.forName("com.nonexistent.ClassName");
        } catch (ClassNotFoundException e) {
            System.out.println("ClassNotFoundException caught: " + e.getMessage());
        }
    }
}
Explanation: This occurs when the JVM cannot find the specified class.

Unchecked Exceptions
6. ArithmeticException
Scenario: Division by zero.

java
Copy code
public class ArithmeticExceptionExample {
    public static void main(String[] args) {
        try {
            int result = 10 / 0;
        } catch (ArithmeticException e) {
            System.out.println("ArithmeticException caught: " + e.getMessage());
        }
    }
}
Explanation: This exception is triggered by invalid arithmetic operations.

7. NullPointerException
Scenario: Accessing a null reference.

java
Copy code
public class NullPointerExceptionExample {
    public static void main(String[] args) {
        try {
            String str = null;
            System.out.println(str.length());
        } catch (NullPointerException e) {
            System.out.println("NullPointerException caught: " + e.getMessage());
        }
    }
}
Explanation: Accessing a method or field on a null object causes this exception.

8. ArrayIndexOutOfBoundsException
Scenario: Accessing an invalid array index.

java
Copy code
public class ArrayIndexOutOfBoundsExceptionExample {
    public static void main(String[] args) {
        try {
            int[] numbers = {1, 2, 3};
            System.out.println(numbers[5]);
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("ArrayIndexOutOfBoundsException caught: " + e.getMessage());
        }
    }
}
Explanation: Attempting to access an array index beyond its bounds triggers this exception.

9. ClassCastException
Scenario: Invalid type casting.

java
Copy code
public class ClassCastExceptionExample {
    public static void main(String[] args) {
        try {
            Object obj = new String("Test");
            Integer num = (Integer) obj;
        } catch (ClassCastException e) {
            System.out.println("ClassCastException caught: " + e.getMessage());
        }
    }
}
Explanation: Occurs when attempting an invalid cast.

10. IllegalArgumentException
Scenario: Passing invalid arguments to a method.

java
Copy code
public class IllegalArgumentExceptionExample {
    public static void main(String[] args) {
        try {
            Thread.sleep(-1000);
        } catch (IllegalArgumentException | InterruptedException e) {
            System.out.println("IllegalArgumentException caught: " + e.getMessage());
        }
    }
}
Explanation: This exception is thrown to indicate invalid arguments passed to a method.

11. NumberFormatException
Scenario: Converting an invalid string to a number.

java
Copy code
public class NumberFormatExceptionExample {
    public static void main(String[] args) {
        try {
            int num = Integer.parseInt("ABC");
        } catch (NumberFormatException e) {
            System.out.println("NumberFormatException caught: " + e.getMessage());
        }
    }
}
Explanation: Triggered when a string cannot be converted to a numeric type.
