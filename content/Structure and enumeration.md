## 구조체

- 구조체를 사용하면 여러개의 변수들을 하나의 자료형으로 묶어서 관리할수 있다.
- 클래스와 달리 구조체에서는 보통 상속을 사용안한다.

### 구조체를 선언하는 방법

```CC
struct myStruct {
    std::string name;
    int age;
    void introduce() {
        std::cout << "My name is " << name << '.' << endl;
    }
};
```

### 구조체 변수를 선언 하는 방법

```CC
int main() {
    myStruct myStructure;
    myStructure.name = "Yeongu";
    myStructure.introduce();
    return 0;
}
```

## 열거형 자료형(Enumeration)

### 열거형 자료형에 값을 넣으면 변수로 지정을 할 수 있다.

- 용어: enum 집합의 이름을 enumeration이라고 하고, enumeration 안에 들어 있는
  element들을 enumerator라고 한다.

```CC
enum Enumeration {
    enumerator1 = 100,
    enumerator2 = 200,
    enumerator3 // 디폴트 값으로 이전 enumerator보다 1 큰 수가 된다.
};
```