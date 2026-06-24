# AI Fix Summary

## Error
POST /students failed

## Analysis
The root cause is fully confirmed. The exact bad line is `StudentForm.js:41`:

```js
addStudent();   // ← student object never passed
```

`App.js:addStudent(student)` receives `undefined`, so `JSON.stringify(undefined)` produces no body at all. The server receives `{}`, destructures `name/age/email` as `undefined`, and SQLite throws a `NOT NULL` constraint error on `Name`, `Age`, and `Email` columns.

The fix is to pass `student` to `addStudent()` on that line:

```json
{"root_cause":"In Studen
