const express = require('express');
const bodyParser = require('body-parser');

const app = express();
const PORT = 3000;

// Middleware to parse incoming request body as JSON
app.use(bodyParser.json());

// In-memory database for simplicity
let posts = [];

// Route to get all existing posts
app.get('/api/posts', (req, res) => {
  res.json(posts);
});

// Route to create a new post
app.post('/api/posts', (req, res) => {
  const { text } = req.body;
  const newPost = { text };
  posts.push(newPost);
  res.status(201).json(newPost);
});

// Start the server
app.listen(PORT, () => {
  console.log(`Server listening on port ${PORT}`);
});