# CourseWork_4sem [Novak Ksenia 353504]

## Content Sharing Web Application with Adaptive Recommendation System

People naturally seek out connection and interaction with others, and this tendency is a fundamental aspect of human nature. In the digital age, where interactions often happen through screens, content sharing platforms serve as vital conduits for communication. These platforms enable users to express themselves, share their thoughts, ideas, and creativity, thus contributing to the development of a more dynamic and varied information landscape.

JWT upon successful authentication, which will be used for subsequent requests to verify their identity. OAuth 2.0 will be used for secure authorization, allowing users to log in through various external services. The project will utilize a REST API to facilitate communication between the client and server. This will enable seamless data exchange and interaction with the application’s resources, such as user profiles, posts, and comments, using standard HTTP methods.


## Functional Requirements

1. **Authorization via mail** – the ability to log in through other services.
2. **User profile** – text description field.
3. **Creating a note** – with the ability to add a hashtag(s).
4. **Creating comments** – to your own or other people's posts, the "like" function, reposts to your page.
5. **A feed of recommendations** – based on user preferences, subscriptions, and used/viewed hashtags.


### 1. The User Model

**Purpose:** Authorization management and storage of user information.

**Fields:**
- `userId` (String): The unique user ID.
- `username` (String): Username.
- `email` (String): The email address for authentication.
- `passwordHash` (String): A hash of the password to ensure security.
- `profilePicture` (String): The URL to the profile picture.
- `bio` (String): A text description of the user.
- `createdAt` (Date): The registration date.
- `updatedAt` (Date): The date of the last profile update.
- `authProvider` (String): The service that the user used to register (for example, Google, Facebook).

**Methods:**
- `register()`: Registration of a new user via email or an external service.
- `login()`: The user logs into the application via email or an external service.
- `editProfile()`: Changing profile information.
- `deleteAccount()`: Deleting an account.

### 2. The Post Model

**Purpose:** Storing and managing records created by users.

**Fields:**
- `postId` (String): The unique identifier of the post.
- `title` (String): The title of the post.
- `content` (String): The main content of the post.
- `createdAt` (Date): The date when the post was created.
- `updatedAt` (Date): The date of the last update of the post.
- `userId` (String): The ID of the user who created the post.
- `hashtags` (Array of Strings): A list of hashtags associated with a post.

**Methods:**
- `createPost()`: Create a new post with hashtags.
- `editPost()`: Editing an existing post.
- `deletePost()`: Deleting a post.
- `getPost()`: Getting information about a post.
- `likePost()`: Adding the "like" function to a post.
- `repost()`: Repost a post on your page.

### 3. The Comment Model

**Purpose:** Storing and managing comments on posts.

**Fields:**
- `commentId` (String): The unique ID of the comment.
- `content` (String): The content of the comment.
- `createdAt` (Date): The date when the comment was created.
- `userId` (String): The ID of the user who wrote the comment.
- `postId` (String): The ID of the post to which the comment belongs.

**Methods:**
- `addComment()`: Adding a new comment to a post.
- `editComment()`: Editing an existing comment.
- `deleteComment()`: Deleting a comment.
- `getCommentsByPost()`: Getting all comments for a specific post.

### 4. Recommendation Model

**Goal:** Generate recommendations for users based on their interactions and interests.

**Fields:**
- `recommendationId` (String): The unique identifier of the recommendation.
- `userId` (String): The identifier of the user for whom the recommendation is intended.
- `postId` (String): The ID of the recommended post.
- `reason` (String): Description of the reason for the recommendation (for example, based on viewed hashtags or subscriptions).
