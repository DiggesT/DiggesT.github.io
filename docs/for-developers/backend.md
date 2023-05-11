---
sidebar_position: 1
---

# Backend

All object-only enums must be stringified with `asString` function. For example `Role`:

```scala
enum Role:
  case Admin     extends Role
  case Moderator extends Role
  case User      extends Role
  case Guest     extends Role

  def asString: String =
    this.toString.toLowerCase
```

All complex enums must have `kind` property. For example `AuthError`:

```scala
enum AuthError(val kind: String):
  def reason: String

  case ServerError(reason: String) extends AuthError("server_error")
  case InvalidLogin(reason: String) extends AuthError("invalid_login")
```

That way, they can be exported into OpenAPI in a consistent way.

Most of the core entities are formatted in a similar way with following repeating patterns:

- `Id` opaque type (over UUID) to represent a DB id column
- The main entity case class exactly represents all DB columns as its members, _except_ the `Id`. Sometimes referred to as `Column`.
  If the table contains any foreign keys they'd be represented as their respective `Id`s with a name like `userId` or `itemId`
- The `WithMeta` case class containing main entity and some metadata. Most entities have the shared metadata residing in `common` package
- The `New` case class representing a set of values that are _not_ inserted by a DB (read DAO), such as `createdAt`, `Id` etc
- The `Base` case class representing a set of values that are passed from frontend, typically it's a web form and RESTful input
- There's a clear path from the smallest class (`Base`) to a biggest (`WithId`), e.g. `base.toNew(authorId).toColumn(createdAt).withId(id)`
- Possible other representations of the entity, e.g. one with joined entities or with `New` with default values
