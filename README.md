# GraphQL Job Board

This is a project used in the [GraphQL by Example](https://www.udemy.com/course/graphql-by-example/?referralCode=7ACEB04674F000BAC061) course.

It uses Apollo Server with Express, and GraphQL-Request and Apollo Client as GraphQL clients. The application is used to explain queries, mutations, custom object types, authentication, etc.

# Getting started

## Server
- nvm use
- npm i
- npm start

To access the playground go to: http://localhost:[yourport]/graphql

## Client
- npm i
- npm start

To access the front go to: http://localhost:[yourport]

## Plugins
[SQLLite Plugin](https://marketplace.visualstudio.com/items?itemName=alexcvzz.vscode-sqlite)
- After installing run command Open Database and open the provided sqllite db in the project.
- You can find this in the file explorer under the collapsible "SQLITE EXPLORER"

## Suggestions
If you are using visual studio code I suggest using a split-terminal. Run the client on one side and the server on the other side.

## Login Info
| id          | companyId    | email              | password |
|-------------|--------------|--------------------|----------|
| AcMJpL7b413Z| FjcJCHJALA4i | alice@facegle.io   | alice123 |
| BvBNW636Z89L| Gu7QW9LcnF5d | bob@goobook.co     | bob123   |

Access Token for alice: 
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJBY01KcEw3YjQxM1oiLCJlbWFpbCI6ImFsaWNlQGZhY2VnbGUuaW8iLCJpYXQiOjE3MjI1MTI1OTV9.-C-2wigZtyfZw2UKHDDSRzeLjaxTyfXpqS1OHskTTRE

## Examples

### QUERY
```
{
    jobs {
        items {
            company {
                id,
                description,
                name,
            },
            description,
            date,
            title,
        },
        totalCount
    },
    company (id: "FjcJCHJALA4i") {
        name,
        description,
        jobs {
            id,
            title,
            date,
            description,
        }
    }
}
```
### MUTATIONS
Requires the following header to be added in the playground (or whatever logged in user from above you use):

Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJBY01KcEw3YjQxM1oiLCJlbWFpbCI6ImFsaWNlQGZhY2VnbGUuaW8iLCJpYXQiOjE3MjI1MTI1OTV9.-C-2wigZtyfZw2UKHDDSRzeLjaxTyfXpqS1OHskTTRE

```
mutation {
  createJob(input: { title: "test", description: "test description" }) {
    id
    title
    description
  }
}
```