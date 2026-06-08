# AI Fix Summary

## Error
POST /students failed

## Analysis
The bug is crystal clear. Here is the complete analysis:

---

**Root cause:** In `StudentForm.js` line 41, `addStudent()` is called **with no arguments**. The `addStudent` function in `App.js` (line 56) expects a `student` object to be passed and serializes it as the POST body. Calling it with no argument means `student` is `undefined`, so `JSON.stringify(undefined)` produces nothing — the POST body sent to the backend is empty (`{}`), giving SQLite `null` for `Name`, `Age`, and `Email`, which 
