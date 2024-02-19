Employee management system in Java
import java.util.Scanner;
import java.util.Stack;

public class EmployeeManagementSystem {
    static class Employee {
        String name;
        int id;
        String position;
        float salary;
    }

    public static void main(String[] args) {
        Stack<Employee> employeeStack = new Stack<>();
        Scanner scanner = new Scanner(System.in);
        int choice;

        do {
            System.out.println("\nEmployee Management System");
            System.out.println("1. Add Employee");
            System.out.println("2. Remove Employee");
            System.out.println("3. Display Top Employee");
            System.out.println("4. Exit");
System.out.println("4. Search the Employee");
            System.out.print("Enter your choice: ");
            choice = scanner.nextInt();
            scanner.nextLine(); // Consume newline character

            switch (choice) {
                case 1:
                    Employee newEmployee = new Employee();
                    System.out.print("Enter employee name: ");
                    newEmployee.name = scanner.nextLine();
                    System.out.print("Enter employee ID: ");
                    newEmployee.id = scanner.nextInt();
                    scanner.nextLine(); // Consume newline character
                    System.out.print("Enter employee position: ");
                    newEmployee.position = scanner.nextLine();
                    System.out.print("Enter employee salary: ");
                    newEmployee.salary = scanner.nextFloat();
                    employeeStack.push(newEmployee);
                    break;
                case 2:
                    if (!employeeStack.isEmpty()) {
                        Employee removedEmployee = employeeStack.pop();
                        System.out.println("Removed employee:");
                        displayEmployee(removedEmployee);
                    } else {
                        System.out.println("Employee stack is empty");
                    }
                    break;
                case 3:
                    if (!employeeStack.isEmpty()) {
                        System.out.println("Top employee:");
                        displayEmployee(employeeStack.peek());
                    } else {
                        System.out.println("Employee stack is empty");
                    }
                    break;
                case 4:
                    System.out.println("Exiting program");
                    break;
               case 5:
    if (!employeeStack.isEmpty()) {
        System.out.print("Enter employee ID to search: ");
        int searchId = scanner.nextInt();
        boolean found = false;
        for (Employee emp : employeeStack) {
            if (emp.id == searchId) {
                System.out.println("Employee found:");
                displayEmployee(emp);
                found = true;
                break;
            }
        }
        if (!found) {
            System.out.println("Employee with ID " + searchId + " not found");
        }
    } else {
        System.out.println("Employee stack is empty");
    }
    break;

                default:
                    System.out.println("Invalid choice");
            }
        } while (choice != 4);
    }

    static void displayEmployee(Employee emp) {
        System.out.println("Name: " + emp.name);
        System.out.println("ID: " + emp.id);
        System.out.println("Position: " + emp.position);
        System.out.println("Salary: " + emp.salary);
    }
}




