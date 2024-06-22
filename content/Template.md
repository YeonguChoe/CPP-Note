# 템플릿(Template)

- 클래스 템플릿
- 함수 템플릿

## 클래스 템플릿

### 1단계: 클래스 템플릿 선언

```CC
template<typename T, typename U, typename V>
class 클래스_템플릿_이름 {
public:
    T 변수이름;

    T 함수이름() {
        
    }
};
```

- T, U, V는 type parameter라고 부른다.
- template<자료형>을 클래스 선언 위에 써준다.
- typename은 reserved keyword이다.
- typename 키워드 대신 class 키워드를 사용해도 된다.

```CC
template<class T>
class 클래스_템플릿_이름 {
};
```

### 2단계: 클래스 템플릿으로 객체 만들기

```CC
클래스_템플릿_이름<자료형> 객체_이름;
```

### 3단계: 멤버에 접근 하기

#### 멤버 변수(Instance variable)에 접근 하기

```CC
템플릿_객체_이름.변수_이름 = 값;
```

#### 멤버 함수(Method)에 접근 하기

```CC
템플릿_객체_이름.함수_이름();
```

### 템플릿 클래스 안에 있는 함수를 템플릿 클래스 밖에 선언하는 방법

- 함수만 템플릿 클래스 밖에 선언 가능하고, 멤버 변수는 클래스 밖에서 선언 불가능
  하다.

```CC
// 템플릿 클래스
template<typename T>
class Node {
public:
    T value;

    T modifyValue();
};

// 템플릿 클래스 밖에 선언한 함수
template<typename T>
T Node<T>::modifyValue() {
    Node::value += 1;
    return Node::value;
}
```

- 템플릿 클래스 밖에 선언한 함수의 signature은 type parameter만 괄호 <> 안에
  적어 줘야한다.

```CC
// 함수의 시그니처
template<typename T>
반환_자료형 템플릿_클래스_이름::메소드_이름()<T>{}
```

### Default type argument 지정 방법

#### 1단계: 템플릿 클래스 선언

```CC
template<typename T=기본_자료형1, class U=기본_자료형2, typename V=기본_자료형3>
class 템플릿_클래스_이름 {
};
```

#### 2단계: 객체 만들기

- default type argument를 지정하면 type parameter의 자료형을 지정해 주지 않아도
  된다.

```CC
템플릿_클래스_이름<> 객체_이름;
```

- 객체를 만들때 선택적으로 type parameter을 왼쪽 부터 지정해 줄수 있다.

```CC
템플릿_클래스_이름<double, double, double> 객체_이름;
```

## 함수 템플릿(function template)

### 1단계: 함수 템플릿 선언

```CC
template<typename T>
반환_자료형 함수_이름() {
    return 반환값;
}
```

### 2단계: 함수 사용

```CC
함수_이름<자료형>();
```

### Default type argument 지정 방법

#### 1단계: 함수 템플릿 선언

```CC
template<typename T=기본_자료형>
반환_자료형 함수_이름() {
    return 반환값;
}
```

#### 2단계: 함수 사용

```CC
함수_이름<>();
```

- 선택적으로 type parameter의 자료형을 지정할수 있다.

```CC
함수_이름<자료형>();
```