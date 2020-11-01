---
layout: post
title: Optional(옵셔널)
tags:
  - swift
  - optional
  - 옵셔널
  - 스위프트
comments: true
---
> 해당 포스트는 저자 야곰님의  `Swift 스위프트 프로그래밍 3판` 을 참고하여 작성되었습니다.
# Chapter8 옵셔널

- 스위프트의 특징중 하나인 안전성을 위한 기능이다.
- 옵셔널의 단어 뜻처럼 선택적인, 즉 값이 있을 수도 없을 수도 있음을 나타낸다.
- 다른 언어의 API의 문서를 보면 nullable이거나 nonnullable임을 표시해주는데 swift에서는 ?기호로 nil일수있음을 단번에 알 수 있다.



## 8.1 옵셔널 사용

- nil은 값이 없을을 의미한다.

- 옵셔널은 해당 변수 혹은 상수가 nil일 수 있음을 의미한다. 즉 nil 일수 있으니 사용에 주의하라는 의미이다.

- nil은 옵셔널로 선언된 곳에서만 사용 할 수 있다.

- 옵셔널 변수, 상수 등은 데이터 타입 뒤에 물음표(?)를 붙여 표현해준다

- 옵셔널은 왜 필요할 까?

  - 함수에 전달하는 전달 인자의 값이 잘못된 값일 경우 제대로 처리하지 못했음을 nil을 반환하여 표현할 때 사용할 수 있다. 또는 매개 변수를 굳이 넘기지 않아도 될다는 뜻으로 매개변수 타입을 옵셔널로 정의할 수도 있다.

- 옵셔널 열거형의 정의

  ```swift
  public enum Optional<Wrapped> :ExpressibleByNilLiteral {
    case none
    case some(Wrapped)
    
    public init(_ some: Wrapped)
   	/// 중략
  }
  ```
  - 값이 nil 일때 none케이스, 값이 있을때 some 케이스가 된다.
  - 옵셔널 자체가 열거형이기 때문에 switch 구문을 통해 값이 있고 없을을 확인 할 수 있다.



## 8.2 옵셔널 추출

- 옵셔널이 값을 옵셔널이 아닌 값으로 추출하는 방법

### 8.2.1 강제 추출

- 가장 간단하지만 가장 위험한 방법
- 옵셔널 값의 뒤에 느낌표(!)를 붙여주어 값을 강제로 추출하여 반환
- 만약 강제 추출시 옵셔널에 값이 없다면 값이 nil이라는 런타임 오류가 발생
  - 때문에 옵셔널을 만든 의미가 무색해지는 방법이다.
- 런타임 오류의 가능성을 항상 가지고 있기 때문에 강제추출을 지양해야 한다.

### 8.2.1 옵셔널 바인딩

- 옵셔널 바인딩은 옵셔널에 값이 있는지 확인할 때 사용

- 옵셔널에 값이 있다면 블록안에서 사용할수 있는 변수나 상수로 할당해서 옵셔널이 아닌 형태로 사용할 수 있도록 해준다.

  ``` swift
  var optionalVariable: String? = "optional"
  
  // 옵셔널 바인딩을 이용하여 임시 상수 할당
  // optionalVariable 변수가 nil이라면 someCase 상수에 할당하여 블록에서 사용
  // nil이라면 else 블록
  if let someCase = optionalVariable {
    print("is \(someCase)")
  } else {
    print("none case")
  }
  
  // 옵셔널 바인딩을 이용하여 임시 변수 할당
  if var someCase = optionalVariable {
    someCase = "some case"
    print("is \(someCase)")
  } else {
    print("none case")
  }
  ```

  - 위 두가지 예제에서 someCase라는 변수와 상수에 optionalVariable 값을 할당하였다. optionalVariable에 값이 있다면 someCase는 if 블록 안에서만 사용할 수 있다.

- 옵셔널 바인딩을 통해 한 번에 여러 옵셔널의 값을 추출 할 수도 있다. 쉼표를 사용해서 바인할 옵셔널을 나열하면 되나 하나라도 nil값이라면 if 블록 내부의 코드가 실행 되지 않는다.

### 8.2.3 암시적 추출 옵셔널

- nil을 할당하고 싶지만, 옵셔널 바인딩으로 매번 값을 추출하기 귀찮을때
- 로직상 nil 때문에 런타임 오류가 발생하지 않을 것 같다는 확실이 들 때 
- 타입 뒤에 (!)를 사용하는 것을 암시적 추출 옵셔널이라고 한다.
- 강제추출과 마찬가지로 상용을 권장하지는 않는다.
