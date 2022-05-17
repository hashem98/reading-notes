
# Add relationships between types

 * `@connection` directive enables you to specify relationships between `@model` types


1. Definition
   `directive @connection(keyName: String, fields: [String!]) on FIELD_DEFINITION
   `

2. one-to-one connection 
   ```
   type Project @model {
     id: ID!
     name: String
     team: Team @connection
   }
   
   type Team @model {
     id: ID!
     name: String!
   }
   ```
   * define the field you would like to use for the connection by populating the first argument to the fields array and matching it to a field on the type
   add to project `team: Team @connection(fields: ["teamID"])`

   * create projects and query the connected team 

 ```
   mutation CreateProject {
     createProject(input: { name: "New Project",    teamID: "a-team-id"}) {
       id
       name
       team {
         id
         name
       }
     }
   }
 ```
3. one-to-many connection

  ```
  type Post @model {
  id: ID!
  title: String!
  comments: [Comment] @connection(keyName: "byPost", fields: ["id"])
   }

  type Comment @model
  @key(name: "byPost", fields: ["postID", "content"]) {
  id: ID!
  postID: ID!
  content: String!
  }
  ```
   *  create comments and query the connected Post then query a Post with its comments


   * we can make a connection bi-directional by adding a many-to-one connection to types that already have a one-to-many connection. In this case you add a connection from Comment to Post since each comment belongs to a post
   ```
   type Post @model {
   id: ID!
   title: String!
   comments: [Comment] @connection(keyName:  "byPost", fields: ["id"])
   }

  type Comment @model
  @key(name: "byPost", fields: ["postID", "content"]) {
  id: ID!
  postID: ID!
  content: String!
  post: Post @connection(fields: ["postID"])
  }
   ```
  then create comments with a post, query a Comment with its Post, then all Comments of that Post by navigating the connection

  
4. Many-to-many connections

we can implement many to many using two 1-M @connections, an @key, and a joining @model.



