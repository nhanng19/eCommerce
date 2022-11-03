 # 13_E_Commerce_Back_End_NN
BootCamp Homework - 13 Object-Relational Mapping (ORM): E-Commerce Back End

## The Challenge
Internet retail, also known as e-commerce, is the largest sector of the electronics industry, generating an estimated $29 trillion in 2019. E-commerce platforms like Shopify and WooCommerce provide a suite of services to businesses of all sizes. Due to their prevalence, understanding the fundamental architecture of these platforms will benefit us as a full-stack web developer.
Our task is to build the back end for an e-commerce site by modifying starter code. We'll configure a working Express.js API to use Sequelize to interact with a MySQL database.


## Installation

Before running the application, insert database by running the following commands in the MySQL shell (make sure navigation is in the root directory):

```bash
SOURCE db/schema.sql;
```

Inser custom seeds before starting the server (make sure navigation is in the root directory):

```bash
npm run seed
```

Install node dependencies by running the following command (make sure navigation is in the root directory):

```bash
npm i
```

The application will be invoked by using the following command (make sure navigation is in the root directory):

```bash
npm start
```

[WALKTHROUGH VIDEO HERE](https://drive.google.com/file/d/19__uROFSFop7FS21-rJojSXum1_vC54E/view)

## User Story

```
AS A manager at an internet retail company
I WANT a back end for my e-commerce website that uses the latest technologies
SO THAT my company can compete with other e-commerce companies
```

## Acceptance Criteria

```
GIVEN a functional Express.js API
WHEN I add my database name, MySQL username, and MySQL password to an environment variable file
THEN I am able to connect to a database using Sequelize
WHEN I enter schema and seed commands
THEN a development database is created and is seeded with test data
WHEN I enter the command to invoke the application
THEN my server is started and the Sequelize models are synced to the MySQL database
WHEN I open API GET routes in Insomnia for categories, products, or tags
THEN the data for each of these routes is displayed in a formatted JSON
WHEN I test API POST, PUT, and DELETE routes in Insomnia
THEN I am able to successfully create, update, and delete data in my database
``` 

## The Process
To satisfy the criteria, we had to:
- Install inquirer package
- Install path package
- Define properties for each models
- 

Model Association:

```javascript
const Product = require('./Product');
const Category = require('./Category');
const Tag = require('./Tag');
const ProductTag = require('./ProductTag');

// Products belongsTo Category

Product.belongsTo(Category, {
  foreignKey: "category_id",
  onDelete: "CASCADE"
});

// Categories have many Products

Category.hasMany(Product, {
  foreignKey: 'category_id'
});

// Products belongToMany Tags (through ProductTag)

Product.belongsToMany(Tag, {
  through: ProductTag,
  foreignKey: 'product_id'
});

// Tags belongToMany Products (through ProductTag)

Tag.belongsToMany(Product, {
  through: ProductTag,
  foreignKey: 'tag_id'
})

module.exports = {
  Product,
  Category,
  Tag,
  ProductTag,
};

```

## The Result
Using insomnia, we can send GET requests to retrieve products, tags, and categories individually and collectively. We can also create new products, tags and categories with our POST requests, as well as update them with our PUT requests. If we choose so, we can also remove products, tags, or categories with our DELETE requests.

## Submission
This project was uploaded to GitHub at the following repository link:
[https://github.com/nhanng19/eCommerce](https://github.com/nhanng19/eCommerce)

Walkthrough Video Link:
[https://drive.google.com/file/d/19__uROFSFop7FS21-rJojSXum1_vC54E/view](https://drive.google.com/file/d/19__uROFSFop7FS21-rJojSXum1_vC54E/view)