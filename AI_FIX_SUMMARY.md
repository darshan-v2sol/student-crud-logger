# AI Fix Summary

## Error
POST /students failed

## Analysis
**Found it!** Look at `StudentForm.js` line 44:

```js
// student
addStudent();
```

The `addStudent()` function is called **with no arguments** — the `student` object that was carefully constructed on lines 32–38 is never passed! Meanwhile, `App.js`'s `addStudent` function accepts a `student` parameter and sends `JSON.stringify(student)` to the API. With no argument, `student` is `undefined`, so `JSON.stringify(undefined)` sends nothing, and the backend receives `{}` — meaning `name`, `age`, an
