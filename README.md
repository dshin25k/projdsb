# Project DSB

_(**D**)avid (**S**)hin's (**B**)log_

This project is for learning and practicing basic web development. I
will gradually build this simple blogging platform while studying for
_LPI Web Development Essentials_ from
_[Linux Professional Institute](https://www.lpi.org/)_.

## Requirements

### Tech Stack

-   This project will loosely tied to the certification scope but some
    technologies may be added, removed, or replaced.

-   If possible, I will try to avoid using additional libraries or
    frameworks.

-   The following technologies will be used for this project:

    -   HTML
    -   CSS
    -   JavaScript
    -   [Bulma](https://bulma.io/)
    -   [NodeJS](https://nodejs.org/)
    -   [ExpressJS](https://expressjs.com/)
    -   [SQLite](https://sqlite.org/)

-   Later, the backend portion may be replaced with
    [PocketBase](https://pocketbase.io).

### General

-   The basic structure will be similar to a typical blogging
    platform. In the end, the final product will be something like a
    simple CMS.

-   All the operations will be done from the frontend. (Ex: Managing
    users & writing posts)

-   The interface language will be English but the contents may be in
    any language.

### Users

-   There will be multiple users.

-   A username will consist of alphanumeric characters only, with the
    length of 4 to 8 characters.

-   All the user information will be stored in the database. Each user
    will take one row of `users` table, which stores user information
    and hashed passwords.

-   `users` table will have a `rowid` column to assign a unique
    identity per each row.

-   `admin` user will have a privilege to add, modify, or delete a row
    of `users` table. Each user will only be able to modify his or her
    own row of `users` table.

-   To make sure that each username is unique, `UNIQUE` constraint
    will be used when create `username` column in `users` table.

-   All the manipulations on `users` table will require username and
    password authentication.

### Authentication

-   Authentication will be implemented and performed per each
    sensitive action. (Login feature will not be necessary since only
    a few actions will require authentication.)

-   For example, when a user attempts an action requiring
    authentication, he or she will have to enter his or her username &
    password per each action.

-   Once entered, the password will be hashed by a password hashing
    tool like [OpenSSL](https://www.openssl.org/) or
    [bcrypt](https://github.com/kelektiv/node.bcrypt.js/). Then, the
    hashed password will be compared with the corresponding password
    data (also hashed) stored in `users` table.

-   The action will be performed only when the entered password
    matches the corresponding password data in `users` table.

-   All communications between the client and server will be encrypted
    using `HTTPS` for password security.

### Posts

-   All the posts a user writes will be stored in the database. Each
    post will take one row of `posts` table, which stores headers and
    contents.

-   `posts` table will have a `rowid` column to assign a unique
    identity per each row.

-   `tags` column will be added to `posts` table to enable searching
    by tags. (Since SQLite does not support array data type, I may
    have to add multiple columns for tags.)

-   When reading a post, the content will be dynamically fetched from
    the database to be displayed on a web page. (The page will be a
    kind of fixed HTML template and only the content will be
    dynamically rendered.)

-   Reading a post will not require authentication.

-   When writing/ editing/ deleting a post, the corresponding row in
    `posts` table will be added/ updated/ deleted.

-   Writing/ editing/ deleting a post will require authentication.

### Images

-   When writing or editing a post, only 1 image may be inserted. The
    image will always be located at the top of the page.

-   Only the images in `.jpg` format with the size under 1 MB will be
    accepted.

-   When uploaded, the image will be renamed as `[uername]_[rowid]`
    from the corresponding row in `posts` table. The renamed image
    will be stored in a separate directory named after each username.
    (Ex: `/images/dshin/dshin_61.jpg`) This is to ensure unique image
    names.

-   `posts` table will store only the _path_ of images.

-   When a post is fetched from the database, its corresponding image
    will also be retrieved from the directory.

### Errors

-   Error handling method should be implemented for any unsuccessful
    actions, such as invalid inputs or missing files.

## Notes

-   This is just the initial concept and will be modified as I
    continue studying.

-   It will be a long journey!
