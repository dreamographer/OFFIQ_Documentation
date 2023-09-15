In a Mongoose schema, you can use various options and validators to define conditions and constraints for fields in your model. Here are some commonly used conditions and constraints that you can apply to fields in a Mongoose schema:

1. **Required Field**: You can use the `required: true` option to specify that a field is required and must have a value.

2. **Default Value**: You can set a default value for a field using the `default` option. If a value is not provided, the default value will be used.

3. **Minimum and Maximum Values**: For numeric fields (e.g., integers), you can use the `min` and `max` options to define minimum and maximum allowed values.

4. **Regular Expression (RegExp) Pattern**: You can use the `match` option to specify a regular expression pattern that a string field must match.

5. **Custom Validation Function**: You can define a custom validation function using the `validate` option. This function can perform custom validation logic on the field's value.

6. **Enum (Enumeration)**: You can use the `enum` option to specify a list of allowed values for a field. The field's value must be one of the enumerated values.

7. **Unique Field**: You can use the `unique: true` option to enforce that the field's value must be unique across all documents in the collection.

8. **Sparse Index**: You can use the `sparse: true` option to create a sparse index on the field. Sparse indexes only include documents that have the field, allowing null or missing values.

9. **Trim Whitespace**: You can use the `trim: true` option to automatically remove leading and trailing whitespace from string fields.

10. **Custom Getters and Setters**: You can define custom getter and setter functions for a field using the `get` and `set` options. These functions allow you to manipulate the field's value when reading or writing it.

11. **Immutable Field**: You can use the `immutable: true` option to prevent updates to a field after it has been initially set.

12. **Custom Error Messages**: You can provide custom error messages for validation failures using the `message` option.

Here's an example of how you can apply some of these conditions in a Mongoose schema:

```javascript
const mongoose = require('mongoose');

const userSchema = new mongoose.Schema({
  username: {
    type: String,
    required: true,
    unique: true,
    trim: true,
  },
  age: {
    type: Number,
    min: 18,
    max: 100,
  },
  email: {
    type: String,
    match: /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/,
  },
  status: {
    type: String,
    enum: ['active', 'inactive', 'blocked'],
  },
  createdAt: {
    type: Date,
    default: Date.now,
  },
});

const UserModel = mongoose.model('User', userSchema);

module.exports = UserModel;
```

In this example:

- The `username` field is required, must be unique, and will have leading and trailing whitespace trimmed.
- The `age` field has minimum and maximum value constraints.
- The `email` field uses a regular expression pattern for validation.
- The `status` field must be one of the enumerated values.
- The `createdAt` field has a default value of the current date and time.

You can apply these and other constraints to your schema fields as needed to ensure data integrity and consistency in your MongoDB documents.