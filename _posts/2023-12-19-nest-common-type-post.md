---
title: Type - @nestjs/common
date: 2023-12-19
tags:
- nestjs
---

```typescript
export interface Type<T = any> extends Function {
    new (...args: any[]): T; // T 타입 인스턴스 생성
}
```
- [Type](https://github.com/nestjs/nest/blob/master/packages/common/interfaces/type.interface.ts)

- 런타임 종속성 주입때 편리하게 사용 가능
- NestJS에서는 Module 만들때 사용하면 편리함

```typescript
export class MyModule {
  static createWith(someDependency: Type) {
    // ...
    return {
      module: MyModule,
      // ...
    }
  }
}
```
