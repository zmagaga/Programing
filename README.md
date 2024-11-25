Here's a simple Java program for salon management that uses JavaScript for the user interface (note that JavaScript is typically used for client-side web development, while Java is used for server-side or desktop applications). For this example, we'll create a command-line based Java program and use JavaScript only for a hypothetical web interface.


*Java Program (SalonManagement.java)*
```
import java.util.*;

class Customer {
    String name;
    String service;
    String appointmentDate;

    public Customer(String name, String service, String appointmentDate) {
        this.name = name;
        this.service = service;
        this.appointmentDate = appointmentDate;
    }
}

public class SalonManagement {
    static Scanner scanner = new Scanner(System.in);
    static List<Customer> customers = new ArrayList<>();

    public static void main(String[] args) {
        while (true) {
            System.out.println("Salon Management System");
            System.out.println("1. Book Appointment");
            System.out.println("2. View Appointments");
            System.out.println("3. Exit");
            System.out.print("Choose an option: ");
            int option = scanner.nextInt();
            scanner.nextLine(); // Consume newline left-over

            switch (option) {
                case 1:
                    bookAppointment();
                    break;
                case 2:
                    viewAppointments();
                    break;
                case 3:
                    System.exit(0);
                    break;
                default:
                    System.out.println("Invalid option. Please choose again.");
            }
        }
    }

    static void bookAppointment() {
        System.out.print("Enter customer name: ");
        String name = scanner.nextLine();
        System.out.print("Enter service (e.g., haircut, massage): ");
        String service = scanner.nextLine();
        System.out.print("Enter appointment date (YYYY-MM-DD): ");
        String appointmentDate = scanner.nextLine();

        Customer customer = new Customer(name, service, appointmentDate);
        customers.add(customer);
        System.out.println("Appointment booked successfully!");
    }

    static void viewAppointments() {
        if (customers.isEmpty()) {
            System.out.println("No appointments booked.");
        } else {
            System.out.println("Appointments:");
            for (Customer customer : customers) {
                System.out.println(customer.name + " - " + customer.service + " - " + customer.appointmentDate);
            }
        }
    }
}
```

*JavaScript Interface (index.html)*
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Salon Management</title>
    <style>
        body {
            font-family: Arial, sans-serif;
        }
    </style>
</head>
<body>
    <h1>Salon Management</h1>
    <div id="appointments"></div>

    <button id="book-appointment-btn">Book Appointment</button>
    <div id="book-appointment-form" style="display: none;">
        <label>Customer Name:</label>
        <input type="text" id="customer-name"><br><br>
        <label>Service:</label>
        <input type="text" id="service"><br><br>
        <label>Appointment Date:</label>
        <input type="date" id="appointment-date"><br><br>
        <button id="submit-appointment-btn">Book</button>
    </div>

    <script>
        // Simulate data retrieval from Java program
        const appointments = [
            { name: 'John Doe', service: 'Haircut', date: '2024-09-20' },
            { name: 'Jane Doe', service: 'Massage', date: '2024-09-25' }
        ];

        // Display appointments
        const appointmentsDiv = document.getElementById('appointments');
        appointments.forEach((appointment) => {
            appointmentsDiv.innerHTML += `<p>${appointment.name} - ${appointment.service} - ${appointment.date}</p>`;
        });

        // Book appointment form handling
        const bookAppointmentBtn = document.getElementById('book-appointment-btn');
        const bookAppointmentForm = document.getElementById('book-appointment-form');
        const submitAppointmentBtn = document.getElementById('submit-appointment-btn');

        bookAppointmentBtn.addEventListener('click', () => {
            bookAppointmentForm.style.display = 'block';
        });

        submitAppointmentBtn.addEventListener('click', () => {
            const customerName = document.getElementById('customer-name').value;
            const service = document.getElementById('service').value;
            const appointmentDate = document.getElementById('appointment-date').value;

            // Send data to Java program (omitted for simplicity)
            console.log(`Booking appointment for ${customerName} on ${appointmentDate} for ${service}`);

            // Clear form fields
            document.getElementById('customer-name').value = '';
            document.getElementById('service').value = '';
            document.getElementById('appointment-date').value = '';
```
