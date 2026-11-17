# TypeScript-এ Access Modifiers: public, private, protected ও readonly

## Introduction

TypeScript-এ Class তৈরি করার সময় কোন Property কোথায় ব্যবহার করা যাবে, সেটি নির্ধারণ করার প্রয়োজন হয়। সব Property বাইরে থেকে ব্যবহার করার অনুমতি দেওয়া ঠিক নয়। এই কাজের জন্য TypeScript-এ `public`, `private`, `protected` এবং `readonly` ব্যবহার করা হয়। এগুলোর কাজ আলাদা এবং প্রতিটির ব্যবহারের নিয়মও আলাদা।

## Detailed Body + Code Examples

### ১. public — সবার জন্য

`public` ব্যবহার করলে Class-এর Property বাইরে থেকেও ব্যবহার করা যায়। TypeScript-এ কোনো Access Modifier না লিখলেও Property ডিফল্টভাবে `public` থাকে।

```ts
class Employee {
  public name: string

  constructor(name: string) {
    this.name = name
  }
}

const emp = new Employee("Mofidul")
emp.name = "Rahim"
```

এখানে `name` Property বাইরে থেকে পরিবর্তন করা যাচ্ছে, কারণ এটি `public`।

### ২. private — শুধু নিজের Class-এর জন্য

`private` ব্যবহার করলে Property শুধু নিজের Class-এর ভিতরে ব্যবহার করা যায়। Class-এর বাইরে থেকে সরাসরি এই Property ব্যবহার বা পরিবর্তন করা যায় না।

```ts
class Employee {
  private baseSalary: number = 50000

  getDetails(): string {
    return `Salary: ${this.baseSalary}`
  }
}
```

এখানে `baseSalary` শুধু Employee Class-এর ভিতরে ব্যবহার করা যাবে। `getDetails()` Method-এর মাধ্যমে এর মান পাওয়া যাচ্ছে।

### ৩. protected — নিজের ও Child Class-এর জন্য

`protected` ব্যবহার করলে Property নিজের Class এবং সেই Class থেকে তৈরি Child Class-এর ভিতরে ব্যবহার করা যায়। তবে Class-এর বাইরে থেকে সরাসরি ব্যবহার করা যায় না।

```ts
class Employee {
  protected name: string;

  constructor(name: string) {
    this.name = name
  }
}

class Manager extends Employee {
  getRoleInfo(): string {
    return `Manager: ${this.name}`
  }
}
```

এখানে Manager হলো Employee-এর Child Class। তাই Manager-এর ভিতরে `name` Property ব্যবহার করা যাচ্ছে।

### ৪. readonly — পরিবর্তন করা যাবে না

`readonly` ব্যবহার করলে কোনো Property-তে একবার মান সেট করার পর সেটি আবার পরিবর্তন করা যায় না। সাধারণত Constructor-এর মাধ্যমে এর মান নির্ধারণ করা হয়।

```ts
class Invoice {
  readonly id: number;

  constructor(id: number) {
    this.id = id
  }
}
```

এখানে `id`-এর মান Constructor-এ দেওয়া হচ্ছে। পরে অন্য কোথাও থেকে এই মান পরিবর্তন করা যাবে না।

## Conclusion

`public`, `private` এবং `protected` নির্ধারণ করে কোন জায়গা থেকে Property ব্যবহার করা যাবে। অন্যদিকে `readonly` নির্ধারণ করে Property-এর মান পরিবর্তন করা যাবে কি না। প্রয়োজন অনুযায়ী এগুলো ব্যবহার করলে Class-এর Property নিয়ন্ত্রণ করা সহজ হয় এবং Code আরও পরিষ্কার থাকে।