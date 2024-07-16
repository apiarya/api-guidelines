# Collection Filtering By Permission Scope

Microsoft Graph API Design Pattern

*Clients don't always have permission to read all of the data in a collection. In these cases, APIs need to clearly define the expected behavior of the API. One option is to filter out elements of the collection that the client does not have access to.*


## Problem

For the following model:

```xml
<EntityType Name="buzz">
</EntityType>

<EntityType Name="foo" BaseType="self.buzz">
</EntityType>

<EntityType Name="bar" BaseType="self.buzz">
</EntityType>

<EntityType Name="fizz">
  <NavigationProperty Name="buzzes" Type="Collection(self.buzz)" ContainsTarget="false" />
</EntityType>

//// TODO flesh out this model fully
```

where the `Foo.Read.All` gives access to list all `foo`s in `buzzes` and `Bar.Read.All` gives access to list all `bar`s in `buzzes`, there is ambiguity about what behavior a client should expected when making the following request with **only** `Foo.Read.All`:

```http
GET /fizzes/{fizzId}/buzzes
```

//// TODO options are:
//// 1. only return foos
//// 2. return everything, but have the bars with only odata.id
//// 3. 403 entirely

## Solution

*Describe how to implement the solution to solve the problem.*

*Describe related patterns.*

## When to use this pattern

*Describe when and why the solution is applicable and when it might not be.*

## Issues and considerations

*Describe tradeoffs of the solution.*

## Example

*Provide a short example from real life.*
