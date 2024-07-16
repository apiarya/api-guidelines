# Collection Filtering By Permission Scope

Microsoft Graph API Design Pattern

*Clients don't always have permission to read all of the data in a collection. In these cases, APIs need to clearly define the expected behavior of the API. One option is to filter out elements of the collection that the client does not have access to.*


## Problem

For the following model:

```xml
```

where the `Foo.Read.All` gives access to list all `foo`s in `fizzes` and `Bar.Read.All` gives access to list all `bar`s in `fizzes`, there is ambiguity about what behavior a client should expected when making the following request with **only** `Foo.Read.All`:

```http
```

## Solution

*Describe how to implement the solution to solve the problem.*

*Describe related patterns.*

## When to use this pattern

*Describe when and why the solution is applicable and when it might not be.*

## Issues and considerations

*Describe tradeoffs of the solution.*

## Example

*Provide a short example from real life.*
