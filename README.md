# 🚀 _TRANSACTIONS APPLICATION_

## ⚙ Functionalities

This applications simply take care of _income_ and _outcome_ transactions you make, then return to you as **JSON** all transactions and the balance with the _income_, _outcome_ and the _total_ value.

## 🛠 What i used in this application

- **NODE**
- **TYPESCRIPT**
- **JEST**
- **EXPRESS**

## 🤝 Third party helpers

- eslint (airbnb-base)
- uuidv4
- prettier
- ts-node-dev
- yarn

## 💻 Usage

### First as always run { yarn }

### **Routes:**

> [ POST ] /transactions: this rout shout recive a **title**, **value**, **type** (income or outcome), inside of the request body. So the response should be like this:

```JSON
{
  "id": "uuid",
  "title": "Salary",
  "value": 2000,
  "type": "income"
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
      "type": "income"
    },
    {
      "id": "uuid",
      "title": "Freelancer",
      "value": 2000,
      "type": "income"
    },
    {
      "id": "uuid",
      "title": "Motorcycle",
      "value": 4000,
      "type": "outcome"
    },
    {
      "id": "uuid",
      "title": "Notebook",
      "value": 1200,
      "type": "outcome"
    }
  ],
  "balance": {
    "income": 6000,
    "outcome": 5200,
    "total": 800
  }
}
```

## 📝 Test Especifications

- should be able to create a new transaction.
- should be able to list the transactions.
- should not be able to create outcome transaction without a valid balance.
