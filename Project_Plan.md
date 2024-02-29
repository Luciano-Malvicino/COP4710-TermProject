# testing

### User Table
| Attribute Name         | Data Type               | Key Constraint           |
|------------------------|-------------------------|--------------------------|
| UserID                 | INT                     | Primary Key              |
| Username               | VARCHAR(255)            |                          |
| Password               | VARCHAR(255)            |                          |
| UserType               | ENUM('Regular', 'Admin', 'SuperAdmin') |                          |

### Events Table
| Attribute Name         | Data Type               | Key Constraint           |
|------------------------|-------------------------|--------------------------|
| EventID                | INT                     | Primary Key              |
| Name                   | VARCHAR(255)            |                          |
| Category               | VARCHAR(255)            |                          |
| Description            | TEXT                    |                          |
| Time                   | TIME                    |                          |
| Date                   | DATE                    |                          |
| ContactPhone           | VARCHAR(20)             |                          |
| ContactEmail           | VARCHAR(255)            |                          |
| EventType              | ENUM('Public', 'Private', 'RSO') |                          |
| AverageRating          | DECIMAL(5, 2)            |                          |
| Latitude               | DECIMAL(9, 6)           |                          |
| Longitude              | DECIMAL(9, 6)           |                          |

### Comments Table
| Attribute Name         | Data Type               | Key Constraint           |
|------------------------|-------------------------|--------------------------|
| CommentID              | INT                     | Primary Key              |
| EventID                | INT                     | Foreign Key (Events.EventID) |
| UserID                 | INT                     | Foreign Key (Users.UserID) |
| Text                   | TEXT                    |                          |
| Rating                 | INT                     |                          |
| Timestamp              | TIMESTAMP               |                          |

### SuperAdmins Table
| Attribute Name         | Data Type               | Key Constraint           |
|------------------------|-------------------------|--------------------------|
| UserID                 | INT                     | Primary Key, Foreign Key (Users.UserID) |
| OwnedUniversityID      | INT                     | Foreign Key (Universities.UniversityID) |
| (Additional attributes specific to super admins) | (Data type) |          |

### Admins Table
| Attribute Name         | Data Type               | Key Constraint           |
|------------------------|-------------------------|--------------------------|
| UserID                 | INT                     | Primary Key, Foreign Key (Users.UserID) |
| UniversityAffiliationID| INT                     | Foreign Key (Universities.UniversityID) |
| OwnedRSOID             | INT                     | Foreign Key (RSOs.RSOID) |
| (Additional attributes specific to admins) | (Data type) |              |

### RSOs Table
| Attribute Name         | Data Type               | Key Constraint           |
|------------------------|-------------------------|--------------------------|
| RSOID                  | INT                     | Primary Key              |
| Name                   | VARCHAR(255)            |                          |
| UniversityID           | INT                     | Foreign Key (Universities.UniversityID) |
| AdministratorUserID    | INT                     | Foreign Key (Users.UserID) |
| NumberOfMembers        | INT                     |                          |
| AdministratorAssigned | BOOLEAN                  |                          |
| (Other RSO-related attributes) | (Data type)           |                          |

### Universities Table
| Attribute Name         | Data Type               | Key Constraint           |
|------------------------|-------------------------|--------------------------|
| UniversityID           | INT                     | Primary Key              |
| Name                   | VARCHAR(255)            |                          |
| Location               | VARCHAR(255)            |                          |
| Description            | TEXT                    |                          |
| NumberOfStudents       | INT                     |                          |
| (Other university-related attributes) | (Data type)          |                          |

### Users Table
| Attribute Name         | Data Type               | Key Constraint           |
|------------------------|-------------------------|--------------------------|
| RegularUserRSOID       | INT                     | Primary Key              |
| UserID                 | INT                     | Foreign Key (Users.UserID) |
| RSOID                  | INT                     | Foreign Key (RSOs.RSOID) |


tech stack: mysql with react
