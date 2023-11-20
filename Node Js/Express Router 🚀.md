



```js
const express = require("express");
const app = express();
const router = require("./routes/auth.router.js");
const PORT = 3000;
app.use("/api/auth", router);
app.listen(PORT, () => {
console.log(`Server has been started on https://localhost:${PORT}`);
});
```
