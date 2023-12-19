---
title: "Aragon2"
date: 2023-01-27
categories: OOP
---

- Blake2b 로 해시하여 초기 변환을 거치고, 내부 함수를 반복 수행하여 완성
    - 차차 스트림(ChaCha stream)에 기반함
    - 메모리 접근 방법에 따라 tradeoff attack 방어 가능 가능
- Argon2i:
    - 메모리 접근방법: data-independent memory access
        - 메모리를 두 번 덮어씀
            - 메모리 누수 공격(memoty-leak attack), tradeoff attack에 대해 안전함
- Argon2d:
    - 메모리 접근방법: data-dependent memory access
        - 메모리를 덮어쓰지 않음
            - 쓰레기 수집 공격(garbage-collector attack)에 취약 할 수 있음
    - 가변길이 입력 값 사용
    - 동등한 문자열 입력 할 수 없음
    - 연상 방법(단일 패스, 단일 스레드로 메모리를 채우는 방법에 기반 한 내부함수), 회복력, 저항력 의 주요 특징을 지님.

### Ref
- [패스워드 해싱 알고리즘 분석](http://www.koreascience.kr/article/CFKO201529368417738.pdf)
- [블레이크2B](http://wiki.hash.kr/index.php/%EB%B8%94%EB%A0%88%EC%9D%B4%ED%81%AC2B)
