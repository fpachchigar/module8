# Blogging Application: Logical & Physical Model

## 📌 Logical Model (ERD)
The blogging application includes the following entities:

- **Users**
  - UserID (PK)
  - Username
  - Email
  - PasswordHash
  - ProfileImage
  - CreatedAt

- **Posts**
  - PostID (PK)
  - UserID (FK → Users.UserID)
  - Title
  - Description
  - ImageURL
  - CreatedAt

- **Likes**
  - UserID (PK, FK → Users.UserID)
  - PostID (PK, FK → Posts.PostID)
  - CreatedAt

- **Comments**
  - CommentID (PK)
  - UserID (FK → Users.UserID)
  - PostID (FK → Posts.PostID)
  - Content
  - CreatedAt

### ERD Diagram
<img width="1024" height="1536" alt="image" src="https://github.com/user-attachments/assets/f633759c-a7d8-4045-9552-45441dbd248d" />



---

## 📌 Physical Model (SQL Schema)
erDiagram
    USERS {
        INT UserID PK
        VARCHAR Username
        VARCHAR Email
        VARCHAR PasswordHash
        VARCHAR ProfileImage
        TIMESTAMP CreatedAt
    }

    POSTS {
        INT PostID PK
        INT UserID FK
        VARCHAR Title
        TEXT Description
        VARCHAR ImageURL
        TIMESTAMP CreatedAt
    }

    LIKES {
        INT UserID FK
        INT PostID FK
        TIMESTAMP CreatedAt
        PK(UserID, PostID)
    }

    COMMENTS {
        INT CommentID PK
        INT UserID FK
        INT PostID FK
        TEXT Content
        TIMESTAMP CreatedAt
    }

    USERS ||--o{ POSTS : "creates"
    USERS ||--o{ COMMENTS : "writes"
    USERS ||--o{ LIKES : "likes"
    POSTS ||--o{ COMMENTS : "has"
    POSTS ||--o{ LIKES : "receives"

---
<img width="1024" height="1536" alt="ChatGPT Image Sep 13, 2025 at 11_46_55 AM" src="https://github.com/user-attachments/assets/dc0344fb-80e8-473b-8637-7858cb7c7069" />
## 📌 Flowchart (User Interaction)
![Flowchart](A_flowchart_in_the_image_illustrates_the_sequence_.png)
