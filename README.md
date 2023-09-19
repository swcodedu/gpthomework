# gpthomework

## class diagram
``` mermaid
classDiagram
    class User {
        +String email
        +String password
        +Boolean isAuthenticated
        +viewSpaceInfo()
        +makeReservation()
        +cancelReservation()
    }

    class Admin {
        +createOrganization()
        +modifyOrganization()
        +deactivateOrganization()
        +manageSpaceTemplate()
    }
    
    class SuperAdmin {
    }
    
    class Master {
        +approveUser()
        +denyUser()
        +manageUserInGroup()
        +manageSpaceInGroup()
        +createSpaceInGroup()
        +modifySpaceInfo()
        +blockSpaceForTime()
        +viewSpaceUsage()
        +viewAttendance()
    }
    
    class Space {
        +DateTime startTime
        +DateTime endTime
        +String type
        +setAvailableTime()
    }

    class MeetingRoomSpace {
        +setHourlyAvailableTime()
    }

    class ParkingSpace {
        +set10MinAvailableTime()
    }

    class AttendanceSpace {
        +registerAttendanceList()
        +modifyAttendanceList()
    }

    User --|> AuthenticatedUser : Inherits
    Admin --|> SuperAdmin : Inherits
    Admin --|> Master : Inherits
    Space --|> MeetingRoomSpace : Inherits
    Space --|> ParkingSpace : Inherits
    Space --|> AttendanceSpace : Inherits
```
