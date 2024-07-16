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

where the `Foo.Read.All` gives access to list all `foo`s in `buzzes` and `Bar.Read.All` gives access to list all `bar`s in `buzzes`, there is ambiguity about what behavior a client should expected when making the following request with `Foo.Read.All` and `Fizz.Read.All`:

```http
GET /fizzes/{fizzId}/buzzes
```

//// TODO groupmembers.read.all makes it seem like relationships also need permissions
//// TODO if a scope can be assigned to something, that thing and collections it's a part of and members that it has need to be inherently treated differently than other "data-only" collections
//// TODO options are:
//// 1. only return foos
//// 2. return everything, but have the bars with only odata.id - gorup members are a security "needed information to make a decision"
//// 3. 403 entirely - this is the ideal case
        a. the API should know *all* of what can be present, and requires scopes for each of those types
           i. pros - this is the *actual* ideal case; there are no information leaks about count, id, types in the collection; the documentation can be more explicit about what permission scopes are required, and the workload can have full control over the required scopes
           ii. cons - 
        b. the other cases should follow 1 or 2 and should document exactly how they deviate from 3

## Solution

*Describe how to implement the solution to solve the problem.*

*Describe related patterns.*

## When to use this pattern

*Describe when and why the solution is applicable and when it might not be.*

## Issues and considerations

*Describe tradeoffs of the solution.*

## Example

*Provide a short example from real life.*
