## 데이터 은닉과 보호 (Encapsulation)
-- 정보 보호를 위한 대책
	>> private으로 바꾸기
	>> 공개되는 메서드를 통한 접근 통로 마련: setter / getter

## 객체 생성 제어와 Singleton 디자인 패턴
-- 여러 개의 객체가 필요 없는 경우
	>> 객체를 구별할 필요 X == 수정 가능한 멤버 변수가 없고 기능만 있는 경우 => stateless한 객체
	>> 객체를 계속 생성/삭제 하는데 많은 비용이 들어 재사용이 유리한 경우

## 다형성 (Polymorphism)
-- 하나의 객체가 많은 형(타입)을 가질 수 있는 성질
ex) 황금 잉어빵 is a 붕어빵: 상속 관계
-- 상속 관계에 있을 때 조상 클래스의 타입으로 자식 클래스 객체를 레퍼런스 할 수 있다.


## 정적 바인딩과 동적 바인딩
-- 정적: 컴파일 단계에서 참조 변수의 타입에 따라 연결이 달라짐 / 상속 관계에서 객체의 멤버 변수가 중복될 때 또는 static method
-- 동적: 다형성을 이용해 메서드 호출이 발생할 때 runtime에 메모리의 실제 객체의 타입으로 결정 ex) 대표적으로는toString()메서드 / 


_______________________________________________________________________________________________________________________________________________
싱글톤은 주로 DAO(나중에 테이블과 매핑할 때 혼선을 줄이기 위해 하나만), 서비스 클래스 등에 사용 => 상태보다는 주로 기능을 제공하는 역할에 사용

- access modifier: public, private
- encapsulation
- singleton pattern
	>> stateless
- polymorphism
	>> 메서드(중복정의 overloading, 재정의 overriding), 생성자(오버로딩)
	>> 변수의 타입: 큰 타입(부모 타입)
		=> 변수(기본형, 참조형), 배열(기본형, 참조형), 매개변수, 반환타입 
	>> typecasting
	>> instanceof
형변환시 동적 바인딩 -> class cast exception 발생 가능 => instanceof
- has a
- is a
- 황금붕어빵 < 붕어빵 < 빵 < 음식
- 정적 바인딩 (static binding) - 컴파일시
- 동적 바인딩 (dynamic binding) - 런타임시


________________________________________________________________________________________________________________________________________ #담주 월 시험
단답형 + 소스코드의 수행결과 + 서술형

1. 데이터 타입과 형변환, 연산자
2. 기본문장 - switch, while, continue, break ...
3. class 설계 - 생성자, toString(), equals(), hashcode()
4. 객체 생성 - this, super
5. 다형성 - overloading, overriding
6. 배열 - 초기화
7. 자바 기본 API - String, Object ...
8. Abstract class, interface
9. modifier - access, usage 각각 다 자세히 + 코드까지

상속 재정의 다 개념 연결하면서 이해하기 




memberservice, objecttes, member....

null, 연산자, ++ -- print / ln / f 연산결과 꼼꼼히
&와 && 차이
switch는 int 문자열 byteshortlong
continue break continue label명
switch도빠져나옴
생성자 중복정의
tostring equals hashcode 재정의 같이
this, super, this(), super() 부모의 기본 생성자 여부 확인
오버로드 오버라이딩 규칙 
동적바인딩 - 오버라읻ㅇ 재정으한 메서드는 재정의한 쪽으로
배열 선언 생성 ... 자세하게 방법들 다 볼것
java api charAt, length() length
추상 메서드 인터페이스 
@override
modifier 접근권한자 static,final, static멤버변수-class area
call by value call by reference
static 안에는 static 멤버만

변수 범위 확실하게 알기
static인스턴스




