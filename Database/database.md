## DBMS (Database Management System)

> 데이터베이스: 
>
> - 컴퓨터 시스템에서 전자적으로 저장되고 액세스되는 데이터의 체계화된 모음
> - 여러 사람이 공유하고 사용할 목적으로 통합 관리된다.
> - 자료 항목의 중복을 없애고, 자료를 구조화하여 기억시켜놓은 자료의 집합체

> 데이터베이스의 장점:
>
> - 데이터 중복 최소화
> - 데이터 무결성 (정확한 정보를 보장)
> - 데이터 일관성
> - 데이터 독립성 (물리적/논리적)
> - 데이터 표준화
> - 데이터 보안 유지

> 데이터베이스 관리 시스템은 다수의 사용자, 응용 프로그램 및 데이터베이스 자체와 상호 작용하며 많은 양의 데이터를 관리하고 분석하는 소프트웨어이다.

<br>

## RDB (Relational Datebase)

> 관계형 데이터모델에 기초를 둔 데이터베이스

> 관계형 데이터 모델: 모든 데이터를 2차원 테이블 형태로 표현하는 데이터 모델
>
> - 테이블(table): 행(row, record, tuple)과 열(column, field)로 이루어져있음
>
>   |  id  | name  | age  |
>   | :--: | :---: | :--: |
>   |  1   | John  |  25  |
>   |  2   | Jamie |  30  |
>   |  3   |  Kim  |  19  |
>
>   <br>
>
> - 스키마(schema): 데이터베이스에서 자료의 구조, 표현방법, 관계 등 전반적인 명세를 기술한 것
>
>   | column | datatype |
>   | :----: | :------: |
>   |   id   |   INT    |
>   |  name  |   TEXT   |
>   |  age   |   INT    |
>
>   <br>
>
> - 기본키(Primary Key): 각 행(레코드)의 고유 값. ex) id

> RDBMS(Relational Database System): 관계형 데이터베이스 관리 시스템
>
> - MySQL
> - SQLite
> - PostgreSQL
> - ORACLE
> - MS SQL

<br>

## SQL (Structured Query Language)

> DBMS의 데이터 관리를 위해 설계된 쿼리언어
>
> 데이터베이스 스키마 생성 및 수정
>
> 자료의 검색 및 관리
>
> 데이터베이스 객체 접근 조정 관리
>
> - DDL(Data Definition Language)
> - DML(Data Manipulation Language)
> - DCL(Data Control Language)

