# Secured GraphQL API using Graphql-Shield & JWT

### How to run ?
```
$ npm i
$ npm run server
```

### How to use ?

- Navigate to [http://localhost:4000/graphql](http://localhost:4000/graphql)

- Try to login using mutation :

```
mutation {
  login(email: "test@test.gov", password: "test")
}
```

It should return : Not authorised !

Now try : 
```
mutation {
  login(email: "neil@nasa.gov", password: "password890!")
}
```

It should return a jwt token.


- Copy & paste that token in "HTTP Headers" like this :

```
{
  "Authorization": "Bearer TOKEN"
}
```

- Try to get user informations using :
```
query {
  user(id: "12345") {
    name
  }
}
```

It should return : "Not authorised !" 

```
query {
  user(id: "67890") {
    name
  }
}
```

It should return : "Neil Armstrong"
