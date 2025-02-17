# Requirements

The intent is to create a website where-by a library, or book store can show off their catalog along with reviews and images. 

- [ ] Database of Books
- [ ] Sorted by Categories
- [ ] Reviews and Images from a Public API
- [ ] Bootstrap For Styling
- [ ] Admin User Creation and Login, tutorial [here](https://www.youtube.com/watch?v=Nlg0JrUt0qg).
## Bonus

- [ ] User Profile
- [ ] User Reviews
- [ ] User Ratings
- [ ] Cart Functionality
- [ ] Newsletter
# Research

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

![](Pictures/Front%20Page.png)
