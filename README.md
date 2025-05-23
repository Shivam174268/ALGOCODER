# ALGOCODER
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

// employee class create
abstract class Employee {
    // essential detail hide from the user
    protected String name;
    // code is secure to use pirvate access modifier
    protected int id;

    public Employee(String name, int id) {
        // constructure are used
        this.name = name;
        this.id = id;
    }
// to get the user id
    public int getId() {
        return id;
    }

    public abstract double calculateSalary();

    public void displayInfo() {
        System.out.println("ID: " + id + ", Name: " + name + ", Salary: " + calculateSalary());
    }
}
// to create fuiil time class calculate the monthly salary
 class FullTimeEmployee extends Employee {
    // inheritance the subclass from parent class
     private double monthlySalary;

     public FullTimeEmployee(String name, int id, double monthlySalary) {
         super(name, id);
         this.monthlySalary = monthlySalary;
     }
// method override
     @Override
     public double calculateSalary() {
         return monthlySalary;
     }
     // to create class part time job
 } class PartTimeEmployee extends Employee {
     private int hoursWorked;
     private double hourlyRate;

     public PartTimeEmployee(String name, int id, int hoursWorked, double hourlyRate) {
         super(name, id);
         this.hoursWorked = hoursWorked;
         this.hourlyRate = hourlyRate;
     }

     @Override
     public double calculateSalary() {
         // calculate salary part time job
         return hoursWorked * hourlyRate;
     }
 }

// to create payroll  class in which there are all member
 class PayrollSystem {
     private List<Employee> employees = new ArrayList<>();
     // array concept are used

     public void addEmployee(Employee e) {
         employees.add(e);
     }

     public void removeEmployee(int id) {
         Iterator<Employee> iterator = employees.iterator();
         // here looping concept are used to message the user if user id is present then open their calculate it salary
                 while (iterator.hasNext()) {
             if (iterator.next().getId() == id) {
                 iterator.remove();
                 break;
             }
         }
     }
// to create display method
     public void displayEmployees() {
         // for each loop are used
         for (Employee e : employees) {
             // to call display method
             e.displayInfo();
         }
     }
 }
 // in main class `
public class Main {
    public static void main(String[] args) {
        PayrollSystem payrollSystem = new PayrollSystem();
// to craete object and pass the value
        FullTimeEmployee emp1 = new FullTimeEmployee("Vikas", 1, 75000);
        PartTimeEmployee emp2 = new PartTimeEmployee("Alexander", 2, 40, 300);
// to call the method
        payrollSystem.addEmployee(emp1);
        payrollSystem.addEmployee(emp2);
// print output intial payment , id remaining employee detail
        System.out.println("Initial Employee Details:");
        payrollSystem.displayEmployees();

        System.out.println("Removing Employee with ID 2");
        payrollSystem.removeEmployee(2);

        System.out.println("Remaining Employee Details:");
        // to call the payroll method
        payrollSystem.displayEmployees();
    }
