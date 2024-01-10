const express = require('express');
const bodyParser = require('body-parser');
const app = express();
const port = 3000;

// In-memory database (replace with a real database in a production environment)
let thoughts = [];

app.use(bodyParser.json());
app.use(bodyParser.urlencoded({ extended: true }));

// Serve static files (front-end)
app.use(express.static('public'));

// API endpoint to get thoughts
app.get('/api/thoughts', (req, res) => {
  res.json(thoughts);
});

// API endpoint to add a thought
app.post('/api/thoughts', (req, res) => {
  const thought = req.body.thought;
  if (thought.trim() !== '') {
    const date = new Date().toLocaleDateString();
    const newThought = { date, thought };
    thoughts.push(newThought);
    res.json(newThought);
  } else {
    res.status(400).json({ error: 'Invalid thought input' });
  }
});

app.listen(port, () => {
  console.log(`Server listening at http://localhost:${port}`);
});
