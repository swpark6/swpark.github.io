---
title: "inheritance and composition"
date: 2022-12-21
tags: 
  - OOP
---

## inheritance

```java
public class InstrumentedHashSet<E> extends HashSet<E> {
    private int addCount = 0;

    public InstrumentedHashSet() {
    }

    public InstrumentedHashSet(int initCap, float loadFactor) {
        super(initCap, loadFactor);
    }

    @Override
    public boolean add(E e) {
        addCount++;
        return super.add(e);
    }

    // HashSet의 add 메서드를 통해 구현 되어 있음
    @Override
    public boolean addAll(Collection<? extends E> c) {
        addCount += c.size();
        return super.addAll(c);
    }

    public int getAddCount() {
        return addCount;
    }

}
```

### 문제점

```java
InstrumentedHashSet<String> s = new InstrumentedHashSet<String>();

s.addAll(Arrays.asList("apple","banana","grape"); // addCount += 3
// 결국 addAll 호출과정에서 add를 3번 호출 함
// s.add("apple") -> addCount++
// s.add("banana") ->  addCount++
// s.add("grape") -> addCount++
```

- 상속은 Is-A 관계가 성립할 때만 하는 것이 적절함
  - `InstrumentedHashSet` 는 `HashSet`이 아니라 `HashSet`을 이용한 무엇 이다.
- 같은 패키지 안에 있을 때만 한다.

## Composition

- 기존 클래스를 상송 하는 대신에 (`InstrumentedHashSet<E> extends HashSet<E>`) 상속을 받으려고 했던 클래스에서 기존 객체를 참조하는 private 필드로 설정
- Forwarding: 새로운 클래스에서 기존 클래스의 함수를 호출하여 결과 반환
- Has-A 관계

```java
public class InstrumentedHashSet<E> implements HashSet<E> {
  private final HashSet<E> hashSet;
  public InstrumentedHashSet(HashSet<E> hashSet) { this.hashSet = hashSet; }
  
  // @Override ...
}
```
