# AI Fix Summary

## Error
POST /students failed

## Analysis
The root cause is crystal clear. In `StudentForm.js` at line 41, `addStudent()` is called **without passing the `student` object** as an argument. The `student` variable is built on lines 29–35, but the call on line 41 passes nothing — so `App.js`'s `addStudent(student)` receives `undefined`, `JSON.stringify(undefined)` produces nothing useful, and the backend's `INSERT` gets `null`/`undefined` values for the `NOT NULL` columns (`Name`, `Age`, `Email`), causing the `SqliteError`.

```
// App.js 
