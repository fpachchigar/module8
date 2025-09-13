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
![Logical Model](logical model.png)

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

## 📌 Flowchart (User Interaction)
![Flowchart](A_flowchart_in_the_image_illustrates_the_sequence_.png)
