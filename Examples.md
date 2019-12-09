# Examples

## REST vs GraphQL

1. Show user's profile screen
On the screen should be: user's first name, all user's posts, names of the last three followers

With RestAPI we would call three endpoints:
 - /users/{id}
 - /users/{id}/posts
 - /users/{id}/followers
 
 Each endpoint would return some redundant for this task information. 
 For example, last request would return response body with a list of all followers, but we require only last 3
 
 With GraphQL we'd execute only 1 endpoint:
 
 ```text
{
  user(id: "op24hbh34hb") {
    name
    post {
      title
    }
    followers(last: 3) {
      name
    }
  }
}
```
This will return the body with the specified fields.


## Mutations

- with aliases 

Aliases allow us to give the field a customized name and to request data from the same fields with different arguments.

*update1* and *update2* are aliases
```text
mutation {
  update1: updateUser(name: "David Schwimmer", id: "ck1tt4wwz0njc0140bp5aob0j"){
    name
    id
    createdAt
  }
  update2: updateUser(name: "Kevin S. Bright", id: "ck1tt4a6x0ndc0199osuvl7cb"){
    name
    id
  }
}


{
  "data": {
    "update1": {
      "name": "David Schwimmer",
      "id": "ck1tt4wwz0njc0140bp5aob0j",
      "createdAt": "2019-10-16T21:48:41.000Z"
    },
    "update2": {
      "name": "Kevin S. Bright",
      "id": "ck1tt4a6x0ndc0199osuvl7cb"
    }
  }
}
```

- with fragments

Fragments are reusable sets of fields that can be included in queries as needed. 

```text
mutation {
  update1: updateUser(name: "David Schwimmer", id: "ck1tt4wwz0njc0140bp5aob0j"){
    ...updateUser
  }
  update2: updateUser(name: "Kevin S. Bright", id: "ck1tt4a6x0ndc0199osuvl7cb"){
    ...updateUser
  }
}

fragment updateUser on User {
  name
  id
  createdAt
}
```