# Requirements

The intent is to create a website where-by a library, or book store can show off their catalog along with reviews and images. 

- [x] Database of Books
- [x] Sorted by Categories
- [x] Reviews and Images from a Public API
- [x] Admin User Creation and Login, tutorial [here](https://www.youtube.com/watch?v=Nlg0JrUt0qg).
## Bonus

- [x] User Profile
- [x] User Reviews
- [x] User Ratings
- [x] Cart Functionality
- [x] Newsletter
- [x] Breadcrumb For Book Links
- [x] User Management Panel
- [x] Logging
- [ ] Add Orders Tables
- [ ] Add Sold Table
- [ ] Add Panel to Mark Orders as Completed
- [ ] Add Panel for Users to Track Orders
- [ ] Style Website
## Bugs

- [ ] Logging in redirects to home instead of the last page accessed.
## Issues

1. Multiple Roles is not Implemented Correctly. Fundamental Design Flaw in How Records are Updated and Included.
2. Components That React to User Interaction Should not be Rendered Server Side
3. Communication Between Models can be Improved, Possibly with the User of Interfaces
4. Cart is Missing Features (Delete, Checkout)
# Research

Useful links and resources.
## Book API Endpoints

- [Open Library](https://openlibrary.org/developers/api)
- [Google Books](https://developers.google.com/books)
## How are Books Identified Online?

- ISBN Numbers?
# Database Structure

- Administrator Database
	- Username
	- Email Address
	- Password
	- Role

- Book Database
	- Title
	- Author
	- Publish Year
	- Category
	- Abstract
	- Cover ID
	- Quantity
	- Price
# Scratch Pad

Space to brainstorm and map out ideas.
## DB Object Structure

```json
{
    id: 3,
    title: 'The Hobbit',
    author: 'J.R.R. Tolkien',
    category: 'Fantasy',
    publish_year: 1937,
    abstract: "Bla bla bla long abstract text etc fdklsjfdklsjf ...",
    cover_id: 14627509,
    quantity: 10,
    price: '299.99'
  }
```
## Basic Book Adding Flow

![](Pictures/Book%20Add%20Flow.png)

## Layout Ideas
### Main Page:

Front-end To-do:
- [x] Finish Footer
- [ ] Fold Navbar
- [x] Unsticky Navbar at Mobile Height
- [x] Create Routes to Book Pages
- [x] Categories as Filters not Links
![](Pictures/Front%20Page.png)
### Footer Design

![](Pictures/Footer%20Design.png)

### Book View:

Book View To-do:

- [x] Assign Routes to Each Book
	- [x] Add Route to Index.js
	- [x] Create View EJS File
	- [x] Pass Book info to Route
	- [x] Render EJS File with Book Info
- [x] Render Large Cover
- [x] Create CSS File For Card

![](Pictures/Book%20View.png)

### User Reviews:

![](Pictures/User%20Reviews%20Design.png)

## Cart

Cart To-do:
- [x] Add Model to Database
- [x] Add "Add to Cart" Button to Book View
- [x] Create Post Route to Insert Book Data into Carts Database
- [x] Add Cart Tab to Navbar for Logged in Users
- [x] Show Amount of Items in Cart in Navbar
- [x] Create "Cart" View with Table of Items in Cart

Cart Logic

- Cart Object
	- Foreign Keys Linked to Items Purchased
	- When Clicking Place Order, Convert Cart Object to Order Object
## Newsletter

Users can subscribe to the newsletter where they will receive notifications for new books.

**Bonus**: Add Notify by Category
### Database Structure

The database should be 3rd normal form.

| id  | user_id | email               | name |
| --- | ------- | ------------------- | ---- |
| 4   | 14      | sinsmailza@gmai.com | sins |

Email and Name are referencing the *Users* table and so they will need to copy the information. `user_id` is a *Foreign Key* to the *Users* table.

## Orders

Orders will need 1. an *Orders* table and 2. a *Sold* table. The mailer class can can be used to send the user an email when their order has been placed and when the sale is marked as complete by an administrator the user can receive an email after a month to be reminded to review the book on the web-page. When sales are completed they should reduce the amount of available books from the catalog and the entry should be deleted in the catalog when there are no more remaining.

The *Orders* table should make reference to the users table as well as the books table. It should also track the progress of an order such as "Placed", "Delivery" and "Complete".

**Problem**: If a book is removed from the catalog it will also be removed from this table. Hmm.. Maybe When being displayed it should join info from the *Sold* table instead of being a *Foreign Key*.

| id  | user_id | email           | book_id | book_title       | order_status | payment_status |
| --- | ------- | --------------- | ------- | ---------------- | ------------ | -------------- |
| 1   | 3       | fella@fella.com | 5       | The Great Gatsby | Placed       | Pending        |
| 2   | 4       | cool@cool.com   | 2       | Willy Wonka      | Complete     | Paid           |
`email` and `user_id` reference the *Users* table, `user_id` will be a *Foreign Key*. `book_id` and `book_title` reference the *Books* table, `book_id` will be a *Foreign Key.*

The *Sold* or *Sales* table will have no relational data and only handle logging past events so that when orders are completed the information can be examined at a later date if necessary.