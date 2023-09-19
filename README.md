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
