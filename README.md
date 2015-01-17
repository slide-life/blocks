# The Type Environment

All types are stored in a single environment dictionary. Types are scoped to
organizations, with a separate scope existing for canonical types. Each type
includes types of nested scope, that is, component types, as well as some
sample of the following reserved keywords.

- `_description` - A description of the type.
- `_inherits` - Another type from which the type inherits.
- `_type` - A primitive type which the type encapsulates. One of `text`, `number`, `image`, `tel`, `date`, `select`, `list`.
- `_options` - The options from which a type can select should it be of type `select`.
- `_representation` - A pattern used to serialize a compound type.
- `_components` - Array of existing types which should be added as components of a type
  with their names stripped of their prefixes.

A type can then be addressed based on its place within this hierarchy, using
the following pattern.

```scala
thecoop.com:membership-card.number
```

Compound types will be deserialized before submission, by a transform provided
by the vendor.

