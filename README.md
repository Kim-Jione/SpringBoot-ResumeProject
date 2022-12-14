# MyBatis DB연결 세팅

### MariaDB 사용자 생성 및 권한 주기
```sql
CREATE USER 'green'@'%' IDENTIFIED BY 'green1234';
CREATE DATABASE greendb;
GRANT ALL PRIVILEGES ON greendb.* TO 'green'@'%';
```

### 테이블 생성
```sql
USE greendb;

create table user(
	id INT primary KEY auto_increment,
	username VARCHAR(20),
	password VARCHAR(20),
	role VARCHAR(10),
	created_At TIMESTAMP
);


create table recommend(
	recommend_id INT primary KEY auto_increment,
	subject_id INT,
	content LONGTEXT,
	created_At TIMESTAMP
);

create table subscribe(
	subscribe_id INT primary KEY auto_increment,
	user_id INT,
	subject_id INT, 
	created_At TIMESTAMP
);

create TABLE person(
person_id INT primary KEY AUTO_INCREMENT,
user_id INT,
person_name VARCHAR(20),
person_email VARCHAR(50),
person_phone VARCHAR(20),
is_gender BOOLEAN,
degree VARCHAR(20),
career INT,
created_At TIMESTAMP
);


create table person_skill(
  person_skill_id INT primary KEY auto_increment,
  person_id INT,
  skill VARCHAR(20),
  created_At TIMESTAMP/
);

create table resume(
  resume_id INT primary KEY auto_increment,
  person_id INT,
  photo LONGTEXT,
  introduction LONGTEXT,
  company_id INT,
  created_At TIMESTAMP
);


create table company (
	company_id INT primary KEY auto_increment,
	user_id INT,
	company_name VARCHAR(20),
	company_email VARCHAR(50),
	company_phone VARCHAR(20),
	tech VARCHAR(20),
	address LONGTEXT,
	history INT,
	introduction LONGTEXT,
	created_At TIMESTAMP
);

create table notice(
notice_id INT primary KEY auto_increment,
company_id INT,
job VARCHAR(20),
salary VARCHAR(20),
created_At TIMESTAMP
);

create table need_skill(
need_skill_id INT primary KEY auto_increment,
notice_id INT,
skill VARCHAR(20),
created_At TIMESTAMP
);



```

### 더미데이터 추가
```sql
insert into user(username, password, role, created_At) values('ssar', '1234', 'company', NOW());
insert into user(username, password, role, created_At) values('cos', '1234', 'person', NOW());
insert into recommend(subject_id, content, created_At) VALUES('1', '추천', NOW());
insert into subscribe(usgreendber_id, subject_id, created_At) VALUES('2', '3', NOW());
insert into person(user_id, person_name, person_email, person_phone, is_gender, degree, career, created_At  ) values('1', '홍길동', 'ssar@nate.com', '01000000000', 0 , '4년제', '1', NOW());
insert into person_skill(person_id, skill, created_At) VALUES('1', '자바', NOW());
insert into resume(person_id , photo , introduction , company_id, created_At) VALUES('2', '이력서', '안녕하세요', '3', NOW());
insert into company (user_id, company_name , company_email , company_phone ,tech , address , history ,  introduction , created_At) VALUES('2', '그린회사', 'cos@nate.com', '01000000000', 'C언어', '부산','2021','안녕하세요', NOW());
insert into notice(company_id , job , salary , created_At) VALUES('2','프론트 엔드', '3천만원', NOW());
insert into need_skill(notice_id , skill , created_At) VALUES('2', '자바스크립트', NOW());
COMMIT;
```

## Tip
#### MariaDB auto commit 설정-해제 하기
```sql
show variables like 'autocommit%'; ### 현재 상태 확인
SET AUTOCOMMIT = TRUE;  ### 설정
SET AUTOCOMMIT = FALSE; ### 해제
```

