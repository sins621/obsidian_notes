# Requirements

The intent is to create a website where-by a library, or book store can show off their catalog along with reviews and images. 

- [x] Database of Books
- [x] Sorted by Categories
- [x] Reviews and Images from a Public API
- [x] Admin User Creation and Login, tutorial [here](https://www.youtube.com/watch?v=Nlg0JrUt0qg).
## Bonus

- [ ] User Profile
	- [ ] View Purchase History
	- [ ] Add Panel for Users to Track Orders
	- [ ] View Reviews
- [x] User Reviews
- [x] User Ratings
- [x] Cart Functionality
- [x] Newsletter
	- [x] Ability to Sign up in Footer
- [x] Breadcrumb For Book Links
- [ ] User Management Panel
	- [ ] View User's Roles
		- [x] Fetch All Users
		- [ ] Display a Single User with Radio Buttons or Drop-down With Radio Buttons with Roles
			- [ ] Allow Multi-Selection of Roles
			- [ ] Include All Roles
			- [ ] Set Roles a User Has to Checked
	- [ ] Delete Users
	- [ ] Manually Add Users
- [ ] Logging
- [ ] Add Orders Tables
	- [ ] Users Need to be Able to Checkout Their Carts
- [ ] Add Sold Table
	- [ ] Administrator's Need to Be Able to Update Order Status
		- [ ] Orders Panel
- [ ] Add Panel to Mark Orders as Completed
- [ ] Refine `databaseService.js` error handling.
- [ ] Style Website
- [ ] Add Visual Indicators to Respond to User Actions that Don't Change the Page State
	- [ ] Signing up to the Newsletter
- [ ] Implement a Solution to Increase Image Load Times
## Bugs

- [ ] Logging in redirects to home instead of the last page accessed.
## Issues

1. Multiple Roles is not Implemented Correctly. Fundamental Design Flaw in How Records are Updated and Included.
2. ~~Components That React to User Interaction Should not be *Only* be Rendered Server Side. They Must be Reproduced in Raw JavaScript~~
3. ~~Communication Between Models can be Improved, Possibly with the User of Interfaces~~ Existing Models Refactored in To Services and Project Moved to an MVC Framework
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
# Operation Fix

Issues that need to be solved before I can move on without going insane.

- [ ] ONLY use ejs for static elements when rendering routes.
- [ ] Use ejs to render 'components' and update these components with Ajax queries.
- [ ] Fetch categories from the server instead of them being pulled from a constant.
- [ ] Investigate express() routers.
- [ ] Protect API calls with cookies?
## Non-static EJS.

The following routes are using ejs for non-static elements and need to be fixed:

- [x] Home
- [x] Book View
- [x] Reviews
- [ ] User-Panel
- [ ] Cart
### Home

Currently books are pulled in and sorted from the backend. Maybe the entire books grid can be rendered ejs from the back-end?
### Book View:

The book card is rendered from the backend, this will complicate adding cart icons dynamically.

**NOTE TO SELF**: You can only access the `response.text()` property on a `fetch()` query **ONCE** lmaooooooo.
### Reviews.

Iirc the review component is one piece with the entree field and reviews itself. Split reviews into a api call to a rendered ejs file which queries the backend and have the review addition field be it's own thing.

- [x] Adding reviews as manual post requests instead of forms.
- [x] Fetching all reviews as get requests instead of server side rendering.
### User panel.

Table is rendered from the back-end requiring full page refreshes when deleting users. Instead, server this from an api.
### Cart

Same limitations as the user panel.
## Components as API calls.

Instead of building EJS for components when the page is called, server them via an API so that they can be refreshed when other tasks are done. For example:

```javascript
async function addToCart(userId, bookId) {
    console.log("updating cart");
    const RESPONSE = await fetch("/add_cart", {
      method: "POST",
      headers: {
        "Content-Type": "application/json"
      },
      body: JSON.stringify({
        book_id: bookId,
        user_id: userId,
      })
    });
    if (RESPONSE.status === 200) {
      await updateCart(
        userId); // Ensure the cart updates only after the request succeeds
    } else {
      console.error("Failed to add to cart:", RESPONSE.status);
    }
  }
```

This function calls `updateCart()` after the item has been successfully added to the cart. This updates the cart size number dynamically without needing a full page refresh.

```javascript
const cartNum = document.getElementById("cart-size");
  <% if (locals.user) { %>
  const userId = <%= user.id %>;
  updateCart(userId, cartNum);
  <% } %>

  async function updateCart(userId) {
    const QUERY = await fetch(`/fetch_cart_size?user_id=${userId}`)
    const CART_SIZE = await QUERY.json();
    cartNum.innerHTML = CART_SIZE.cart_size;
    console.log(CART_SIZE)
  }
```

**NOTE**: This approach ==does not work==. Scripts not present when the page is pulled in via Template.
## Category Sorting

No idea bra. Never mind I'm cracked
## Express Routers

Maybe express routers is the solution to splitting up the project into different files?
## Protect API Calls.

Test if `req.user.isAuthenticated()` can be used to protect endpoints. 

This does not seem to work. That's because it's actually `req.isAuthenticated()`. Nice one dude.