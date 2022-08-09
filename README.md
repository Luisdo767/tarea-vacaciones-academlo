// Luis David 
// users
// products
// cart 
// categories 
// orders 

table users {
  id serial [pk]
  name varchar [not null]
  email varchar [not null, unique]
  nickname varchar 
  password varchar [not null]
}

table products {
  id serial [pk]
  name varchar [not null]
  description varchar
  category_id int
}

table categories {
  id serial [pk]
  name varchar [not null]
  description varchar [not null]
}

table cart {
  id serial [pk]
  user_id int
}

table cart_products {
  id serial [pk]
  cart_id int
  product_id int 
}

table orders {
  id serial [pk]
  cart_id int
}




Ref: "categories"."id" < "products"."category_id"

Ref: "users"."id" - "cart"."user_id"

Ref: "products"."id" < "cart_products"."product_id"



Ref: "cart"."id" < "cart_products"."cart_id"

Ref: "cart"."id" > "orders"."cart_id"

link: https://dbdiagram.io/d/62f04732c2d9cf52fa60aa5e