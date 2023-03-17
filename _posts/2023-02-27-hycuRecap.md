---
layout: post
title: "hycu Recap"
---

## 코드는 재산이다, 나중에 도움된다, 정리잘하자

```js

2023 정보처리기술

-1- 데이터베이스의 정의와 기본 개념
- 데이터베이스: 조직에 필요한 데이터를 효율적으로 관리하기 위해 통합하여 저장한 데이터의 집합
-- 데이터베이스 시스템은 데이터의 검색과 변경 작업을 주로 수행

- 정보시스템 
-- 조직 운영에 필요한 정보를 수집, 저장해두었다가 필요할 때 유용한 정보를 만들어 내는 시스템

- 데이터베이스의 특징
-- 실시간 접근성: 데이터베이스에 저장된 데이터는 사용자의 요구에 따라 언제든지 접근 가능
-- 계속적인 변화: 데이터베이스는 실시간으로 데이터를 추가, 삭제, 수정할 수 있음
-- 동시 공유: 여러 사용자가 동시에 데이터베이스에 접근할 수 있음
-- 내용에 의한 참조: 데이터베이스에 저장된 데이터는 데이터의 내용을 통해 참조 가능

- 데이터베이스의 구조적 형태
-- 개념적 구조를 논리적 구조로 표현하는 논리적 데이터 모델
-- 하나의 개체에 대한 데이터를 하나의 릴레이션에 저장

- 데이터베이스의 발전 배경
-- 파일을 중심으로 한 종래의 자료 처리 시스템에서는 각 응용프로그램이 개별적으로 자기 자신의 데이터파일을 관리 유지

- 데이터의 종속성과 중복성
-- 데이터의 종속성: 데이터의 논리적 구조를 표현하는 데 있어서 데이터 간의 관계를 표현하는 것
-- 데이터의 중복성: 데이터베이스에 저장된 데이터가 중복되어 저장되는 것

- 데이터베이스의 설계 순서
-- 요구사항 분석: 데이터베이스를 구축하기 위한 요구사항을 분석
-- 개념적 설계: 데이터베이스의 개념적 구조를 설계
-- 논리적 설계: 데이터베이스의 논리적 구조를 설계
-- 물리적 설계: 데이터베이스의 물리적 구조를 설계

- 스키마의 정의
-- 외부스키마 : 사용자의 입장에서 데이터베이스의 구조를 표현
-- 개념스키마 : 데이터베이스의 전체적인 구조를 표현
-- 내부스키마 : 데이터베이스의 물리적 저장 구조를 표현

- 스키마에서 데이터의 독립성
-- 논리적 데이터 독립성: 데이터베이스의 논리적 구조를 변경해도 응용 프로그램은 변경하지 않아도 됨
-- 물리적 데이터 독립성: 데이터베이스의 물리적 저장 구조를 변경해도 응용 프로그램은 변경하지 않아도 됨

- 데이터 모델링
-- 데이터 모델링: 데이터베이스를 구축하기 위한 요구사항을 분석하여 데이터베이스의 논리적 구조를 설계하는 과정
-- 개념적 데이터 모델링: 데이터베이스의 전체적인 논리적 구조를 설계
-- 논리적 데이터 모델링: 데이터베이스의 논리적 구조를 설계
-- 물리적 데이터 모델링: 데이터베이스의 물리적 저장 구조를 설계

- 관계형 데이터베이스
-- 관계형 데이터베이스: 데이터를 테이블 형태로 저장하고, 테이블 간의 관계를 통해 데이터를 연결하는 데이터베이스
-- 속성: 테이블의 열
-- 튜플: 테이블의 행

- 릴레이션 구조와 관련된 용어
-- 릴레이션: 테이블
-- 튜플: 테이블의 행
-- 속성: 테이블의 열
-- 도메인: 속성의 값으로 사용할 수 있는 값의 집합
-- 도메인의 원자값: 도메인의 원소
-- 도메인의 차수: 도메인의 원자값의 개수
-- 릴레이션 스키마: 릴레이션의 구조를 정의한 것
-- 릴레이션 인스턴스: 릴레이션에 저장된 데이터

- 관계형 데이터베이스의 특징
-- 데이터 중복 최소화: 데이터베이스에 저장된 데이터는 중복되어 저장되지 않음
-- 데이터 무결성 유지: 데이터베이스에 저장된 데이터는 무결성을 유지해야 함
-- 데이터 일관성 유지: 데이터베이스에 저장된 데이터는 일관성을 유지해야 함
-- 데이터 독립성 유지: 데이터베이스에 저장된 데이터는 독립성을 유지해야 함

- 관계
-- 관계: 릴레이션 간의 연관성을 표현하는 것

- 키의 개념
-- 키: 릴레이션에서 튜플을 유일하게 식별할 수 있는 속성 또는 속성의 집합
-- 키의 필요성
--- 키를 사용하면 릴레이션에서 튜플을 유일하게 식별할 수 있음

- 후보키
-- 후보키: 릴레이션에서 튜플을 유일하게 식별할 수 있는 최소한의 속성 또는 속성의 집합
-- 후보키의 성질
--- 유일성: 튜플을 유일하게 식별할 수 있어야 함
--- 최소성: 유일성을 만족하는 속성 또는 속성의 집합은 더 이상 줄일 수 없어야 함

- 기본키
-- 기본키: 후보키 중에서 선택한 키
-- 기본키의 성질
--- NULL 값을 가질 수 없음
--- 중복된 값을 가질 수 없음
--- 변경될 수 없음

- 대체키
-- 대체키: 후보키 중에서 기본키로 선택되지 않은 키
-- 대체키의 성질
--- NULL 값을 가질 수 있음
--- 중복된 값을 가질 수 있음
--- 변경될 수 있음

- 외래키
-- 외래키: 다른 릴레이션의 기본키를 참조하는 속성
-- 외래키의 성질
--- NULL 값을 가질 수 있음
--- 중복된 값을 가질 수 있음
--- 변경될 수 있음

- 키 종류 정리
-- 후보키: 릴레이션에서 튜플을 유일하게 식별할 수 있는 최소한의 속성 또는 속성의 집합
-- 기본키: 후보키 중에서 선택한 키
-- 대체키: 후보키 중에서 기본키로 선택되지 않은 키
-- 외래키: 다른 릴레이션의 기본키를 참조하는 속성

- 데이터베이스 관리 시스템
-- 기존의 파일 시스템이 갖는 데이터의 종속성과 중복성의 문제를 해결하기 위해 제안된 시스템으로 모든 응용 프로그램들이 데이터베이스를 공용할 수 있도록 관리해주는 소프트웨어
-- 데이터를 편리하게 저장하고 효율적으로 관리하고 검색할 수 있는 환경을 제공해주는 소프트웨어
-- 데이터베이스의 생성과 관리를 담당하는 소프트웨어 패키지

- 데이터베이스 관리 시스템의 구성요소
-- 데이터베이스: 데이터베이스 관리 시스템이 관리하는 데이터의 집합
-- 데이터베이스 관리 시스템: 데이터베이스를 관리하는 소프트웨어
-- 데이터베이스 언어: 데이터베이스 관리 시스템과 사용자 간의 인터페이스를 제공하는 언어
-- 데이터베이스 응용 프로그램: 데이터베이스 관리 시스템을 사용하여 데이터베이스를 관리하는 응용 프로그램

- DBMS 의 장단점
-- 장점
--- 데이터의 무결성을 보장
--- 데이터의 중복을 최소화
--- 데이터의 독립성을 보장
--- 데이터의 보안성을 보장
--- 데이터를 동시 공유할 수 있음
--- 장애 발생시 회복 가능
--- 응용 프로그램 개발 비용 감소
-- 단점
--- 데이터베이스 관리 시스템의 구축 비용이 많이 듬
--- 백업과 회복 방법이 복잡
--- 중앙 집중 관리로 인한 취약점이 존재함

- dbms 의 발전
-- 계층형 데이터베이스
--- 데이터베이스를 계층적으로 구성하여 데이터를 관리하는 방식
-- 관계형 데이터베이스
--- 데이터베이스를 테이블의 집합으로 구성하여 데이터를 관리하는 방식
-- 객체지향 데이터베이스
--- 데이터베이스를 객체의 집합으로 구성하여 데이터를 관리하는 방식
-- 객체관계형 데이터베이스
--- 데이터베이스를 객체와 관계의 집합으로 구성하여 데이터를 관리하는 방식
-- NoSQL 데이터베이스
--- 데이터베이스를 키-값 쌍의 집합으로 구성하여 데이터를 관리하는 방식

- DBMS 의 필수기능
-- 정의기능: 모든 응용 프로그램들이 요구하는 데이터 구조를 지원하기 위해 db 에 저장될 데이터의 형과 구조에대한 정의 이용방식, 제약 조건등을 명시하는 기능
-- 조작기능: 데이터베이스에 데이터를 저장하고 검색, 갱신, 삽입, 삭제기능
-- 제어기능: 데이터베이스의 무결성을 유지하고 데이터의 독립성을 보장하는 기능
-- 추출기능: 데이터베이스에서 데이터를 추출하는 기능


- 관계대수
-- 원하는 결과를 얻기 위해 릴레이션의 처리과정을 순서대로 기술하는 언어 (절차 언어)
-- 관계대수의 일반 집합 연산자
--- 합집합 연산자: 두 릴레이션의 합집합을 구하는 연산자
--- 교집합 연산자: 두 릴레이션의 교집합을 구하는 연산자
--- 차집합 연산자: 두 릴레이션의 차집합을 구하는 연산자
--- 카티션 프로덕트 연산자: 두 릴레이션의 각 튜플을 모두 연결해 만들어진 새로운 튜플 반환
(모든 경우의 수를 다 표현함)

-- 순수 관계 연산자
--- 셀렉트 연산자: 릴레이션에서 특정 조건을 만족하는 튜플만을 선택하여 구성하는 연산자
--- 프로젝션 연산자: 릴레이션에서 주어진 속성들의 값으로만 구성된 튜플들을 반환
--- 조인 연산자: 두 릴레이션에서 주어진 속성들의 값이 같은 튜플들을 연결해 만들어진 새로운 튜플들을 반환
--- 디비전 연산자: 한쪽에 조건을 만족하는 조건을 뽑아내는 연산자


SQL 의 정의와 종류 
-- 정의: db 관리 시스템에서 데이터를 관리하기위해 사용되는 표준 프로그래밍 언어
-- 종류: DDL, DML, DCL
-- 특징: 데이터베이스를 관리하기 위한 표준 언어로서, 데이터베이스를 생성, 삭제, 수정, 조회하는데 사용되는 언어

- DDL (Data Definition Language)
-- 데이터베이스의 구조를 정의하는 언어
-- 데이터베이스를 생성, 삭제, 수정하는데 사용되는 언어

- DML (Data Manipulation Language)
-- 데이터베이스의 데이터를 조작하는 언어
-- 데이터베이스에 데이터를 삽입, 삭제, 갱신하는데 사용되는 언어

- DCL (Data Control Language)
-- 데이터베이스의 접근 권한을 관리하는 언어
-- 데이터베이스에 접근할 수 있는 사용자를 관리하는데 사용되는 언어


- sql 과 프로그래밍 언어의 차이점
-- sql 은 데이터베이스를 관리하기 위해 사용되는 표준 언어이며, 프로그래밍 언어는 프로그램을 개발하기 위해 사용되는 언어


- SELECT 문
-- SELECT 문의 활용
--- SELECT * FROM 테이블명; (모든 속성을 조회)

- 조건 검색 
-- WHERE 절의 활용
--- SELECT * FROM 테이블명 WHERE 조건식; (조건식에 해당하는 튜플만 조회)

- 복합 조건
-- AND, OR, NOT 연산자의 활용
--- SELECT * FROM 테이블명 WHERE 조건식1 AND 조건식2; (조건식1과 조건식2를 모두 만족하는 튜플만 조회)

- 정렬
-- ORDER BY 절의 활용
--- SELECT * FROM 테이블명 ORDER BY 속성명; (튜플을 속성명의 오름차순으로 정렬하여 조회)

- 집계와 그룹화
-- 집계함수의 활용
--- SELECT 집계함수(속성명) FROM 테이블명; (특정 속성의 집계값을 조회)

- 조인
-- 조인의 활용
--- SELECT * FROM 테이블명1, 테이블명2 WHERE 조건식; (조건식을 만족하는 테이블명1과 테이블명2의 튜플을 연결하여 조회)

- 집합 연산
-- UNION, INTERSECT, MINUS 연산자의 활용
--- SELECT * FROM 테이블명1 UNION SELECT * FROM 테이블명2; (테이블명1과 테이블명2의 합집합을 조회)
--- SELECT * FROM 테이블명1 INTERSECT SELECT * FROM 테이블명2; (테이블명1과 테이블명2의 교집합을 조회)
--- SELECT * FROM 테이블명1 MINUS SELECT * FROM 테이블명2; (테이블명1과 테이블명2의 차집합을 조회)


- 데이터 정의어
-- CREATE: 데이터베이스 객체를 생성
--- CREATE TABLE 테이블명 (속성명1 속성타입1, 속성명2 속성타입2, ...);
-- ALTER: 데이터베이스 객체를 수정
--- ALTER TABLE 테이블명 ADD 속성명 속성타입;
-- DROP: 데이터베이스 객체를 삭제
--- DROP TABLE 테이블명;

- 데이터 조작어
-- INSERT: 테이블에 튜플을 삽입
--- INSERT INTO 테이블명 VALUES (값1, 값2, ...);
-- UPDATE: 테이블의 튜플을 갱신
--- UPDATE 테이블명 SET 속성명 = 값 WHERE 조건식;
-- DELETE: 테이블의 튜플을 삭제
--- DELETE FROM 테이블명 WHERE 조건식;

- 데이터 제어어
-- GRANT: 사용자에게 권한을 부여
--- GRANT 권한 ON 객체 TO 사용자;
-- REVOKE: 사용자에게 부여된 권한을 취소
--- REVOKE 권한 ON 객체 FROM 사용자;


- 데이터 이상: 하나의 릴레이션 내에 데이터의 중복과 종속으로 인해 발생되는 문제점
-- 삽입 이상: 새로운 튜플을 삽입할 때 원하지 않는 값이 삽입될 수 있는 현상
-- 삭제 이상: 튜플을 삭제할 때 원하지 않는 튜플까지 삭제될 수 있는 현상
-- 갱신 이상: 튜플을 갱신할 때 원하지 않는 튜플까지 갱신될 수 있는 현상


- 데이터의 함수적 종속성: A 의 값을 알면 B 의 값을 알수있거나 A 값에 따라 B 의 값이 달라진다면 B 는 A에 종속되어있음
-- 함수적 종속성: 릴레이션의 속성들 사이에 존재하는 종속성
-- 완전 함수적 종속성: 릴레이션의 모든 속성들이 결정자가 되는 종속성
-- 부분 함수적 종속성: 릴레이션의 일부 속성들이 결정자가 되는 종속성
-- 이행적 함수적 종속성: A 를 알면 B 를 알 수 있고, B 를 알면 C 를 알 수 있을 때 A 는 C 에 함수적 종속성이 있다고 함


-데이터 정규화 고려 사항
-- 실전에서의 정규화 전략
--- 정규화 전략의 결정은 데이터의 특성과 응용 시스템의 특성을 고려하여 결정

-- 데이터 정규화의 유형
--- 1차 반복되는 속성 제거 
--- 2차 부분함수 종속성 제거
--- 3차 이행함수 종속성 제거 
--- BCNF 결정자 함수 종속성 제거
--- 4차 다중값 종속성 제거
--- 5차 결합 종속성 제거


데이터 정규화의 절차
-- 1차 정규화: 릴레이션에 존재하는 모든 속성들이 원자값만을 가지도록 분해
-- 2차 정규화: 릴레이션에 존재하는 모든 속성들이 완전 함수적 종속을 만족하도록 분해
-- 3차 정규화: 릴레이션에 존재하는 모든 속성들이 이행적 함수적 종속을 만족하도록 분해
-- BCNF 정규화: 릴레이션에 존재하는 모든 속성들이 BCNF를 만족하도록 분해
-- 4차 정규화: 릴레이션에 존재하는 모든 속성들이 다중값 종속을 만족하도록 분해
-- 5차 정규화: 릴레이션에 존재하는 모든 속성들이 결합 종속을 만족하도록 분해


- 역정규화의 정의
-- 역정규화: 데이터 정규화를 통해 분해된 릴레이션을 다시 결합하여 정규화 전의 릴레이션으로 복원하는 과정
-- 역정규화의 목적: 데이터베이스의 성능을 향상시키기 위해 데이터 정규화를 통해 분해된 릴레이션을 다시 결합하는 과정




================================================================

2023 데이터통신개론 

- 정보통신과 데이터 통신
-- 정보통신: 정보를 주고 받는 통신
-- 데이터 통신: 데이터를 주고 받는 통신
-- 원격 통신: 물리적으로 떨어져 있는 두 장치 간의 통신

- 통신의 역사
-- 원시시대의 통신: 화음, 손짓, 신호등
-- 언어의 발달: 언어를 통한 통신
-- 문자의 발달: 문자를 통한 통신
-- 원격통신: 멀리 있는 사람과의 통신 (봉화, 세마포르)
-- 운송의 발달: 운송 수단을 통한 통신 (비둘기, 역마, 기차)
-- 전기통신의 시작: 전기를 통한 통신 (모오스 부호)
-- 인쇄전기통신의 발달: 인쇄를 통한 통신 (인쇄기, 텔레그래피)
-- 무선전기통신의 발달: 무선을 통한 통신 (라디오, 무선전화)

- 컴퓨터의 발전
-- 컴퓨터의 세대별 분류
--- 1세대 컴퓨터: 진공관을 사용한 컴퓨터
--- 2세대 컴퓨터: 트랜지스터를 사용한 컴퓨터
--- 3세대 컴퓨터: 집적회로를 사용한 컴퓨터
--- 4세대 컴퓨터: 초중고속 연산을 지원하는 컴퓨터
--- 5세대 컴퓨터: 인공지능을 지원하는 컴퓨터

- 데이터 통신의 개념
-- 데이터 통신: 데이터를 주고 받는 통신
-- 데이터 통신의 특징
--- 데이터 통신은 정보 통신의 일종

- 컴퓨터 종류
-- 데스크탑 컴퓨터: 개인용 컴퓨터
-- 노트북 컴퓨터: 개인용 컴퓨터
-- 서버 컴퓨터: 서버용 컴퓨터
-- 스마트폰: 개인용 컴퓨터
-- 태블릿 컴퓨터: 개인용 컴퓨터
-- 스마트워치: 개인용 컴퓨터
-- Microcomputer: 개인용 컴퓨터
-- Mini Computer: 서버용 컴퓨터
-- Mainframe Computer: 서버용 컴퓨터
-- Super Computer: 서버용 컴퓨터

- 데이터통신의 발전
-- SAGE 시스템: 미국의 항공전투기의 제어를 위한 컴퓨터 통신 시스템
-- SABRE 시스템: 미국의 항공예약 시스템
-- ARPANET: 미국의 국방부가 개발한 컴퓨터 네트워크 (최초의 패킷교환망 유선망)
-- ALOHA 시스템: 미국의 무선망 (최초의 패킷교환망 무선망)
-- SNA: IBM 사가 개발한 컴퓨터간 접속 표준

- 정보통신 기술
-- 정보표현의 기술, 정보처리의 기술, 정보저장의 기술, 정보전송의 기술
-- 인간의 감정, 사상, 지식등의 정보를 서로 교환하는데있어서 시간적,공간적 제약을 극복하고자하는 모든기술

- 5감 통신의 가능성
-- 시각감: 영상통신
-- 청각감: 음성통신
-- 미각감: 음식통신
-- 후각감: 향기통신
-- 촉각감: 터치통신

- 데이터 통신 시스템의 5가지 구성 요소
-- 송신기, 수신기, 메시지, 전송매체, 프로토콜

- 데이터 처리 방식
-- 데이터 처리 방식의 분류
--- 일괄처리: 데이터를 일정한 시간 간격으로 일괄적으로 처리하는 방식
--- 온라인: 데이터를 실시간으로 처리하는 방식
--- 분산처리: 데이터를 여러 대의 컴퓨터에 분산하여 처리하는 방식

- 데이터 전송계
-- 단말장치,전송회선,통신제어장치
-- 단말장치: DTE (Data Terminal Equipment) 데이터 터미널 장치, 입출력 기능, 전송제어기능, 기억기능 등을 수행
-- 단말장치의 구성: 입출력 장치와 전송제어 장치로 구성
-- 전송제어 장치: Transmission Control Unit, 데이터 전송 시에 발생하는 오류를 검출 혹은 정정하는 장치

- 신호 변환 장치 DCE (Data Circuit-terminating Equipment), 데이터를 전송에 적합한 신호로 변환하는 장치
-- DCE의 구성: 데이터 전송 회선과 전송제어 장치로 구성
-- 신호 변환 장치 DSU / CSU : 모뎀: Modem, 데이터를 전송에 적합한 신호로 변환하는 장치
-- 통신 제어 장치
-- 통신 소프트웨어: 통신 제어 장치의 기능을 소프트웨어로 구현한 것

- 네트워크의 필요성 및 정의
-- 네트워크의 필요성
--- 네트워크의 필요성: 네트워크를 통해 정보를 공유하고, 정보를 효율적으로 관리할 수 있음
-- 네트워크의 정의
--- 네트워크의 정의: 두 대 이상의 컴퓨터가 연결되어 정보를 교환할 수 있는 시스템
-- 거리에 따른 분류: LAN, MAN, WAN
--- 근거리 통신망: LAN (Local Area Network)
--- 광역 통신망: WAN 공중망 (통신 사업자가 구축한 망을 임대해 사용)

- 프로토콜
-- 프로토콜의 정의
--- 프로토콜의 정의: 컴퓨터 간의 통신을 위한 표준 규약
-- 프로토콜의 종류
--- 프로토콜의 종류: TCP/IP, OSI 7계층 모델
-- 프로토콜의 주요 요소: 구분, 의미, 타이밍
-- 프로토콜의 주요 기능: 캡슐화, 흐름제어, 오류제어, 동기화, 경로지정
--- 캡슐화: 주소나 오류검출 부호 등과 같은 프로토콜 제어정보를 부가하는 것, 보통 헤더라고 부름


- OSI 7 Layer model
-- OSI 7 Layer model의 정의
--- OSI 7 Layer model의 정의: 국제표준화기구에서 개발한 통신 프로토콜의 7계층 모델
-- OSI 7 Layer model의 구성
--- OSI 7 Layer model의 구성: 물리계층, 데이터링크계층, 네트워크계층, 전송계층, 세션계층, 표현계층, 응용계층
-- OSI 7 Layer model의 특징
--- OSI 7 Layer model의 특징: 계층화된 구조, 계층간의 독립성, 계층간의 상호작용, 계층간의 통신은 프로토콜을 통해 이루어짐

1,2,3 정보의 전송 기능 담당, 실제로 데이터가 공간을 이동하는데 관련된 기능을 수행
-1 물리 계층 (Physical Layer) 주요기능 : 물리적인 전송로를 제공
-2 데이터 링크 계층 (Data Link Layer) 주요기능 : 인접 노드 사이의 데이터 전송 기능 수행
-3 네트워크 계층 (Network Layer) 주요기능 : 호스트 간의 데이터 전송 기능, 데이터의 전송 경로 설정

4 상,하위 계층을 연결하는 기능
-4 전송 계층 (Transport Layer) 주요기능 : 프로세스와 프로세스 간의 전달

5,6,7 정보의 처리 기능 담당, 실제로 데이터가 공간을 이동하는데 관련된 기능을 수행
-5 세션 계층 (Session Layer) 주요기능 : 네트워크의 대화조정, 동기화 지점 설정
-6 표현 계층 (Presentation Layer) 주요기능 : 데이터의 표현을 공통된 형식으로 변환, 압축, 암후화 기능
-7 응용 계층 (Application Layer) 주요기능 : 파일 전송이나 이메일과 같은 End-user service 제공

- 계층화 구조와 캡슐화
-- 계층화 구조와 캡슐화의 정의
--- 계층화 구조와 캡슐화의 정의: 계층화 구조는 프로토콜을 계층으로 나누어 설계한 것, 캡슐화는 프로토콜의 헤더를 추가하는 것
-- 계층화 구조와 캡슐화의 특징
--- 계층화 구조와 캡슐화의 특징: 계층화 구조는 계층간의 독립성을 보장, 계층간의 통신은 프로토콜을 통해 이루어짐, 캡슐화는 프로토콜의 헤더를 추가함으로써 프로토콜의 기능을 수행할 수 있음


- OSI 모델의 계층간 상호 작용
-- 중간 노드들은 3계층까지만 동작
-- 대등-대-대등 프로세스 (peer-to-peer process)


- 프로토콜 데이터 단위 (PDU)
-- 계층
Media Layers
--- 물리계층: 비트
--- 데이터링크계층: 프레임
--- 네트워크계층: 패킷/데이터그램

--- 전송계층: 세그먼트

Host Layers
--- 세션계층: 메시지
--- 표현계층: 메시지
--- 응용계층: 메시지

================================================================

2023 인터넷기반기술 XML 
extensible markup language 
- XML의 정의
-- XML의 정의: 데이터를 저장하고, 전송하고, 처리하기 위한 표준 언어
--- 문서 전체에 포함된 정보가 아닌 어떤 태그에 관련된 정보를 기반으로 함
-- 특징: 개발자는 여러가지 응용프로그램으로부터 구조화된 데이터를 로컬 컴퓨팅 및 프레젠테이션을 위해 데스크톱으로 전달할 수 있음, XML 을 사용해 특정 응용프로그램에 대한 독특한 데이터 형식을 만들 수 있음, 서버 간의 구조화된 데이터 전송을 위한 이상적인 형식임

- XML 탄생 전: HTML 과 SGML 과 같은 언어들이 있었음
-- HTML: 웹페이지를 만들기 위한 언어
-- SGML: 문서를 만들기 위한 언어

- XML 의 효과
-- 통합의 필요성 대두
--- 기업간 거래시 해당 정보를 교환하기 위해 공통의 언어를 제공함으로 앱 과정을 통합하고 단순화할 필요성이 대두되고있음
--- 공급 체인은 자동화되고 모든 거래 파트너로 확장될 수 있음
--- 거래 파트너들이 연결되기때문에 고객 입장에선 보다 풍부한 정보를 통해 구매결정을 내릴 수 있음
-- 데이터베이스 지원
--- 사용자가 구조화된 db 를 뜻대로 조작 가능
-- 정확한 정보 검색 지원
--- 검색엔진이 xml 을 이용해 정보를 더 정확하게 검색할 수 있음(검색엔진의 효율성을 높이고 불필요한 접속으로 인한 웹 서버의 부담을 감소시키는 효과를 가져옴)
-- 비즈니스 데이터 교환
--- xml 을 이용해 비즈니스 데이터를 교환할 수 있음
-- 웹 서비스 지원
--- 웹 서비스는 xml 을 이용해 웹 서버와 클라이언트 간의 통신을 가능하게 함


- XML 문서의 종류
-- 첫 시작은 <?xml version="1.0" encoding="UTF-8"?> 시작함

--EBNF (Extended Backus-Naur Form) : 문법을 표현하는 방법
--- 기호 ::= 표현식 
EX CODE
Char a ~ z 까지 한 문자를 갖는 표현식
Char ::= [a-z]
EX CODE
VersionNum 이 0~9 까지 한 문자를 갖는 표현식
VersionNum ::= [0-9]
EX CODE
World 가 version 이라는 고정 문자열을 갖는 표현식
World ::= version

-- 표현식
A? : A가 0번 또는 1번 나타남 (A가 있을 수도 있고 없을 수도 있음)
A* : A가 0번 이상 나타남 (A가 0번 이상 나타남) 여러개가 와도 됨
A+ : A가 1번 이상 나타남 (A가 1번 이상 나타남) 한개 이상이 와야함
A|B : A 또는 B가 나타남 (A 또는 B가 나타남)


-- DTD (Document Type Definition) : 문서의 구조를 정의하는 방법
-- XML Schema : 문서의 구조를 정의하는 방법



================================================================

2023 웹기반시스템과S/W활용

WBI (Web Based Instruction) : 웹의 등장과 함께 부각된 새로운 교수학습 방법으로 온라인 형태의 교수학습방법

웹기반교육의 특징
- 웹기반교육의 특징
-- 학습자 상호 간이나 학습자와 교수자 간의 상호작용이 가능
-- 멀티미디어를 제공함 : 오디오, 비디오, 애니메이션, 텍스트 등
-- 개방적임 : 학습자가 언제 어디서든지 학습할 수 있음
-- 온라인 검색이 가능함 : 학습자가 원하는 정보를 검색할 수 있음
-- 정보나 자료를 수시로 수정및 보완이 가능: HTML 을 이용해 웹페이지를 만들면 수정이 쉬움
-- 학습자는 최신의 정보를 이용하고 정보를 공유할수있음
-- 호환성이 뛰어남
-- 이용하기가 쉬움


- 웹 기반교육과 유사한 용어
-- Educational Technology : 교육과정에 정보기술을 적용하는 것
-- e-Learning : 웹 기반 교육
-- m-Learning : 모바일 기기를 이용한 교육
-- Blended Learning : 온라인과 오프라인을 결합한 교육
-- Distance Learning : 원격으로 교육을 제공하는 것
-- Virtual Learning Environment : 가상의 학습환경
-- Smart Learning : 지능형 학습
-- Online Learning : 온라인으로 교육을 제공하는 것
-- Web Based Learning : 웹 기반 교육
-- EdTech : 교육과정에 정보기술을 적용하는 것
-- Cyber Learning : 인터넷을 이용한 학습


- 웹기반교육과 ict 환경
-- 웹기반교육은 ict 환경에서 가능한 교육방법임
-- ict 환경은 웹기반교육을 가능하게 함
-- ict 환경은 웹기반교육을 효과적으로 이용할 수 있도록 지원함


- 디지털 컨버전스
-- 디지털 컨버전스: 디지털 컨버전스란 디지털 기술을 이용해 기존의 비디지털 기술을 디지털 기술로 변환하는 것을 말함


- STEAM: 전통적인 미디어와 IT 기술의 융합
-- STEAM: Science, Technology, Engineering, Art, Mathematics


- 웨어러블 사회 iot
-- 웨어러블 사회: 웨어러블 사회란 사람들이 웨어러블 기기를 이용해 정보를 수집하고, 정보를 공유하고, 정보를 분석하고, 정보를 활용하는 사회를 말함
-- iot: iot란 사물인터넷을 말함


- 유비쿼터스 사회
-- 유비쿼터스 사회: 유비쿼터스 사회란 사람들이 어디에 있든지 정보를 얻고, 정보를 공유하고, 정보를 분석하고, 정보를 활용할 수 있는 사회를 말함


- 웹기반교육의 구성요소
-- 교육철학적 특성
-- 웹기반교육의 특성
-- 교수자의 역할에 따른 분류
--- 강의 모형: 교수자가 학습자에게 강의를 진행하는 방식
--- 촉진 모형: 교수자가 학습자에게 학습을 촉진시키는 방식
--- 관리 모형: 교수자가 학습자에게 학습을 관리하는 방식


- 웹기반 교수-학습 체제 설계의 절차적 단계 : 분석 -> 설계 -> 제작 -> 운영 -> 평가


- 컴퓨터시스템의 구성 요소
-- Motherboard : 컴퓨터의 기본적인 구성요소
-- CPU : 컴퓨터의 뇌
-- power supply : 전원 공급 장치
-- cooling fan : 냉각 장치
-- internal speaker : 내장 스피커
-- drive bay : 드라이브 슬롯
-- expansion slot : 확장 슬롯
-- ram : 램
-- network card : 네트워크 카드


- 입력 장치
-- 키보드 : 키보드는 문자, 숫자, 기호 등을 입력하는 장치
-- 마우스 : 마우스는 컴퓨터 화면에서 원하는 위치를 지정하는 장치
-- 스캐너 : 스캐너는 문서나 사진 등을 컴퓨터로 입력하는 장치
-- 터치스크린 : 터치스크린은 손가락으로 화면을 터치하여 입력하는 장치
-- 펜 : 펜은 손가락이 아닌 펜으로 화면을 터치하여 입력하는 장치
-- 마이크 : 마이크는 음성을 입력하는 장치
-- 웹캠 : 웹캠은 영상을 입력하는 장치
-- 디지털 카메라 : 디지털 카메라는 사진을 입력하는 장치
-- 디지털 캠코더 : 디지털 캠코더는 영상을 입력하는 장치
-- 그래픽 태블릿 : 그래픽 태블릿은 손가락으로 화면을 터치하여 입력하는 장치


- 출력 장치
-- 모니터 : 모니터는 컴퓨터 화면을 출력하는 장치
-- 프린터 : 프린터는 문서를 출력하는 장치
-- 스피커 : 스피커는 소리를 출력하는 장치
-- 헤드폰 : 헤드폰은 소리를 출력하는 장치
-- 프로젝터 : 프로젝터는 영상을 출력하는 장치
-- HMD : HMD는 가상현실을 출력하는 장치


- 저장 장치
-- 하드디스크 : 하드디스크는 컴퓨터에 저장된 정보를 저장하는 장치
-- USB 메모리 : USB 메모리는 컴퓨터에 저장된 정보를 저장하는 장치
-- SSD : SSD는 컴퓨터에 저장된 정보를 저장하는 장치
-- CD-ROM : CD-ROM은 컴퓨터에 저장된 정보를 저장하는 장치
-- DVD-ROM : DVD-ROM은 컴퓨터에 저장된 정보를 저장하는 장치
-- NetworkAttachedStorage: 양쪽 화면에 나타나는 약간의 위치 차이에의해 3차원 물체를 보는것과같은 느낌
-- Remote Storage : 원격 저장소는 컴퓨터에 저장된 정보를 저장하는 장치


- 광저장장치 ODD : Optical Disk Drive
-- CD -> DVD -> BD

- 저장원리 및 단위
-- kilobit : 1,000 bit
-- ASCII : 정보 교환을 위한 미국 표준 코드


- 연결장치
-- USB : USB는 컴퓨터와 외부 장치를 연결하는 장치
-- SCSI : SCSI는 컴퓨터와 외부 장치를 연결하는 장치
-- eSATA : eSATA는 컴퓨터와 외부 장치를 연결하는 장치


- Flipped learning : 학생들이 미리 수업을 듣고, 수업 시간에는 수업 내용을 활용한 실습을 진행하는 학습 방식
-- Flipped learning의 장점
--- 학생들이 수업 시간에 집중할 수 있음
--- 학생들이 수업 시간에 질문을 할 수 있음
--- 학생들이 수업 시간에 실습을 할 수 있음
--- 학생들이 협동 학습을 할 수 있음
--- 학생들이 개별 학습을 할 수 있음
-- Flipped learning의 단점
--- 학생들이 미리 수업을 들어야 함
-- 개발 과정 
--- plan -> record -> share -> change -> group -> regroup -> review -> revise -> repeat


- MOOCs
-- Massive Open Online Courses : 교육자가 온라인으로 강의를 제공하고, 학생들이 온라인으로 강의를 수강하는 교육 방식


- 초거대 AI 
-- 초거대 AI : 인간의 지능을 모방한 인공지능
-- 빅데이터 처리 능력
-- 고도의 처리 능력
-- 실시간 분석

- 생성 AI
-- 새로운 컨텐츠를 생성하는 기능
-- 기존 패턴 및 정보 기반
-- 독특하고 다양한 결과물 생성

- 학습 AI
-- 맞춤형 학습
-- 지능형 튜터링 시스템
-- 예측 분석
-- 자동 평가 및 채점
-- 장점 
--- 효율성 향상 
--- 개인화된 학습 경험
--- 학습자 참여도 향상
--- 데이터 기반의 의사 결정
-- 단점
--- 알고리즘 개발의 편향성과 공평성
--- 윤리 및 개인 정보 보호 문제
--- 기술에 대한 의존성
--- 전문 교육의 필요성


- 4차 산업혁명
-- 4차 산업혁명 : 인공지능, 빅데이터, 사물인터넷, 클라우드 컴퓨팅 등의 기술을 기반으로 새로운 융합 기술을 개발하고, 이를 통해 새로운 가치를 창출하는 혁명
-- 4차 산업혁명의 특징
--- 자율진화, 무인 의사결정, 만물의 데이터화, 실시간 반응

- 4차 산업혁명으로인한 변화 전망
-- 산업구조의 변화
-- 고용구조
-- 삶의 모습과 환경


- 10대 미래유망기술
-- iot 기반 상황 인식형 조광기술
-- 능동제어형 소음 저감 기술
-- ai 팩트 체킹 보조 기술
-- 원전 사고 대응 시스템
-- 비방사성 비파괴 검사 기술
-- 초미세먼지 제거 기술
-- 친환경 녹조-적조 제거 기술
-- 생활폐기물 첨단 분류- 재활용 시스템
-- 환경변화 실시간 입체 관측 기술
-- 미생물 활용 환경복원 기술

- 사람 중심 스마트 사회 구현 10대 미래유망 기술
-- 반응형 주택 기술
-- 라이프로그 개인비서 소프트웨어 기술
-- 커넥티드카 기술
-- 모듈형 대중교통 시스템
-- 무선 전력 전송 기술
-- 스마트 타투 기술
-- 소프트 로봇 기술
-- 스마트 팜 기술
-- 인공지능 보안 기술
-- 혼합 현실 기술

- 제조업 경쟁력 강화를 위한 소재분야 10대 미래유망기술
-- 친환경 바이오플라스틱 필름
-- 손실된 인체감각을 대체하는 기기용 소재
-- 3d 프린팅 인공장기
-- 불이 안나는 고성능 고체전해질
-- 수송용 고속 충-방전이 가능한 배터리
-- 더 이상 무겁지 않은 초경량 수송체
-- 1억도시 이상의 극한의 환경을 견디는 차세대 핵융합 소재
-- 스트레처블 디스플레이
-- 자율적으로 수명을 제어하는 화학소재
-- 완전 직물형 웨어러블 소자


- 혁신적 기술의 확산
-- 휴먼 임파워먼트
-- 초연결에 의한 혁신
-- 환경 리스크 심화
-- 사회 복잡성의 진화
-- 경제 시스템의 재편

- 24개 혁신기술의 기술확산점 도출결화
-- 멀티콥터 드론
-- 실감형 가상-증강 현실
-- 스마트 팩토리
-- 만물인터넷
-- 3d 프린팅
-- 빅데이터 활용 개인 맞춤형 의료
-- 스마트 그리드
-- 초고용량 배터리
-- 극한 성능용 탄소섬유 복합 재료
-- 롤러블 디스플레이
-- 희소금속 리사이클링
-- 웨어러블형 보조 로봇
-- 자율주행 자동차
-- 포스트 실리콘 반도체
-- 인지 컴퓨팅
-- 이산화 탄소 포집 저장
-- 유전자 치료
-- 줄기세포
-- 지능형 로봇
-- 인공 장기
-- 양자 컴퓨팅
-- 뇌-컴퓨터-인터페이스
-- 인공광합성
-- 초고속 튜브 트레인


- 5대 글로벌 메가 트렌드
-- 세계 경제력의 변화
-- 기후 변화와 자원 부족
-- 기술 혁신
-- 인구와 사회 변화
-- 급속한 도시화


- 10대 글로벌 기술 트렌드
-- 인공지능 및 기계학습
-- 5g 네트워크
-- 엣지 컴퓨팅: 데이터는 중앙 지붖ㅇ식 위치가아닌 네트워크 엣지(가장자리)에서 처리됨
-- 가상 및 증강 현실
-- 양자 컴퓨팅
-- 블록체인 기술
-- 로봇 공학 및 자동화
-- 사물 인터넷
-- 맞춤형 건강 및 웰빙 기술



================================================================

2023 안드로이드프로그래밍

스마트폰 개발 환경
- 안드로이드 : java, kotlin, c++
-- 개발도구 : 안드로이드 스튜디오
- 아이폰: objective C
-- 개발도구 : Xcode
- 윈도우폰: C#, VB.NET
-- 개발도구 : Visual Studio


- 안드로이드 버전
-- 알파 : 1.0 , API 레벨 1, 발표일자 2008년 09월 
-- 베타 : 1.1 , API 레벨 2, 발표일자 2009년 02월
-- 컵케이크 : 1.5 , API 레벨 3, 발표일자 2009년 10월
-- 도넛 : 1.6 , API 레벨 4, 발표일자 2010년 02월
-- 이클레어 : 2.0 , API 레벨 5, 발표일자 2010년 10월
-- 프로요거트 : 2.2 , API 레벨 8, 발표일자 2010년 11월
-- 진저브레드 : 2.3 , API 레벨 9, 발표일자 2011년 02월
-- 허니콤 : 3.0 , API 레벨 11, 발표일자 2011년 02월
-- 아이스크림샌드위치 : 4.0 , API 레벨 14, 발표일자 2011년 10월
-- 젤리빈 : 4.1 , API 레벨 16, 발표일자 2012년 07월
-- 킷캣 : 4.4 , API 레벨 19, 발표일자 2013년 10월
-- 롤리팝 : 5.0 , API 레벨 21, 발표일자 2014년 11월
-- 마시멜로 : 6.0 , API 레벨 23, 발표일자 2015년 10월
-- 누가 : 7.0 , API 레벨 24, 발표일자 2016년 08월
-- 오레오 : 8.0 , API 레벨 26, 발표일자 2017년 08월
-- 파이 : 9.0 , API 레벨 28, 발표일자 2018년 08월

- 안드로이드의 주요한 기능
-- 앱 프레임워크를 통해 제공되는 API 를 사용해 코드를 재사용하고 효율적이고 빠른 앱 개발 가능
-- 모바일 기기에 최적화된 달빅 또는 아트런 타임 제공
-- 2d 그래픽 및 삼차원 그래픽 최적화해 표현
-- 모바일용 디비 SQLite 제공
-- 각종 오디오, 비디오, 및 이미지 형식을 지원
-- 모바일 기기에 내장된 각종 하드웨어 지원
-- 이클립스 또는 안드로이드 스튜디오와 같은 통합 개발 환경 제공

- 안드로이드의 특징
-- 리눅스 기반
-- 자바를 앱 개발 언어 사용
-- 안드로이드 SDK 에서 많은 라이브러리를 포함해 개발이 용이함
-- 오픈소스를 지향하기에 운영체제로부터 관련문서, 개발도구등 거의 모든것을 무료로 사용가능
-- 지속적인 업그레이드 제공

- 안드로이드 구조
-- 응용 프로그램 : 안드로이드 스마트폰에서 사용할 수 있는 일반적인 응용 프로그램
--- 웹 브라우저, 달력, 구글맵, 연락처, 게임 등 사용자 입장에서 가장 많이 사용됨
--- 자바로 제작됨
-- 응용 프로그램 프레임워크 : 안드로이드 응용 프로그램을 개발할 때 사용하는 API
-- 안드로이드 런타임 : 자바 코어 라이브러리와 달빅 가상 머신 or 아트 런타임으로 구성됨
-- 라이브러리:  안드로이드에서 사용되는 여러 시스템 라이브러리
-- 리눅스 커널 : 안드로이드의 핵심 부분으로 안드로이드의 모든 기능을 제공함


- 안드로이드 개발 환경 설치 단계
-- 안드로이드 스튜디오 설치
-- 안드로이드 스튜디오 환경 설정
-- 안드로이드 SDK 업데이트 
-- AVD (Android Virtual Device) 만들기
-- 안드로이드 앱 개발















```