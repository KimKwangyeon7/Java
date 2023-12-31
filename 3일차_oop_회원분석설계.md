## 7/19(수)

---
## [참고] 회원관리 프로젝트 요구사항
---

	- 아래의 요구사항을 참고하여 회원 도메인 클래스를 설계(고민)해보세요.
	- 회원의 속성 정보는 어떤것이 필요할까요?
	- 회원을 관리하기 위한 서비스는 어떤것이 필요할까요?

1. 회원관리시스템을 개발하고자 한다.(향후 웹 어플리케이션으로 확장 변경)
2. 회원은 일반회원, 우수회원, 관리자회원으로 구분한다.
3. 일반회원에게는 마일리지 정책에 따라 마일리지를 부여한다.
4. 우수회원에게는 전용 담당자를 배정한다.
5. 관리자 회원은 전체회원들의 정보를 관리한다.
6. 일반회원의 마일리지가 100,000 이상이 되면 우수회원으로 자동 등업한다.
7. 자동 등업시에 랜덤하게 관리자를 배정하며, 기존 마일리지는 초기화시킨다.
8. 마일리지 정책을 세우고 구현한다.
9. 일반, 우수회원은 가입후에 로그인을 통해서 내정보조회, 비밀번호 변경,  내정보전체변경 등의 기능을 사용할 수 있다.
10. 관리자 회원은 초기화 데이터를 통해서 관리자 회원으로 등록(생성)하여 사용한다.
11. 관리자 회원이 로그인을 하면 본인의 정보 조회, 변경등을 할 수 있으며, 전체회원의 정보를 조회 할 수 있다.
12. 단, 관리자 회원이 전체회원의 정보를 조회할때 회원들의 비밀번호는 앞2자리만 보여주고 나머지는 * 문자로 대체하여 조회한다.
13. 아이디 및 비밀번호를 잊어버린 회원을 위한  찾기 기능을 제공한다.
14. 공통으로 사용하기 위한 유틸 기능은 분리하여 설계한다.
15. 회원 관리를 위한 추가 기능을 설계한다.


---
## 회원관리 프로젝트
--- 객체 추출 : 회원, 게시판, 공지, 상품 등

## 회원(Member) 객체 => 클래스(Abstraction)
1. 속성(멤버변수): 목록 추출, 타입, 제약, 길이, 순서
- 7. (grade)등급: 일반(G), 우수(S), 관리자(A) : String(확장성) /  char
- 8. (mileage)마일리지: 일반 : int
- 1. (memberId)아이디 : String
- 2. (memberPw)비밀번호 : String
- 3. (name)이름 : String
- 4. (mobile)휴대폰: 010-1234-1234(형식-String), 01012341234(형식-String)
- 5. (email)이메일: String
- 9. (manager)담당자: String
- 6. (entryDate)가입일: String(고정형식, 연산하지않음) / Date(가변형식, 연산필요)

2. 기능(메서드)
- 관리자회원 등록 초기화
- 마일리지정책: 회원가입, 로그인, 가입1주년 등
- 전체회원조회: 관리자(회원 비밀번호 * 대체 보안변환)
- 우수회원 등업: 일반 100,000 이상, 담당자배정, 마일리지 초기화
- 담당자 랜덤 배정
- 가입(아이디, 비밀번호)
- 로그인(아이디, 비밀번호)
- 내정보조회
- 비밀번호변경
- 내정보전체변경
- 비밀번호 보안문자 변환 : 공통 유틸 분리
- 비밀번호찾기(아이디, 이름, 휴대폰/이메일)
- 아이디찾기(이름, 휴대폰/이메일)

## 유틸 공통 클래스: Utility
- 보안문자 변환: 비밀번호, 이름, 휴대폰 등


## 회원 데이터 설계
-- 사용자 입력 데이터: 아이디, 비밀번호, 이름, 휴대폰, 이메일(가입): 필수
-- 시스템 제공 데이터: 가입일(현재날짜-필수), 등급(가입시-일반G-필수), [마일리지-선택], [담당자-선택]



## 생성자(Constructor)	
-- 역할: 
	(1) 객체 생성시 멤버변수 초기화
	(2) 객체가 서비스되기전에 선행처리해야하는 로직
	
-- 특징:
	>> 중복 정의 가능: 중복정의 규칙(이름 동일, 매개변수 타입, 순서, 갯수 다름)
	>> 모든 클래스는 최소 1개 이상의 생성자가 정의되어야함
	>> javac(컴파일시점)가 생성자 명시적으로 정의되어 있지 않으면 자동으로 기본생성자를 제공
	>> 호출시점: 객체 생성시에 자동으로 호출 수행
	>> 객체생성시 사용하는 키워드 : new 클래스이름();  new 클래스이름(params)
	>> 반환타입을 표기해서는 안됨!!
	
-- 정의방법:
	>> 기본생성자 : no argument, empty body
	public 생성자클래스이름 () {}
	
	>> 중복정의 생성자
	[access-modifier] 생성자클래스이름 (args) { // statements }
	
-- 생성자를 이용한 객체 생성 방법
	>> 형식: 
		클래스이름 참조변수명 = new 클래스이름(); 
		클래스이름 참조변수명 = new 클래스이름(params);
		
		
## 상속(inheritnce)
-- 부모님꺼 내껏
-- 단일 상속
-- 재정의(Overriding)
-- Polymorphic Variable: 부모타입(큰타입)의 변수
-- this : 현재 객체를 지칭하는 참조변수, 객체 생성시 자동 제공
-- super: 현재 객체의 부모 객체를 지칭하는 참조변수, 객체 생성시 자동 제공
-- java.lang.Object : 
	>> 모든 클래스의 root class
	>> 계층구조(tree)
	>> 자동으로 상속받음: extends Object 
	>> 주로 재정의 사용하는 메서드
		=> toString():String
		=> equals(Object):boolean / hashCode();int
		=> getClass(): Class
-- modifiers
	>> access modifiers : 단일, public > protected > defaut(package) > private
	>> non-access modifiers(usage modifiers)
		=> static: 멤버변수(class 변수, static 변수), 멤버메서드(class 메서드, static 메서드)
		=> final : 멤버변수(변경불가), 매개변수(전달받은값변경불가), 메서드(재정의불가), 클래스(상속불가)
		=> abstract
		
-- 메서드선언형식: 표준화(규칙)
	[modifiers] 반환타입 메서드이름(매개변수타입 매개변수명, 매개변수타입 매개변수명) 
		throws 예외클래스명1, 예외클래스명x{
		// 수행문
	}
	
## 자바 소스파일의 구조	
1. package 선언문
-- 형식: package top.sub;
-- 사용횟수: 0(defaut package), 1
-- 물리적으로 폴더 개념
-- 목적: 관련 클래스들의 효율적인 관리, 권한 제어, 이름 충돌 방지
-- 해당 회사(단체) url을 뒤집어서 사용함: 공개시에 패키지명 충돌 방지
	>> http://www.ssafy.com
	>> package com.ssafy.model;
-- 패키지 레벨: 2 ~ 4	


2. import 선언문
-- 사용횟수 : 0 ~ N
-- javac(컴파일), java(실행) 시에 현재 클래스에서 사용한 다른 클래스의 경로 지정
-- 생략 가능한 클래스 패키지:
	(1) java.lang.* : // sub-package는 포함하지 않음, 클래스에만 적용됨
	(2) same package: 
	
-- 소스코드 지정:
	(1) import java.util.*;
	(2) import java.util.ArrayList; (권장)
	(3) 동일한 이름의 클래스가 다른 패키지에 존재하는 클래스를 함께 사용해야 하는 경우
		=> import 구문 대신에 클래스명앞에 패키지명을 포함해서 지정해야함
		//import java.util.Date;
		//import java.sql.Date;
		
		java.util.Date date = new java.util.Date();
		java.sql.Date date = new java.sql.Date();
	
-- javac(컴파일), java(실행) 시에 지정: classpath 경로 지정


3. class 선언문
-- 사용횟수: 1 ~ N
	>> 다중 클래스 선언은 가능하지만 권장하지는 않음
	>> 권장: 하나의 소스코드 파일안에 하나의 클래스 선언: 파일명만 보고 클래스를 식별가능
	>> 테스트시에 사용하기도 함
-- 규칙:
	>> public 권한의 클래스는 0, 1 : 1개이상 올수없음
	>> public 클래스 존재시에 파일명은 반드시 public클래스이름.java
	>> public 권한의 클래스가 없는 경우에 파일명은 마음데로 지정 가능함
	>> 보통 main(), 중심이 되는 클래스이름.java 주로 지정함

## class  구성요소
1. 멤버변수 선언문
2. 생성자 선언문: 기본생성자 > 매개변수 작은갯수 순서데로 구현 
3. 멤버메서드 선언문


## MVC Pattern
-- Model
	>> 업무처리 로직(Business/Service/Process Logic)
	>> 데이터베이스 처리 로직: DAO(Data Acess Object) Pattern
	>> 데이터를 갖고있는 객체(도메인): DTO(Data Transfer Object) Pattern
-- View
	>> 화면처리 로직(Presentation Login)
	>> UI(User Interface)
		=> CUI: Command Line UI (JavaSE: java.io.*, java.util.Scanner)
		=> GUI: Graphic UI(JavaSE: java.awt.*, java.swing.*, JavaEE: html/jsp)
-- Controller	
	>> 요청 ~ 응답 제어: JavaEE(Servlet)
	>> 1. 요청파악
	>> 2. 요청데이터 가져오기
	>> 3. 요청데이터 검증
	>> 4. Model 요청의뢰(검증받은요청데이터전달)
	>> 5. Model 요청의뢰한 결과받아서 응답하기
		=> 성공응답
		=> 실패응답
		
## MVC 기반의 package 구조		
-- com.ssafy.model
-- com.ssafy.model.dto
-- com.ssafy.model.service
-- com.ssafy.model.dao

-- com.ssafy.view
-- com.ssafy.controller

-- com.ssafy.util
-- com.ssafy.exception
		
	
## UML(Unified Modeling Language)
-- 객체 지향 분석 설계 표준 표기법
-- Class Diagram
	

## this : 현재 객체를 지칭하는 참조변수, 객체 생성시 자동 제공
1. 멤버변수명 지칭: this.멤버변수명, 지역변수명과 동일한 경우에 식별 가능
	-- 생성자의 멤버변수 초기화 사용
	
2. 현재객체의 다른 생성자 호출
	-- this(params)
	-- 중복코드 줄일수있음, 공통 로직을 일관성 부여
	-- 해당 객체의 생성자의 첫번째 수행문 위치
	
3. 객체 지칭 : this
	-- 메서드 매개변수 전달 받음
	-- 반환타입


## super: 현재 객체의 부모 객체를 지칭하는 참조변수, 객체 생성시 자동 제공
1. 부모의 멤버변수/멤버메서드 지칭 : 
	>> super.부모멤버변수명;  // 잘못 설계된 형식
	>> super.부모멤버메서드명();
	
2. 부모의 생성자를 명시적으로 지정: 
	>> super(params)
	>> 자식의 생성자에서 명시적으로 부모생성자를 지정하지 않으면 자동으로 부모의 기본생성: super();
	>> 자식객체의 생성자의 첫번째 수행문 위치: this(), super() 동시에 사용불가
	
	
## 재정의(Overriding)
-- 상속 전제조건
-- 규칙: 
	1. 반드시 동일해야함	: 반환타입 메서드이름(매개변수 순서, 타입, 갯수)
	2. 동일 또는 확대 가능: 접근 권한 (public > protected > package(defaut) > private)
	3. 축소 가능(동일, sub예외, 미발생): 예외 클래스 
-- @Override : 재정의 어노테이션
	>> javac(컴파일) 시점에서 재정의 규칙 준수여부 체킹
	

## 중복정의(Overloading)	
-- 전제조건 : 상속, same class
-- 규칙:
	1. 반드시 동일해야함: 메서드이름
	2. 반드시 달라야함: 매개변수 타입, 순서, 갯수
	3. 상관없음: 동일 또는 달라도됨, 반환타입, 접근권한, 예외클래스
	
	
## 상속(Inheritance)	: 회원관리
-- 부모클래스: Member
	>> 모든 회원이 갖는 공통 분리설계
	>> 아이디, 비밀번호, 이름, 휴대폰, 이메일, 가입일, 등급
-- 일반회원(자식): GeneralMember
	>> 마일리지
-- 우수회원(자식): SpecialMember
	>> 담당자
-- 관리자(자식) : AdminMember
	>> 직책 : position: String
	
