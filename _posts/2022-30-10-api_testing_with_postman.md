---
layout: post
title:  "API Testing with Postman"
date:   2022-30-10 20:54:37 +0530
categories: postman
---

## API Testing with Postman

* GET, POST, PATCH, DELETE
* Variables
* Test
* Collection Runner 
* Postman Monitors 

```javascript
//GET Api Status

pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();
console.log(response.status);
console.log(response["status"])

pm.test("Status should be ok", () => {
    pm.expect(response.status).to.eql("OK");
})

postman.setNextRequest("List of books");

//GET List of Books
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

const response = pm.response.json();
const nonFictionBooks = response.filter((book) => book.available === true);

const book = nonFictionBooks[0];

if(book){
    pm.globals.set("bookId", nonFictionBooks[0].id);
}

pm.test("book found", ()=> {
    pm.expect(book).to.be.an('object');
    pm.expect(book.available).to.be.true;
});

//POST Ordre book
pm.test("Status code is 201", function () {
    pm.response.to.have.status(201);
});

const response = pm.response.json();
pm.globals.set("orderid", response.orderId);
```

<iframe width="560" height="315" src="https://www.youtube.com/embed/VywxIQ2ZXw4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

https://www.youtube.com/watch?v=VywxIQ2ZXw4


                                   
                                  
                                  
