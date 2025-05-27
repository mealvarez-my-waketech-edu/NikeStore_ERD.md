# NikeStore_ERD.md
Understand the Business Context:
o *Products: Represents different models of Nike shoes sold in the store.
o Customers: Details about customers who purchase shoes.
o Sales: Transaction records linking customers and the products they buy.
o Inventory: Tracks the stock levels of various shoe models.

```mermaid
erDiagram
    PRODUCT ||--o{ INVOICE : allows
    PRODUCT {
        string serialNumber PK
        string type
        string size
        string color
    }
    CUSTOMER ||--o{ ORDER : places
    CUSTOMER ||--o{ INVOICE : liable for
    CUSTOMER {
        string membershipNumber PK
        string firstName
        string lastName
        string phone
        int age
    }
    ORDER {
        string orderNumber PK
        string membershipNumber PK, FK
        string serialNumber PK, FK
    }
    INVOICE {
        string invoiceNumber PK
        string membershipNumber PK, FK
        string serialNumber PK, FK
    }
    MANUFACTURER only one to zero or more PRODUCT : makes
```
