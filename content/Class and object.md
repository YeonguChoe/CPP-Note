# 함수(Method)

- C++에서 함수는 main함수 내부나 클래스 내부 뿐만아니라, 어디에서든지 작성해도
  된다.

```CC
<반환 자료형> myFunction(<parameter>) {
    <코드>
    return <반환값>;
}
```

# 상속

- Super클래스와 Sub클래스를 만드는 방법

```CC
class SuperClass1 {
protected:
//    데이터 멤버
    <자료형> <변수 이름>;

//    멤버 함수
    <반환 타입> <함수 이름>() {
        <코드>
    }
};

class SuperClass2 {
protected:
//    멤버 함수
    <반환 타입> <함수 이름>() {
        <코드>
    }
};

//    상속을 하는 Super type인 클래스들을 접근 제어자와 함께 적어 준다.
class SubClass : public SuperClass1, public SuperClass2 {
public:
//    데이터 멤버
    <자료형> <변수 이름>;

//    생성자
    SubClass() {
        <데이터 멤버 초기화>
    }

//    멤버 함수
    void bark() {
        <코드>
    }

private:
    <자료형> <변수 이름> = <값>;
};
```

# 객체를 만드는 방법

```CC
int main() {
    클래스_이름 객체_이름;
    return 0;
}
```

# 접근 제어자

- public: 어디에서나 접근 가능.
- protected: 같은 클래스 내부 또는 상속 받는 클래스 내부 에서만 접근 가능.
- private: 같은 클래스 내부에서만 접근 가능.

## public 상속을 하는 경우 sub클래스에서 멤버의 접근제어자

```CC
class SubClass : public SuperClass {
```

| Super클래스에서 접근제어자 | Sub클래스에서 변화된 접근제어자 |
| -------------------------- | ------------------------------- |
| public                     | public                          |
| protected                  | protected                       |

## protected 상속을 하는 경우 sub클래스에서 멤버의 접근제어자

```CC
class SubClass : protected SuperClass {
```

| Super클래스에서 접근제어자 | Sub클래스에서 변화된 접근제어자 |
| -------------------------- | ------------------------------- |
| public                     | protected                       |
| protected                  | protected                       |

## private 상속을 하는 경우 sub클래스에서 멤버의 접근제어자

```CC
class SubClass : private SuperClass {
```

| Super클래스에서 접근제어자 | Sub클래스에서 변화된 접근제어자 |
| -------------------------- | ------------------------------- |
| public                     | private                         |
| protected                  | protected                       |

# 가상 함수를 이용해서 interface를 구현하는 방법

- C++의 인터페이스에는 가상 함수와 가상 함수에서 사용할 수 있는 변수 들어갑니다.
- 가상 함수는 Sub클래스에서 재정의 할것을 기대하는 멤버 함수 입니다.
- 가상 함수를 포함하는 interface로는 객체를 만들수 없습니다.

```CC
class MyInterface {
public:
    int MYNUMBER = 1962; // 변수
    virtual void functionToBeImplemented(int input) = 0; // 가상 함수
};
```

## Interface를 구현 하는 클래스

- 일반적인 클래스와 같이 상속을 하고, 함수의 내용을 override 한다.

```CC
class MyClassImplements : public MyInterface {
public:
    void functionToBeImplemented(int input) {
        std::cout << MYNUMBER << std::endl;
    }
};
```

# abstract 키워드를 이용해서 추상 클래스를 구현하는 방법

- 추상 클래스는 구현하지 않은 함수를 포함한 클래스 입니다.
- 구현하지 않은 함수는 가상 함수로 signature을 작성해 놓는다.
- 추상 클래스로는 객체를 만들수 없습니다.

```CC
class MyAbstractClass {
public:
    int myVariable;
    void implementedFunction() {
        std::cout << "This Function is already implemented." << std::endl;
    }
    virtual void abstractFunction() = 0; // 가상 함수
};
```

## 추상 클래스를 extends 하는 클래스

- 일반적으로 클래스가 다른 클래스를 상속 받는 것 처럼 코드를 작성한다.

```CC
class MyClassExtends : public MyAbstractClass {
public:
    void abstractFunction() {
        myVariable = 1962;
        std::cout << myVariable << std::endl;
    }
};
```

# 생성자(Constructor)

## 생성자 선언

```CC
// 클래스 내부
// Default constructor
클래스_이름() {
    필드 초기화
}

// Parametrized constructor
클래스_이름(자료형 매개변수_이름) {
    필드 초기화
}
```

# 소멸자(Destructor)

- 소멸자는 메모리에 할당된 객체에 대한 모든 데이터를 삭제 한다.
- Stack에 생성된 객체는 자동으로 삭제 된다.

## 소멸자 선언

```CC
~클래스_이름() {
    std::cout << "객체에 대한 모든것이 삭제 되었습니다" << std::endl;
}
```
