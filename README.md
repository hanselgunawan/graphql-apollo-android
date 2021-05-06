# GraphQL + Apollo Android

## GraphQL
GraphQL is a **query language** for your API. 

### What is Query Language?
One of the well-known examples is **Structured Query Language (SQL)**.
Example:
```
SELECT name FROM users
```
It will grab `name` from a table called `users` from database.

### How Does a Query Look like in GraphQL?
```
query UserList {
  user {
    name
    phone_number
  }
}
```
`user` is the object that we want to grab.

### Keywords

**[OPERATION TYPE]**
* Query: we use this to get information back from the server.
* Mutation: we use this if we want to change some data.
* Subscription: we use this to find out / listen to changes.

**[OPERATION NAME]**

If we see at the example above, `UserList` is an operation name.

## GraphQL vs REST API

* `query` in GraphQL = `GET` request in REST
* `mutation` = `POST`,`PUT`,`PATCH`,`DELETE` in REST

## GraphQL is a Specification
GraphQL is language agnostic. It was developed by [Facebook](http://spec.graphql.org/draft/). Language agnostic means it can be written in multiple languages, such as JavaScript, Kotlin, Perl, Python, Ruby, Java, C++, C#, Scala, Go, Rust, Elixir, Erlang, PHP, R, D and Clojure.

## GraphQL is Introspective
GraphQL type system should be able to be queried by GraphQL itself.
For example:
```
query {
  __type(name: "User") {
    fields {
      name
    }
  }
}
```

## Why is REST so painful?
For example, we call `users` endpoint with REST API, we'll get something like this:
```
{
  "ID": 1,
  "First Name": "Hansel",
  "Last Name": "Tritama",
  "Phone Number": "123-234-3456"
},
{
  "ID": 2,
  "First Name": "Thomas",
  "Last Name": "Enstein",
  "Phone Number": "123-234-3456"
}
```
What if we just want to grab the `Phone Number` field? That will require more work!

**BUT** with `GraphQL`, we only get what we ask for!

## GraphQL Server
Any GraphQL Server is made up by:

* Types
* Schema
* Resolvers

### Types
```
type User {
  id: Int! // can't be nullable (required)
  firstName: String,
  lastName: String,
  ssn: String
}
```

## GraphQL Endpoint
`/graphql`. That's it!

## GraphQL Client
It's made up by:

* Apollo Client
* Schema
* .graphql Files

### Apollo Client
To setup:
```
ApolloClient.builder()
  .serverURL(BASE_URL)
  .okHttpClient(okHttpClient)
  .build()
```

### Download the Schema
```
apollo-codegen download-schema
```

### `.graphql` File
This is where we put our queries -> rebuild the project -> the plugin will auto-generate Kotlin/Java files for us.
Generated code will contain `Query` at its file name.

## Useful Plugins

### IntelliJ GraphQL Plugin

<img src="https://user-images.githubusercontent.com/10084360/116491028-c1110b80-a84d-11eb-8767-5d319cb5b60c.png">

### Public GraphQL APIs
[Public GraphQL APIs](https://github.com/APIs-guru/graphql-apis)

### Schema Cheat Sheet
[Schema Cheat Sheet](https://wehavefaces.net/graphql-shorthand-notation-cheatsheet-17cd715861b6)

## Demo
<img src="https://user-images.githubusercontent.com/10084360/116381875-27ece100-a7ca-11eb-99d3-81cab3a6da8f.gif" width="350px" height="650px" />
