# ODM RPA Invoicing sample

This sample describe how to integrate IBM Operational Decision Manager with IBM RPA.

## Table of Contents

  - [Before you begin](#before-you-begin)
     - [Create an Invoicely account](#create-an-invoicely-account)
     - [Create a Credential vault in IBM RPA Control Room](#create-a-credential-vault-in-ibm-rpa-control-room)
  - [Scenario](#scenario)
  - [Automating invoice creation with IBM RPA](#automating-invoice-creation-with-ibm-rpa)
     - [Creating the Invoice](#creating-the-invoice)
     - [Read the CSV](#read-the-csv)
  - [Full automation with IBM RPA + IBM ODM](#full-automation-with-ibm-rpa-ibm-odm)

---

## Before you begin

### Required software

Here is the list of software you need to install in order to run the demo:

* [IBM Robotic Process Automation with Automation Anywhere](https://www.ibm.com/cloud-computing/products/digital-process-automation/robotic-process-automation/)
* [IBM Operational Decision Manager](http://www-03.ibm.com/software/products/en/odm)
* [NodeJS](https://nodejs.org/en/download/)

### Create an Invoicely account

Go to [](https://invoicely.com) and create an account

### Create a Credential vault in IBM RPA Control Room

* Log in to Control Room
* Go to the *Credential Manager* tab
* Click *Add Credential*
* Name it **Invoicely**
* Add the following attributes, wit their corresponding values:
   * **email**: email you used to create your Invoicely account.
   * **password**: password for your account
   * **business**: name of the 'business' entity you created when creating your invoicely account.

## Scenario

Jack is an accountant for Acme Retail, a small retailing company.

Andrea is a reseller for Acme Retail. Each week, she orders a list of goods to Jack, sending him 
<a target="_blank" href="./assets/invoices.csv">a CSV file </a>
listing the quantity and unit price of each item she wants to order.

<img src="https://raw.githubusercontent.com/ODMDev/odm-rpa-invoicing-sample/master/screenshots/Orders.png" width="75%"></img>

Jack uses invoicely.com to register invoices corresponding to Andreas orders. 

Depending on the quantity and type of goods, he applies a tax rate and a discount to each row in the orders CSV
and save the result in his invoicely account.

<img src="https://raw.githubusercontent.com/ODMDev/odm-rpa-invoicing-sample/master/screenshots/Invoicely_Create.png" width="75%"></img>

## Step 1: Automating invoice creation with IBM RPA

Our first step consists of recording an Automation Anywhere task that reads the CSV file, and, for each row, connects 
to [](http://invoicely.com) and create the corresponding invoice.

Since the tax rate and discounted price are not present in the CSV, we prompt the user during the process in order to get those values.

### Creating the Invoice

The [Create Invoice.atmx](./assets/Create%20Invoice.atmx) task creates an invoice in Invoicely, given
a unit price, a quantity, an order id, an item description, a tax rate, and a client first name and last name.

1. Login, create Invoice, set order ID, description and quantity

    ![Create Invoice 1](./screenshots/CreateInvoice_01.png)

2. Set tax and unit price

    ![Create Invoice 1](./screenshots/CreateInvoice_02.png)

3. Set client information, save and logout

    ![Create Invoice 1](./screenshots/CreateInvoice_03.png)

### Main Loop

The [Main.atmx](./assets/Main.atmx) task does the following:
* Opens orders CSV file
* For each row
   * Prompt the user with the tax rate
   * Prompt the user with the discounted prixe
   * Invoke the invoice creation task.

![Main](./screenshots/Main.png)

## Step 2: Full automation with IBM RPA + IBM ODM


# Issues and contributions
For issues relating to this demo, please use the [GitHub issue tracker](../../issues).
We welcome contibutions following [our guidelines](CONTRIBUTING.md).

# License
The source files found in this project are licensed under the [Apache License 2.0](LICENSE).

# Notice
© Copyright IBM Corporation 2017.

