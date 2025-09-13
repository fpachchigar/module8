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

```sql
-- Users Table
CREATE TABLE Users (
    UserID INT PRIMARY KEY AUTO_INCREMENT,
    Username VARCHAR(50) NOT NULL UNIQUE,
    Email VARCHAR(100) NOT NULL UNIQUE,
    PasswordHash VARCHAR(255) NOT NULL,
    ProfileImage VARCHAR(255),
    CreatedAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Posts Table
CREATE TABLE Posts (
    PostID INT PRIMARY KEY AUTO_INCREMENT,
    UserID INT NOT NULL,
    Title VARCHAR(255) NOT NULL,
    Description TEXT,
    ImageURL VARCHAR(255),
    CreatedAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (UserID) REFERENCES Users(UserID) ON DELETE CASCADE
);

-- Likes Table (Composite Primary Key to avoid duplicates)
CREATE TABLE Likes (
    UserID INT NOT NULL,
    PostID INT NOT NULL,
    CreatedAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    PRIMARY KEY (UserID, PostID),
    FOREIGN KEY (UserID) REFERENCES Users(UserID) ON DELETE CASCADE,
    FOREIGN KEY (PostID) REFERENCES Posts(PostID) ON DELETE CASCADE
);

-- Comments Table
CREATE TABLE Comments (
    CommentID INT PRIMARY KEY AUTO_INCREMENT,
    UserID INT NOT NULL,
    PostID INT NOT NULL,
    Content TEXT NOT NULL,
    CreatedAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (UserID) REFERENCES Users(UserID) ON DELETE CASCADE,
    FOREIGN KEY (PostID) REFERENCES Posts(PostID) ON DELETE CASCADE
);
```

---

## 📌 Flowchart (User Interaction)
![Flowchart](A_flowchart_in_the_image_illustrates_the_sequence_.png)
