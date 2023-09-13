 # Mock eCommerce
Mock Ecommerce

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
