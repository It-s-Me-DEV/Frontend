```mermaid
erDiagram
    OWNER {
        string business_number PK
        string branch_name
        string phone_number
        string owner_name
    }

    MANAGER {
        string name PK
        date birth_date
        string address
        string contact_number
        string owner_business_number FK
    }

    COMPUTER {
        int computer_id PK
        string specifications
        boolean boot_status
    }

    CUSTOMER {
        int customer_id PK
        int usage_time
        string password
        string phone_number
    }

    OWNER ||--o{ MANAGER : "employs"
    MANAGER ||--o{ COMPUTER : "manages"
    CUSTOMER ||--|| COMPUTER : "uses"
    CUSTOMER ||--o{ MANAGER : "places_order_with"

    Employment {
        int working_hours
        int hourly_wage
    }

    Management {
        string management_zone
    }

    Order {
        int price
        string items
    }
