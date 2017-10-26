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

### Create an Invoicely account

Go to https://invoicely.com and create an account

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

Jack uses invoicely.com to register invoices corresponding to Andreas orders. 

Depending on the quantity and type of goods, he applies a tax rate and a discount to each row in the orders CSV
and save the result in his invoicely account.

## Automating invoice creation with IBM RPA

### Creating the Invoice

The [Create Invoice](./assets/Create%20Invoice.atmx) script creates an invoice in Invoicely, given
a unit price, a quantity, an order id and an item description.

1. Login, create Invoice, set order ID, description and quantity

    ![Create Invoice 1](./screenshots/CreateInvoice_01.png)

2. Set tax and unit price

    ![Create Invoice 1](./screenshots/CreateInvoice_02.png)

3. Set client information, save and logout

    ![Create Invoice 1](./screenshots/CreateInvoice_03.png)

### Read the CSV

Since neither the tax nor the discount are part of the CSV, we ask them to the user through a prompt dialog

## Full automation with IBM RPA + IBM ODM


# Issues and contributions
For issues relating to this demo, please use the [GitHub issue tracker](../../issues).
We welcome contibutions following [our guidelines](CONTRIBUTING.md).

# License
The source files found in this project are licensed under the [Apache License 2.0](LICENSE).

# Notice
© Copyright IBM Corporation 2017.

