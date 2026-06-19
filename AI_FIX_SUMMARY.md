# AI Fix Summary

## Error
POST /students failed

## Analysis
Found it. The bug is right there in `StudentForm.js` line 43:

```js
addStudent();  // called with NO argument
```

But in `App.js`, `addStudent(student)` expects the `student` object to be passed. When `addStudent()` is called with no argument, `student` is `undefined`, so `JSON.stringify(undefined)` produces `undefined` (not a string), which means the `fetch` POST body is empty/undefined — the backend receives `{}`, so `name`, `age`, `email` are all `undefined`, causing the SQLite `NOT NULL` c
