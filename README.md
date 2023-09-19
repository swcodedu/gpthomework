# gpthomework

## class diagram
``` mermaid
classDiagram
  class User {
    + email: string
    + register()
    + login()
    + viewProfile()
    + editProfile()
    + viewReservationStatus()
    + makeReservation()
    + cancelReservation()
  }

  class Admin {
    + manageOrganization()
    + manageGroups()
    + manageSpaces()
  }

  class SuperAdmin {
    + createOrganization()
    + manageOrganization()
    + manageGroups()
    + manageSpaces()
  }

  class Master {
    + manageGroups()
    + manageUsers()
    + manageSpaces()
    + manageAttendance()
  }

  class Space {
    + type: string
    + createSpace()
    + manageSpace()
    + viewAvailability()
    + blockTimeSlot()
    + viewAttendance()
    + viewAttendanceHistory()
  }

  class Organization {
    + createGroup()
    + manageGroups()
    + manageSpaces()
  }

  User --|> SuperAdmin : Inherits
  User --|> Admin : Inherits
  User --|> Master : Inherits
  Admin --|> Organization : Manages
  SuperAdmin --|> Organization : Manages
  Master --|> Organization : Manages
  Master --|> Space : Manages
  Space --|> Organization : Belongs to
  Admin --|> Space : Manages
  SuperAdmin --|> Space : Manages
  Master --|> User : Manages
  Organization --|> Group : Contains
  Organization --|> Space : Manages
  Group --|> User : Contains
```

## sequence diagram
``` mermaid
@startuml
actor User
participant App
database DB

User -> App: 로그인 요청
App -> DB: 사용자 확인
DB --> App: 사용자 정보 반환
App --> User: 로그인 성공 메시지

@enduml
```
