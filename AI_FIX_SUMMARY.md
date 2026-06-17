# AI Fix Summary

## Error
Failed to add student: Add failed
Error: Add failed
    at http://localhost:3000/static/js/bundle.js:97:26

## Analysis
Found it. The bug is on **line 41** of `frontend/src/components/StudentForm.js`.

**Root cause:** `addStudent()` is called with **no arguments** — the `student` object constructed just above (lines 29–35) is never passed to it. When `App.js`'s `addStudent` receives `undefined` as the body, the `POST` to the backend sends `{}`, which causes the DB insert to fail, the server returns a non-2xx status, and the `.catch` in `App.js` fires with `"Add failed"`.

```
StudentForm.js:41  addStudent();     
