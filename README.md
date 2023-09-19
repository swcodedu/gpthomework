# gpthomework

## class diagram
``` mermaid
classDiagram
    class User {
        -id
        -email
        +register()
        +leave()
        +viewProfile()
        +editProfile()
        +viewReservations()
    }

    class Space {
        -id
        -type (e.g., Meeting Room, Parking Lot, Attendance)
        +checkAvailability()
    }

    class Reservation {
        -id
        -startTime
        -endTime
        +makeReservation()
        +cancelReservation()
    }

    class Organization {
        -id
        +createOrg()
        +viewOrgInfo()
        +editOrgInfo()
        +deactivateOrg()
    }

    class Group {
        -id
        +createGroup()
        +viewGroupInfo()
        +editGroupInfo()
        +deactivateGroup()
        +deleteGroup()
        +moveSpaceToOtherGroup()
    }

    class Attendance {
        -id
        +markAttendance()
        +viewAttendanceLog()
    }

    class SuperAdmin {
        +manageOrgTemplates()
        +manageSpaceTypes()
        +deactivateOrg()
    }

    class Master {
        +manageGroups()
        +manageUsers()
        +manageSpaces()
        +blockSpaceUsage()
        +approveJoinRequests()
        +releaseUserFromOrg()
        +moveUserToDifferentGroup()
        +viewSpaceUsage()
    }

    User "1"--o"*" Reservation : makes
    User "1"--o"*" Group : belongs to
    Space "1"o--"*" Reservation : has
    Space "1"--o"*" Group : managed by
    Group "1"--o"*" Organization : part of
    Organization "1"o--"*" SuperAdmin : managed by
    Group "1"o--"*" Master : managed by
    Attendance o-- User : logs
    Attendance o-- Space : held at
```

## sequence diagram
``` mermaid
sequenceDiagram
    participant U as User
    participant S as Space
    participant R as Reservation
    participant G as Group
    participant M as Master

    U->>S: checkAvailability()
    S-->>U: availableSlots()
    U->>R: makeReservation(startTime, endTime)
    R->>S: reserveSpace(startTime, endTime)
    S-->>R: confirmation()
    R-->>U: reservationConfirmation()

    Note over U,R: In case of modifications, user can only cancel & rebook
    U->>R: viewReservations()
    R-->>U: currentReservations()
    U->>R: cancelReservation(id)
    R-->>U: cancellationConfirmation()

    U->>G: viewGroupSpaces()
    G->>S: fetchSpaces()
    S-->>U: groupSpaces()

    G->>M: alertSpaceUsage()
    M->>S: viewSpaceUsage()
    S-->>M: currentUsageStats()
```
