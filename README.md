# 🚀 _TRANSACTIONS APPLICATION_

## ⚙ Functionalities

This applications simply take care of _income_ and _outcome_ transactions you make, then return to you as **JSON** all transactions and the balance with the _income_, _outcome_ and the _total_ value.

## 🛠 What i used in this application

- **NODE**
- **TYPESCRIPT**
- **JEST**
- **EXPRESS**
- **Data Base: Postgres**

## 🛢 Data Base

- **DBNAME: TransactionsApp**
- **PORT: 5432**

## 🤝 Third party helpers

- eslint (airbnb-base)
- uuidv4
- prettier
- ts-node-dev
- yarn

## 💻 Usage

### First as always run { yarn }

### **Routes:**

> [ POST ] /transactions: this rout shout recive a **title**, **value**, **type** (income or outcome) and **category** inside of the request body. When you make a new transaction, this one should be registered in your data base, with the fields _id_, _title_, _created_at_,_updated_at_.

- Detail: If you create more than onde transaction with the same category this catagory will be reused insted of creating another one with the same name.

```JSON
{
  "id": "uuid",
  "title": "Salary",
  "value": 2000,
  "type": "income",
  "category": "Job"
}
```

> [ GET ] /transactions: This route should return a list with all the transactions that you made until now, along with the sum of the income and the outcome values. the response should be like this:

```JSON
{
  "transactions": [
    {
      "id": "uuid",
      "title": "Salary",
      "value": 4000,
      "type": "income",
      "category": {
        "id": "uuid",
        "title": "Job",
        "created_at": "2020-04-20T00:00:49.620Z",
        "updated_at": "2020-04-20T00:00:49.620Z"
      },
      "created_at": "2020-04-20T00:00:49.620Z",
      "updated_at": "2020-04-20T00:00:49.620Z"
    },
    {
      "id": "uuid",
      "title": "Freelancer",
      "value": 2000,
      "type": "income",
      "category": {
        "id": "uuid",
        "title": "Others",
        "created_at": "2020-04-20T00:00:49.620Z",
        "updated_at": "2020-04-20T00:00:49.620Z"
      },
      "created_at": "2020-04-20T00:00:49.620Z",
      "updated_at": "2020-04-20T00:00:49.620Z"
    },
    {
      "id": "uuid",
      "title": "Motorcycle",
      "value": 4000,
      "type": "outcome",
      "category": {
        "id": "uuid",
        "title": "Recreation",
        "created_at": "2020-04-20T00:00:49.620Z",
        "updated_at": "2020-04-20T00:00:49.620Z"
      },
      "created_at": "2020-04-20T00:00:49.620Z",
      "updated_at": "2020-04-20T00:00:49.620Z"
    },
    {
      "id": "uuid",
      "title": "Notebook",
      "value": 1200,
      "type": "outcome",
      "category": {
        "id": "uuid",
        "title": "Recreation",
        "created_at": "2020-04-20T00:00:49.620Z",
        "updated_at": "2020-04-20T00:00:49.620Z"
      },
      "created_at": "2020-04-20T00:00:49.620Z",
      "updated_at": "2020-04-20T00:00:49.620Z"
    }
  ],
  "balance": {
    "income": 6000,
    "outcome": 5200,
    "total": 800
  }
}
```

> [ DELETE ] /transactions/:id should delete a transactions with the id passed on the route params
> [ POST ] /transactions/import This route should allow an **.csv** file that contains the same required information for the creation of a transactions **id, title, value, category**, where each row of the **CSV** file should be a new registry for the data base, by the end return all the transactions that where imported for your data base. This, should be the format of the **CSV** file

```
title, type, value, category
Gabriel, income, 3000, Others
Website Hosting, outcome, 100, Job
Pizza, outcome, 15, iFood
```

## 📝 Test Especifications

- should be able to create a new transaction.
- should be able to list the transactions.
- should not be able to create outcome transaction without a valid balance.
