## GraphQL

a domain specific typed language to design and query data.

Features:

1. it's a query language for APIs 
2. it enables declarative data fetching where a client can specify exactly what data it needs from an API
3. it minimizes the amount of data that needs to be transferred over the network
4. helps to solve problem of over- and under-fetching

### The Schema Definition Language (SDL)

<table>
    <tr>
        <td align=center colspan=3><b>Defining simple types</b></td>
    </tr>
    <tr>
        <td>
        <pre>
  type Person {
    name: String!
    age: Int!
  }
        </pre>
        </td>
        <td align=top>
        <pre>
  type Post {
    title: String!
  }
        </pre>
        </td>
        <td>Notes: ! - field is required; </td>
    </tr>
    <tr>
        <td align=center colspan=3><b>Adding relation</b></td>
    </tr>
    <tr>
        <td>
        <pre>
  type Person {
    name: String!
    age: Int!
    posts: [Post!]!
  }
        </pre>
        </td>
        <td>
        <pre>
  type Post {
    title: String!
    author: Person!
  }
        </pre>
        </td>
        <td>Notes: One person can be an author of many posts </td>
    </tr>
</table>

![1-to-many relation](relation.png)

### Fetching data with queries

![query example](fetching_data_with_queries.png)

### Writing data with mutations

1. creating new data
2. updating existing data
3. deleting existing data

Examples:

<table>
    <tr>
        <td align=center colspan=2><b>Update existing data</b></td>
    </tr>
    <tr>
        <td>
        <pre>
  mutation {
    updateUser(name: "Paul Rudd", 
        id: "ck2cqj2lm04h40102u8du1u92"){
        name
        id
    }
  }
        </pre>
        </td>
        <td>
        <pre>
  {
    "data": {
        "updateUser": {
            "name": "Paul Rudd",
            "id": "ck2cqj2lm04h40102u8du1u92"
        }
    }
  }
        </pre>
        </td>
    </tr>
    <tr>
        <td align=center colspan=3><b>Delete existing user</b></td>
    </tr>
    <tr>
        <td>
        <pre>
  mutation {
    deleteUser(id:"ck3pu3jt10qdf0117eznh7ngg"){
        id
    }
  }
        </pre>
        </td>
        <td>
        <pre>
  {
  "data": {
    "deleteUser": {
      "id": "ck3pu3jt10qdf0117eznh7ngg"
    }
  }
}
        </pre>
        </td>
    </tr>
</table>


### Useful links

- learn about GraphQL
    https://developer.github.com/v4/#about-graphql

- practice GraphQL online
    https://developer.github.com/v4/explorer/
    https://lucasconstantino.github.io/graphiql-online/
    http://graphql.nodaljs.com/
    https://www.graphql.college/practice-graphql/
    
#### Tutorials

https://www.howtographql.com/
https://www.linkedin.com/learning/learning-graphql

    


