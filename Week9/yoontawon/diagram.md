```mermaid
erDiagram
    OWNER {
        string 사업자번호 PK
        string 지점명
        string 전화번호
        string 점주명
    }

    MANAGER {
        string 이름 PK
        date 생년월일
        string 주소
        string 연락처
        string 사업자번호 FK
    }

    COMPUTER {
        int 컴퓨터번호 PK
        string 스펙
        boolean 부팅유무
    }

    CUSTOMER {
        int 아이디 PK
        int 사용시간
        string 패스워드
        string 핸드폰번호
    }

    OWNER ||--o{ MANAGER : "고용"
    MANAGER ||--o{ COMPUTER : "관리"
    CUSTOMER ||--|| COMPUTER : "사용"
    CUSTOMER ||--o{ MANAGER : "주문"

    고용 {
        int 근무시간
        int 시급
    }

    관리 {
        string 관리구역
    }

    주문 {
        int 가격
        string 품목
    }
