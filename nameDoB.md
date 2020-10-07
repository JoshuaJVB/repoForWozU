```java
import java.util.Scanner;
import java.time.LocalDate;

class Main {
  public static void main(String[] args) {
    Scanner scan = new Scanner(System.in);

    System.out.println("Please enter your name: ");
    String name = scan.nextLine();

    System.out.println("Please enter your email: ");
    String email = scan.nextLine();

    System.out.println("Please enter year of birth(YYYY): ");
    int year = scan.nextInt();

    System.out.println("please enter month of birth(MM): ");
    int month = scan.nextInt();

    System.out.println("Please enter day of birth(DD): ");
    int day = scan.nextInt();

    LocalDate DoB = LocalDate.of(year, month, day);

    System.out.println("Name: " + name);
    System.out.println("email: " + email);
    System.out.println("Date of Birth: " + DoB);

    scan.close();
    
  }
}
```
