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

    %% 약한 엔티티 표시 (Manager는 Owner에 종속됨)
    OWNER ||--o{ MANAGER : "employs (1:N)"
    MANAGER ||--o{ COMPUTER : "manages (1:N)"
    CUSTOMER ||--|| COMPUTER : "uses (1:1)"
    CUSTOMER ||--o{ MANAGER : "places_order_with (1:N)"

    %% 관계 속성들
    EMPLOYMENT {
        int working_hours
        int hourly_wage
    }
    
    MANAGEMENT {
        string management_zone
    }

    ORDER {
        int price
        string items
    }
