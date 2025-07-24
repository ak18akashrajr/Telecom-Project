# Telecom Billing and Customer Service System

## Modules
The system comprises six primary modules:

- `Customer Management`
    Add, Edit, Delete Customer records.
    View Customer Profiles.

- `Plan Management`
    Create, Update, Delete Mobile Plans.
    Supports Prepaid, Postpaid, and Corporate plan types.

- `Usage Tracking`
    Record Call and Data usage.
    View usage per customer.

- `Billing Module`
    Generate monthly bills (auto-calculated based on plan and usage).
    Calculate taxes and surcharges.
    PDF/HTML bill generation.

- `Payment Module`
    Track payment due/paid status.
    Send payment reminders.
    Apply late payment penalties.

- `Service Control`
    Temporarily deactivate/reactivate customers for non-payment.
    Initiate permanent disconnection.

## Entities and Relationships (ER)
### Entities:

- Customer
    Attributes: CustomerID (Primary Key), Name, Phone, Email, Address, Plan_ID (Foreign Key), Status (Active/Inactive)

- Plan
    Attributes: PlanID (Primary Key), Name, Type (Prepaid/Postpaid), Monthly Fee, Data Limit, Call Limit

- Usage
    Attributes: Customer_ID (Foreign Key), Month, CallMinutesUsed, DataUsed_GB

- Bill
    Attributes: Bill_ID (Primary Key), Customer_ID (Foreign Key), Month, TotalAmount, DueDate, Status (Paid/Unpaid)

- Payment
    Attributes: Payment_ID (Primary Key), Bill_ID (Foreign Key), Date, Amount, Mode (UPI/Credit Card/NetBanking)

### Relationships: 

- Customer to Plan: Many-to-One (Many Customers can have one Plan)

- Customer to Usage: One-to-Many (One Customer has many Usage records)

- Customer to Bill: One-to-Many (One Customer has many Bills)

- Bill to Payment: One-to-Many (One Bill can have many Payments)