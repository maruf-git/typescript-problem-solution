
# 📘 What are some differences between interfaces and types in TypeScript??

When working with TypeScript, both `interface` and `type` can be used to define the shape of an object. While they can often be used interchangeably, there are important differences and best-use scenarios for each.

## ✅ Similarities
Both `interface` and `type` can:
- Describe the shape of an object.
- Be extended or composed.
- Be used for function signatures.

## 🔹 Differences

| Feature | `interface` | `type` |
|--------|-------------|--------|
| Extending | Can extend other interfaces or types using `extends` | Can extend via intersection (`&`) |
| Declaration merging |  Yes (multiple declarations merge) |  No (redeclaring causes an error) |
| Use with primitives |  No |  Yes (e.g., `type ID = string \| number`) |
| Computed types |  Limited |  Powerful (can use conditional, mapped, and union types) |

### 🔹 When to Use What?

- Use **`interface`** when designing the shape of **objects or classes**, especially when you expect them to be extended.
- Use **`type`** when you need **union, intersection, or primitive types**, or when working with more advanced type logic.

### 🧪 Example

```ts
// Using interface
interface User {
  id: number;
  name: string;
}

// Using type
type Product = {
  id: number;
  title: string;
};

// Extending
interface Admin extends User {
  role: string;
}

type ExtendedProduct = Product & {
  price: number;
};
```

<hr />

# 📘 TypeScript Union (`|`) and Intersection (`&`) Types – Simple Examples

## 🔹 Union Type (`|`)
Union types let a variable hold **one of several types**.

```ts
type Status = "success" | "error" | "loading";

function showStatus(status: Status) {
  if (status === "success") {
    console.log("Operation successful");
  } else if (status === "error") {
    console.log("Something went wrong");
  } else {
    console.log("⏳ Loading...");
  }
}

showStatus("loading"); // Output: ⏳ Loading...
```

## 🔹Intersection Type (&)
Intersection types combine multiple types into one.**.

```ts
type User = {
  name: string;
  email: string;
};

type Admin = {
  role: "admin";
  accessLevel: number;
};

type AdminUser = User & Admin;

const admin: AdminUser = {
  name: "Alice",
  email: "alice@example.com",
  role: "admin",
  accessLevel: 5,
};

console.log(admin.name); // Output: Alice
```
## 🔄 Summary
| Feature | `Union` | `Intersection` |
|--------|-------------|--------|
| Meaning | Either type A or type B | Type A and type B |
| Use Case | Allow multiple possibilities | Combine multiple requirements |
| Example Output | "loading" | { name, email, role, accessLevel } |