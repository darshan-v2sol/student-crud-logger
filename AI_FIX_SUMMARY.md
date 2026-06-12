# AI Fix Summary

## Error
Failed to add student: Add failed
Error: Add failed
    at http://localhost:3000/static/js/bundle.js:97:26

## Analysis
In src/App.js the addStudent catch block discards the real caught error (a JSONError from response.json() receiving a non-JSON server response) and rethrows a new generic Error('Add failed'), hiding the true cause
