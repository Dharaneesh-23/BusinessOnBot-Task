# BusinessOnBot-Task

I tried my level best to create this page. As the time constraint was too short for developing a complete web page with responsiveness, could complete only the structures of the web page and there are some errors to be resolved in the models.py file and views.py file in social folder. The html code does not give the proper content as the page is dynamic which gets the content from the database. The database structure is mentioned below [navigate to structure](#database). 

**Overview**
- User Authentication: Users can create accounts, log in, and log out securely.
- Posts: Users can create posts to share content, thoughts, and updates with others.
- Comments: Users can comment on posts to engage in discussions and provide feedback.
- Likes and Dislikes: Users can express their appreciation or disapproval of posts and comments through likes and dislikes.
- Notifications: Users receive notifications for activities such as new comments on their posts, likes on their content, and mentions.
- User Profiles: Each user has a profile where they can provide additional information about themselves, such as their name, bio, profile picture, and location.
- Messaging: Users can send private messages to other users and engage in one-on-one conversations.
- Tags: Posts can be tagged with keywords or categories to organize and categorize content.
- Threads: Users can participate in threaded conversations, allowing for organized discussions on specific topics.
- File Uploads: Users can upload images to accompany their posts and messages.

## database
- User: Represents registered users of the platform.
- Attributes: id (primary key), username, password, email, etc.

- Comment: Represents comments made by users on posts.
- Attributes: id (primary key), comment, created_on, author_id (foreign key to User), post_id (foreign key to Post), parent_id (foreign key to self for nested comments), likes (many-to-many relationship with User), dislikes (many-to-many relationship with User).

- Post: Represents posts created by users.
- Attributes: id (primary key), shared_body, body, created_on, shared_on, author_id (foreign key to User), shared_user_id (foreign key to User), tags (many-to-many relationship with Tag), likes (many-to-many relationship with User), dislikes (many-to-many relationship with User), image (many-to-many relationship with Image).

- Tag: Represents tags associated with posts.
- Attributes: id (primary key), name.

- UserProfile: Extends the built-in User model to store additional user information.
- Attributes: user_id (primary key, foreign key to User), name, bio, birth_date, location, picture, followers (many-to-many relationship with User).

- Notification: Represents notifications for user activities.
- Attributes: id (primary key), notification_type, date, user_has_seen, from_user_id (foreign key to User), to_user_id (foreign key to User), post_id (foreign key to Post), comment_id (foreign key to Comment), thread_id (foreign key to ThreadModel).

- ThreadModel: Represents threads for private messaging between users.
- Attributes: id (primary key), user_id (foreign key to User), receiver_id (foreign key to User).

- MessageModel: Represents messages within threads.
- Attributes: id (primary key), body, image, date, is_read, sender_user_id (foreign key to User), receiver_user_id (foreign key to User), thread_id (foreign key to ThreadModel).

- Image: Represents images uploaded by users.
- Attributes: id (primary key), image.
