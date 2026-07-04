# Knowledge Map

This map shows the long-term learning connection for Java-Backend-Master-Course.

`MASTER_BOOK.md` remains the authority for curriculum order.

```mermaid
flowchart LR
    Java["Java Recovery"]
    OOP["OOP"]
    Collection["Collection"]
    Spring["Spring Boot"]
    ERP["ERP"]

    Java --> OOP
    OOP --> Collection
    Collection --> Spring
    Spring --> ERP

    Java -. supports .-> Spring
    OOP -. models domains .-> ERP
    Collection -. handles business data .-> ERP
    Spring -. exposes APIs .-> ERP
```

## Learning Chain

- Java builds syntax and basic problem-solving ability.
- OOP builds domain modeling ability.
- Collection builds business data handling ability.
- Spring Boot builds backend API ability.
- ERP combines the full backend stack into business software.
