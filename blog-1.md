# How Generics Help Build Reusable and Strictly Typed TypeScript Code

## Introduction

When writing TypeScript, we often want to create functions, classes, or components that can work with many kinds of data. At the same time, we do not want to lose type safety. This is where **Generics** become very useful.

Generics allow us to write reusable logic that stays strictly typed no matter what data structure is passed in. In simple words, a generic is like a type placeholder. We define the structure once, and TypeScript fills in the actual type later when the code is used.

## What Is a Generic?

A generic lets us create code that works with different types while preserving the exact type information.

```ts
function identity<T>(value: T): T {
  return value;
}
```

Here, `T` is a generic type parameter. It means:

- the function can accept any type
- the return type will be the same as the input type

Now we can use the same function with different values:

```ts
const a = identity<string>("Hello");
const b = identity<number>(123);
const c = identity<boolean>(true);
```

TypeScript knows that:

- `a` is a `string`
- `b` is a `number`
- `c` is a `boolean`

## Why Generics Are Important

Without generics, we would need to write separate functions for separate types.

```ts
function getString(value: string): string {
  return value;
}

function getNumber(value: number): number {
  return value;
}
```

This creates unnecessary duplication. If the logic is the same, writing multiple versions makes the code harder to maintain.

Generics solve this problem by allowing one reusable function to handle multiple types safely.

## Generics with Arrays

Generics are especially helpful when working with arrays or lists.

```ts
function getFirstItem<T>(items: T[]): T {
  return items[0];
}

const firstNumber = getFirstItem<number>([10, 20, 30]);
const firstText = getFirstItem<string>(["TypeScript", "JavaScript"]);
```

In this example:

- `firstNumber` is inferred as `number`
- `firstText` is inferred as `string`

So the function remains reusable, but the returned value is still strongly typed.

## Generics with Interfaces

Generics also make interfaces flexible and reusable.

```ts
interface ApiResponse<T> {
  success: boolean;
  data: T;
}

const userResponse: ApiResponse<{ name: string; age: number }> = {
  success: true,
  data: {
    name: "Sam",
    age: 22,
  },
};
```

Here, `ApiResponse<T>` can represent many kinds of API responses. Today it may hold user data, tomorrow it may hold product data. The structure stays the same, but the data type changes safely.

## Generics in Reusable Components and Functions

In larger applications, we often build utility functions that should work for many data models.

```ts
function wrapInArray<T>(value: T): T[] {
  return [value];
}

const names = wrapInArray<string>("Alice");
const ids = wrapInArray<number>(101);
```

This pattern is common in real-world TypeScript projects because it helps developers write code once and use it in many places without giving up type checking.

## Benefits of Generics

Generics provide several important advantages:

- **Reusability:** one function or interface can work with many data types
- **Type Safety:** TypeScript still checks the exact type
- **Less Duplication:** no need to rewrite the same logic for different types
- **Scalability:** reusable patterns become easier to manage in large projects

## Conclusion

Generics are one of the most powerful features in TypeScript because they combine **flexibility** with **strict typing**. They allow developers to build reusable components, functions, and interfaces that adapt to different data structures while still remaining safe and predictable. For this reason, generics are essential for writing clean, scalable, and professional TypeScript code.
