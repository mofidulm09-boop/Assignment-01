# Union (`|`) ও Intersection (`&`) একসাথে ব্যবহার

## Introduction

TypeScript শেখার সময় প্রথমে আমার মনে হয়েছিল Union এবং Intersection প্রায় একই রকম। কিন্তু পরে বুঝতে পারলাম, এদের কাজ আলাদা। Union একাধিক Type-এর মধ্যে যেকোনো একটি গ্রহণ করতে পারে, আর Intersection একাধিক Type-এর বৈশিষ্ট্য একসঙ্গে যুক্ত করে। এই দুটি ব্যবহার করে বিভিন্ন ধরনের Data নিয়ে কাজ করা যায়।

## Detailed Body + Code Examples

### ১. Union (`|`) — অথবা

Union ব্যবহার করা হয় যখন একটি Variable একাধিক Type-এর মধ্যে যেকোনো একটি গ্রহণ করতে পারে।

```typescript
let studentId: number | string

studentId = 101
studentId = "ST-101"
studentId = true   // Error
```

এখানে `number` অথবা `string` দেওয়া যাবে। কিন্তু `boolean` দেওয়া যাবে না। কারণ এখানে শুধু দুটি Type নির্ধারণ করা হয়েছে।

### ২. Intersection (`&`) — এবং

Intersection দুই বা তার বেশি Type একসঙ্গে যুক্ত করে নতুন Type তৈরি করে।

```typescript
type Personal = {
  name: string
  age: number
}

type Academic = {
  subject: string
}

type Student = Personal & Academic
```

এখন Student Type ব্যবহার করলে Personal এবং Academic-এর সব Property দিতে হবে।

```typescript
const student: Student = {
  name: "Rakib",
  age: 22,
  subject: "TypeScript"
}
```

এখানে `name`, `age` এবং `subject` সবগুলো Property দিতে হবে। কোনো একটি বাদ দিলে Error দেখাবে।

### ৩. Union এবং Intersection একসঙ্গে ব্যবহার

Union এবং Intersection একই Code-এর মধ্যে একসঙ্গে ব্যবহার করা যায়।

```typescript
type User = {
  name: string
  email: string
};

type Role = "admin" | "editor"

type Account = User & {
  role: Role
}
```

এখানে User-এর `name` ও `email` বাধ্যতামূলক। অন্যদিকে Role হিসেবে শুধু `"admin"` অথবা `"editor"` দেওয়া যাবে।

```typescript
const account: Account = {
  name: "Rakib",
  email: "rakib@gmail.com",
  role: "admin"
}
```

এখানে Intersection দিয়ে User-এর Property যুক্ত করা হয়েছে এবং Union দিয়ে Role-এর জন্য দুটি বিকল্প রাখা হয়েছে।

## Conclusion

Union (`|`) মানে অথবা (OR), আর Intersection (`&`) মানে এবং (AND)। Union একাধিক Type-এর মধ্যে যেকোনো একটি গ্রহণ করতে সাহায্য করে। অন্যদিকে Intersection একাধিক Type-এর Property একসঙ্গে যুক্ত করে। প্রয়োজন অনুযায়ী দুটো একসঙ্গে ব্যবহার করে Code লেখা যায়।