---
layout: post
title: 초심자를 위한 안드로이드 키워드
tags:
  - 안드로이드
  - android
  - keyword
comments: true
---


## 필수 키워드

> 해당 글을 2020년에 작성하였습니다. 때문에 최신 트렌드가 반영되지 않았을 가능성을 알려드립니다.

### 초급

- 4대 컴포넌트
- 생명주기
  - onSaveInstanceState() 메소드
  - 화면 회전시 앱이 터지지 않게 하려면?
- ConstraintLayout
  - LinearLayout 보다 성능이 좋음
    - 뷰과 그려지는 과정과 관련되어 있다.
    - 뷰 안에 뷰를 그리게 되면 깊이가 생기게 되는데 안드로이드는 차례로 들어가며 뷰를 생성하기 때문에 리니어에 더 많은 깊이를 추가할 수록 성능이 나빠질 수 있다. 이와 다르게 제약조건은 모든 뷰들이 같은 깊이 이기 때문에 linear보다 성능이 좋다(약간더)
- recyclerView
  - 아이템 재사용 → 메모리 절약
  - 어댑터 패턴
- 액티비티와 프래그먼트
- 안드로이드의 메모리 힙/스택
- 명시적 intent, 암시적 intent - 버전별 제한
- jetpack
- 안드로이드의 프로세스와 쓰레드
- 싱글톤



### 중급

- 비동기 작업
  - 비동기의 의미
  - 라이브러리
  - rxJava, rxKotlin
- 메모리 누수 관리
- 네트워크 컴포넌트 ex) volley, retrofit, okhttp3 라이브러리 등
- mvc, mvp, mvvm 아키텍쳐