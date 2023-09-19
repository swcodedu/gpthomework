# gpthomework

## class diagram
``` mermaid
classDiagram
    class User {
        +id: UUID
        +email: String
        +isAuthenticated: Boolean
        +personalInfo: String
        +bookings: Booking[]
    }
    class Booking {
        +id: UUID
        +spaceId: UUID
        +startTime: DateTime
        +endTime: DateTime
    }
    class Organization {
        +id: UUID
        +info: String
        +isActive: Boolean
    }
    class Space {
        +id: UUID
        +type: SpaceType
        +availabilityStart: Time
        +availabilityEnd: Time
    }
    class Group {
        +id: UUID
        +info: String
        +members: User[]
        +spaces: Space[]
    }
    class Admin {
        +id: UUID
        +type: AdminType
    }
    class Attendance {
        +id: UUID
        +attendanceDate: Date
        +attendanceType: AttendanceType
        +userId: UUID
    }
    enum SpaceType {
        MEETING_ROOM
        PARKING_LOT
        ATTENDANCE_LIST
    }
    enum AdminType {
        SUPER_ADMIN
        MASTER
    }
    enum AttendanceType {
        PRESENT
        ABSENT
        LATE
        LEFT_EARLY
    }

    User "1" --> "*" Booking : makes
    Organization "1" --> "*" Group : has
    Group "1" --> "*" User : contains
    Group "1" --> "*" Space : manages
    Admin "1" --> "*" Organization : manages (for Super Admin)
    Admin "1" --> "*" Group : manages (for Master)
    Space "1" --> "*" Attendance : tracks
    User "1" --> "*" Attendance : isFor
```
