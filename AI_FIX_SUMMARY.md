# AI Fix Summary

## Error
POST /students failed: NOT NULL constraint failed: StudentFees.Name
SqliteError: NOT NULL constraint failed: StudentFees.Name
    at C:\V2\student-crud-logger\backend\routes\students.js:42:8
    at Layer.handle [as handle_request] (C:\V2\student-crud-logger\backend\node_modules\express\lib\router\layer.js:95:5)
    at next (C:\V2\student-crud-logger\backend\node_mod

## Analysis
The root cause is now clear. I have everything I need.

**Root cause:** In `StudentForm.js` line 41, `addStudent()` is called with **no arguments** — `addStudent()` — instead of `addStudent(student)`. The `student` object is built on lines 29–35 but never passed to the function. This means `App.js`'s `addStudent` receives `undefined` as the body, so the POST request sends `{}` to the backend, which then has no `name` field — triggering SQLite's `NOT NULL constraint failed: StudentFees.Name`.

**
