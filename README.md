# NikeStore_ERD.md

```mermaid
erDiagram
    PRODUCT ||--o{ ORDER : allows
    PRODUCT {
        string serialNumber PK
        string manufacturer
        string type
        string size
        string color
    }
    INVENTORY }o--o{ PRODUCT : has
    INVENTORY {
        string storeNumber PK, FK
        string type
        string size
        string color
        string quantity
    }
    ORDER ||--o{ INVOICE : has
    ORDER {
        string orderNumber PK
        string storeNumber PK, FK
        string invoiceNumber PK, FK
        string membershipNumber PK, FK
        string serialNumber PK, FK
    }
    STORE ||--o{ ORDER : has
    STORE ||--o{ INVOICE : has
    STORE ||--o{ INVENTORY : has
    STORE {
        string storeNumber PK
        string address
        string territory
    }
    INVOICE {
        string invoiceNumber PK
        string storeNumber PK, FK
        string orderNumber PK, FK
        string membershipNumber PK, FK
        string serialNumber PK, FK
    }
    CUSTOMER ||--o{ ORDER : places
    CUSTOMER ||--o{ INVOICE : "pays for"
    CUSTOMER {
        string membershipNumber PK
        string firstName
        string lastName
        string phone
        int age
    }
    MANUFACTURER only one to zero or more PRODUCT : makes
```

The entities I have made are PRODUCT, INVENTORY, CUSTOMER, ORDER, STORE, and INVOICE (SALES)
 * Product: an article or substance that is manufactured or refined for sale.
 * Inventory: a complete list of items such as property, goods in stock, or the contents of a building.
 * Customer: a person or organization that buys goods or services from a store or business.
 * Order: a formal request made by a buyer to a seller indicating what they want to purchase and how much they are willing to pay.
 * Store: a business or franchise location.
 * Invoice: a document that outlines goods or services provided by a seller to a buyer, including the price and terms of sale.  
**Definitions from [Google](https://www.google.com/)**

Product to Invoice relationship - **Invoices** are sales made to customers and have lists of **products** purchased.
Inventory to Product relationship - **Inventories** are lists of items such as **products** that detail inforation such as quantity on hand, product characteristics, and pricing.
Customer to Order relationship - **Customers** can place one or many **orders** which have lists of products purchased.
Customer to Invoice relationship - **Customers** orders have associated **invoices** that lists money to be paid for the products purchased.
Store to Order relationship - **Stores** are where **Orders** originate
Store to Invoice relationship - **Stores** are where **Invoices** originate
Order to Invoice relationship - **Orders** always have associated **invoices**
