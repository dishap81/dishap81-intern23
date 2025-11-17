README – Simple REST API for Managing Books

Internship Task – Node.js & Express

📌 Project Overview

This project is a simple REST API built using Node.js and Express to manage a list of books.
The API supports CRUD operations without any database — all data is stored in memory.

This project demonstrates understanding of:

Express Routing

HTTP Methods

JSON handling

REST API Basics



---

📁 Project Structure

project-folder/
│
├── app.js        # Main server file (API code)
├── package.json  # Project configuration & dependencies
└── node_modules/ # Installed dependencies


---

🚀 How to Run the Project

1. Install dependencies

npm install express

2. Start the server

node app.js

✔️ You should see:

Server running on port 3000

The API is now running at:

http://localhost:3000


---

🛠️ API Endpoints

✅ 1. GET all books

GET /books

Returns the list of all books.


---

✅ 2. POST a new book

POST /books

Body (JSON):

{
  "title": "Sample Book",
  "author": "Author Name"
}

Adds a new book to the list.


---

✅ 3. PUT - Update a book

PUT /books/:id

Body (JSON):

{
  "title": "Updated Title",
  "author": "Updated Author"
}

Updates the book with the given ID.


---

✅ 4. DELETE - Remove a book

DELETE /books/:id

Deletes the book with the given ID.


---

📦 Same Code Used (for reference)

This is the full working API code in app.js:

const express = require("express");
const app = express();

app.use(express.json());

// In-memory books array
let books = [
  { id: 1, title: "Book One", author: "Author A" },
  { id: 2, title: "Book Two", author: "Author B" }
];

// GET all books
app.get("/books", (req, res) => {
  res.json(books);
});

// POST a new book
app.post("/books", (req, res) => {
  const newBook = {
    id: books.length + 1,
    title: req.body.title,
    author: req.body.author
  };
  books.push(newBook);
  res.json({ message: "Book added", book: newBook });
});

// PUT update a book by ID
app.put("/books/:id", (req, res) => {
  const id = parseInt(req.params.id);
  const book = books.find(b => b.id === id);

  if (!book) return res.status(404).json({ message: "Book not found" });

  book.title = req.body.title || book.title;
  book.author = req.body.author || book.author;

  res.json({ message: "Book updated", book });
});

// DELETE a book by ID
app.delete("/books/:id", (req, res) => {
  const id = parseInt(req.params.id);
  books = books.filter(b => b.id !== id);
  res.json({ message: "Book deleted" });
});

// Start server
app.listen(3000, () => {
  console.log("Server running on port 3000");
});


---

🎯 Conclusion

This project successfully meets all requirements:

✔ Simple
✔ Beginner-friendly
✔ Fully working REST API
✔ No database needed
✔ Perfect for internship submission# dishap81-intern23
