# AI Fix Summary

## Error
Failed to add student

## Analysis
The root cause is confirmed. In `StudentForm.js` line 41, `addStudent()` is called with **no arguments** — the `student` object constructed just above is never passed. This means the POST body sent to the backend is `{}`, so `name`, `age`, and `email` are all `undefined`, causing the SQLite `NOT NULL` constraint to fail, which throws an error caught by the `.catch` in `App.js` that logs `"Failed to add student"`.

The fix is a one-word change: pass `student` to `addStudent()`.

```json
{"root_ca
