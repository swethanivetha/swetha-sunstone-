const express = require('express');
const bodyParser = require('body-parser');
const mongoose = require('mongoose');

const app = express();
const PORT = 3000;

// Middleware to parse incoming request body as JSON
app.use(bodyParser.json());

// Connect to MongoDB database
mongoose.connect('mongodb://localhost/social-media-app', {
  useNewUrlParser: true,
  useUnifiedTopology: true,
  useCreateIndex: true,
});

// Define Post schema
const postSchema = new mongoose.Schema({
  text: String,
});

// Define Post model
const Post = mongoose.model('Post', postSchema);

// Route to get all existing posts
app.get('/api/posts', async (req, res) => {
  try {
    const posts = await Post.find({});
    res.json(posts);
  } catch (error) {
    console.log(error);
    res.status(500).send('Internal Server Error');
  }
});

// Route to create a new post
app.post('/api/posts', async (req, res) => {
  try {
    const { text } = req.body;
    const newPost = new Post({ text });
    await newPost.save();
    res.status(201).json(newPost);
  } catch (error) {
    console.log(error);
    res.status(500).send('Internal Server Error');
  }
});

// Start the server
app.listen(PORT, () => {
  console.log(`Server listening on port ${PORT}`);
});