In a typical Express.js application, as it grows in complexity, you might want to organize your routes into separate files or folders to maintain a clean and modular code structure. This can be achieved using the `express.Router` middleware. Here's a step-by-step guide on how you can implement routing in separate folders:

Assuming you have a basic Express application:

1. **Create a `routes` folder:**
    
    In your project directory, create a folder named `routes`. This folder will contain your route modules.
    
```js
/your-express-app
├── node_modules
├── routes
├── views
├── public
├── app.js
└── package.json
```
    
2. **Create a route module:**
    
    Inside the `routes` folder, create a new JavaScript file for each set of routes. For example, you might have a `userRoutes.js` for user-related routes:
    
```js
const express = require('express');
const router = express.Router();

// Define routes for users
router.get('/', (req, res) => {
  res.send('User home page');
});

router.get('/profile', (req, res) => {
  res.send('User profile page');
});

// Export the router
module.exports = router;
```
    
3. **Use the router in your main app file:**
    
    In your main Express application file (e.g., `app.js`), require the route modules and use them with the `app.use()` method:
    
```js
   // app.js
const express = require('express');
const app = express();

// Require route modules
const userRoutes = require('./routes/userRoutes');

// Use route modules
app.use('/users', userRoutes);

// Start the server
const PORT = process.env.PORT || 3000;
app.listen(PORT, () => {
  console.log(`Server is running on port ${PORT}`);
});

```
    
    In this example, all routes defined in `userRoutes.js` will be prefixed with `/users`.
    
4. **Repeat for other route modules:**
    
    Create additional route modules for different parts of your application as needed. Each module should export an instance of `express.Router()`.
    
```js
   // routes/productRoutes.js
const express = require('express');
const router = express.Router();

// Define routes for products
router.get('/', (req, res) => {
  res.send('Product home page');
});

router.get('/details', (req, res) => {
  res.send('Product details page');
});

// Export the router
module.exports = router;
```
    
    Then, in `app.js`, you would use it like this:
    
```js
   const productRoutes = require('./routes/productRoutes');
app.use('/products', productRoutes);
```
    

Now, your routes are organized into separate files and folders, making your Express application more modular and maintainable.