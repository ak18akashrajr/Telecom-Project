# Project - Telecom Billing and Customer Service Management System

## 1. Description

The main goal of this project is to create a simple system for a telecom company to manage its customers and billing. It acts as a digital assistant for the company's admin staff.

It helps with tasks such as:

* Signing up new customers with proper verification
* Keeping track of their mobile plans (Prepaid or Postpaid)
* Monitoring data and call time usage
* Automatically creating and sending monthly bills
* Recording payments and handling service status changes

---

## 2. Modules

### Customer Management

* Handle all customer information
* Add, update, or delete customer records
* View full customer profiles

### Plan Management

* Create, update, or remove mobile plans
* Manage various plan types: Prepaid, Postpaid, and Corporate

### Usage Tracking

* Record call minutes and data usage monthly
* View individual usage history per customer

### Billing Module

* Automatically calculate and generate bills every month
* Include monthly plan fees and extra charges for overuse
* Add applicable taxes and surcharges

### Payment Module

* Record and update bill payments
* Send payment reminders for unpaid bills
* Apply late payment penalties

### Service Control

* Temporarily deactivate service due to non-payment
* Reactivate service after payment is made
* Perform permanent disconnections for inactive or defaulting customers

---

## 3. Storage of Information (Data Structure)

### Customer

* Stores: Name, Phone, Email, Address, and National ID (e.g., Aadhaar)
* Unique identifier: Cust\_ID

### Plan

* Stores: Plan Name, Type (Prepaid/Postpaid), Monthly Fee, Call and Data Limits
* Unique identifier: Plan\_ID

### Registered Sim (RegSim)

* Links a customer to a plan using Sim\_No
* Tracks the current status of the SIM (Active/Inactive)

### Usage

* Tracks monthly data and call minutes used by each SIM
* Connected to RegSim for customer reference

### Bill

* Stores: Total Amount, Due Date, and Payment Status
* Linked to the respective SIM and usage for a specific month

### Payment

* Records all payments made toward bills
* Stores: Amount, Date, and Mode of Payment (UPI, Credit Card, etc.)

---

## 4. Detailed Processes and Case Study

### Customer Registration and SIM Allocation

#### Step 1: Identity Verification

* Verify identity using national ID (e.g., Aadhaar)
* Check the ID’s validity in the system

#### Step 2: Check Existing Connections

* System checks how many SIMs are already registered to the ID
* If the user has 9 SIMs: request is denied
* If under the limit: continue registration

#### Scenario A: New Customer Registration

* Admin enters new customer details
* Upon successful verification, a new Cust\_ID is generated
* Customer selects a plan, and a SIM is issued (new RegSim entry)

#### Scenario B: Existing Customer Gets a New SIM

* Admin searches customer by phone number or Cust\_ID
* System repeats identity and SIM limit check
* If allowed, new RegSim entry is created with a selected plan

### Billing and Payment Cycle

#### Bill Generation

* On a fixed day each month (e.g., 1st), the system:

  * Calculates total due for each active postpaid SIM
  * Adds plan fee, extra usage charges, taxes
  * Stores bill in the Bill table

#### Notifications

* System notifies customers via SMS and email about generated bills and due dates

#### Reminders

* First reminder is sent a few days before the due date
* Second reminder after due date if still unpaid

#### Recording Payment

* When payment is made, it is recorded in the Payment table
* Bill status is automatically updated to "Paid"

### Service Deactivation and Reactivation

#### Deactivation Triggers

* Non-payment beyond grace period (e.g., 15 days)
* Customer requests temporary suspension
* Security concerns or fraudulent usage

#### Reactivation

* After dues are cleared
* Or as requested by the customer
* Reconnection fees may apply

#### Permanent Disconnection

* If a service remains unpaid and deactivated for over 90 days
* Number is permanently disconnected and may be reassigned

---



## 5. Conclusion

This system provides a structured and scalable approach to manage telecom billing operations. It automates core functions such as billing, usage tracking, and payment collection, ensuring accuracy, compliance, and customer satisfaction.
