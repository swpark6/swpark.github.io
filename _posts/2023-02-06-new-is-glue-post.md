---
title: "New is glue"
date: 2023-02-06
categories: OOP
---

# New is glue (커플링)
## 용어
- POCO, or Plain Old CLR Type
## 내용
- Code that is tightly coupled to a particular file system or a particular vendor's database tends to be more difficult to test, change, and maintain than software that is loosely coupled to its infrastructure.
- 강결합 형태를 가지고 OCP 를 위반하는 세 가지 일반적인 패턴이 있음.
    - 왜냐하면 코드를 고치지 않고서는 구현을 할 수 없기 때문
    - 첫 두개는 정적 메서드를 호출하는 것과  정적 메서드를 호출하여 싱글톤 패턴 인스턴스를 참조하는 기술
    - 세번째는 `new` 키워드를 직접 사용하여 인스턴스화 하는 것. 애플리케이션이 유용하려면 특정 구현 유형과 함께 작동해야 하지만 사용할 구현 유형에 대한 결정은 이상적으로는 **시스템 전체에 흩어져 있는 것이 아니라 한 곳에서 이루어져야 합니다.**
- `new` 키워드를 사용할 때 현재 함수나 클래스를 특정 구현에 밀접하게 결합한다는 사실에 대해 생각해야 합니다.
### New 가 문제가 되는 곳
- POCO 또는 Plain Old CLR Type 이 아닌 경우 (랭기지에서 제공하는 기본 클래스라고 생각하면 될듯)
    - String, DateTime, 사용자 정의 DTO들은 테스트하기에 어렵지 않다.
    - `SqlConnection` 같은 것을 붙일 때, 즉시 데이터베이스 서버에 연결 시도를 할 것이고, 연결에 실패했을 경우 예외를 던질 것이다. 이것은 매우 큰 risk이다. 또한 특별한 도구 없이는 쉽게 테스트할 수 없다. 따라서 connection에 관한 추상화 없이는 connection pooling, caching 이나 다른 종류의 데이터 스토어를 구현하는게 어렵다.
## Ref
- [New is glue](https://www.weeklydevtips.com/episodes/005)
