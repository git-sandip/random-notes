Date:2023-11-01 

### Setting Up an Server

  ```js
  const express=require("express");
  const app = express();
  const port = 3000;
  app.listen(port,()=>{
  console.log(`Server has been started on https://localhost:${port}`)
  })
```

- This will start a basic express server on your localhost at port 3000

## Routing In Express

  ```js
  const express=require("express");
  const app = express();
  const port = 3000;
  // This the the basic roting or api ! When / path is hitted on browser it will 
  // respone as a hello world or we can serve a specific html or ejs file
  app.get,("/"(req,res)=>{
  res.send("Hello World")
  })
  app.listen(port,()=>{
  console.log(`Server has been started on https://localhost:${port}`)
  })
```

### Dynamic Routing


  ```js
  const express=require("express");
  const app = express();
  const port = 3000;
  app.get("/post/:id", (req, res) => {
  res.send(`Content of the url is : ${req.params.id}`);
  });
  app.listen(port,()=>{
  console.log(`Server has been started on https://localhost:${port}`)
  })
```

## Express Generator
##### Date:2023-11-01
   - Express generator is a tool that is used to quickly generate a application skeleton .
   - At First You have to install this tool globally by using following command:
   
```bash
npm install -g express-generator
```

Then you can use following command to generate an express app skeleton:
```bash
express
```
> Here it will generate the express skeleton containing view engine as pug !

But I am learning on it EJS we need to generate express app following command :
```bash
express --view=ejs
```

##### Folder Structure 

```console
.
├── app.js
├── bin
│   └── www
├── package.json
├── public
│   ├── images
│   ├── javascripts
│   └── stylesheets
│       └── style.css
├── routes
│   ├── index.js
│   └── users.js
└── views
    ├── error.ejs
    ├── index.ejs
    └── layout.ejs

7 directories, 9 files
```
