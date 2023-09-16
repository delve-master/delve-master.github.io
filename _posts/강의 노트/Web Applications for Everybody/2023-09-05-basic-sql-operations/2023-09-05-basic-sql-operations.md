---
title: "[Introduction to Structured Query Language] - 기본적인 SQL 쿼리 실행해보기"
date: 2023-09-05 19:33:00 +0900
categories: ["강의 노트", "Web Applications for Everybody"]
tags: ["web", "coursera"]
image: Basic SQL Operations.png
---

{: .prompt-info }
> 이 포스팅은 Charles Severance 교수(이하 척 아저씨)의 Coursera 강의 ["Introduction to Structured Query Language"](https://www.coursera.org/learn/intro-sql) Week 2 에서 다룬 내용을 정리합니다.

이번 포스팅에서는 MySQL를 이용해 기본적인 DB 작업을 해볼것이다. 내가 따라가는 코세라 강의에서는 MAMP를 이용해 이 작업을 진행하는데, **설치를 강력히 추천한다.** MySQL, php, 아파치 웹서버가 전부 패키지로 딸려오기 때문에 세팅을 원큐에 할 수 있다!

기본적으로 Mac 유저면 MAMP, 윈도우 유저면 WAMP, 리눅스 유저면 LAMP 사용이 권장되는데 나는 윈도우 유저지만 MAMP도 나쁘지 않아서 크게 상관은 없는 것 같다. 


## 쿼리 실행 준비하기
MySQL에 쿼리를 생성하는 방법은 두 가지가 있는데 하나는 phpMyAdmin이라는 프로그램을 쓰는 것이고 다른 하나는 CUI 상으로 하는 것이다. 아무래도 phpMyAdmin이 GUI 기반이기 때문에 조금 더 가시성이 좋긴하다.


### phpMyAdmin

MAMP를 실행하여 Apache Server와 MySQL Server를 활성화한다. 

![Alt text](<Screenshot 2023-09-05 171613.jpg>)
_MAMP 창에서 전원 버튼 같이 생긴걸 누르면 알아서 서버를 실행할 것이다._

그러면 브라우저에 다음과 같은 페이지가 뜰텐데 여기서 상단의 TOOLS를 누르면 PHPMYINFO와 PHPMYADMIN 옵션이 보일 것이다. 여기서 PHPMYADMIN을 클릭하자. 

![Alt text](<Screenshot 2023-09-05 171908.jpg>)
_MAMP 페이지. 주소는 localhost로 맞춰져 있을 것이다._

![Alt text](<Screenshot 2023-09-05 172046.jpg>)


PHPMYADMIN으로 들어가면 옵션이 여러가지 보이는데, 여기서 상단의 SQL을 누르면 SQL 쿼리를 넣을 수 있는 페이지가 뜬다.

![Alt text](<Screenshot 2023-09-05 173340.jpg>)


![Alt text](<Screenshot 2023-09-05 173416.jpg>)
_현재 'localhost' 서버에 SQL 쿼리를 실행한다는 안내문이 보인다._

phpMyAdmin 상에서 SQL 쿼리를 실행할 준비는 모두 마쳤다. 

### CUI 

CUI에서 SQL 쿼리를 실행하려면 먼저 MySQL을 cmd에서 실행해야 한다.[^1] 내 기준으로 `mysql` 프로그램은 `C:\MAMP\bin\mysql\bin`에 있었지만 이건 MAMP 설치를 어디에 했느냐에 따라 다를 수 있다. 

따로 MySQL을 PATH에 등록하지 않았다면 cmd의 working directory를 `mysql` 프로그램이 설치된 디렉토리에 맞춰놓고 `mysql -u root -p` 명령어를 실행하자. 그러면 비밀번호를 입력하라는 얘기가 나올텐데, <u>기본 비밀번호는 'root' 이다.</u>

> mysql만 실행하면 **ERROR 1045 (28000): Access denied for user 'ODBC'@'localhost' (using password: NO)** 에러가 뜰 것이다. 이는 비밀번호를 입력하지 않아서 그런것이므로 cmd에 `mysql -u root -p`를 치고 비밀번호 root를 입력하자. MAMP 기준으로 기본 username과 password 모두 root다. 
{: .prompt-warning }

성공했다면 CUI 상에서 sql 환영 메세지가 출력되며 쿼리를 생성할 수 있게된다. 

![Alt text](<Screenshot 2023-09-05 175023.jpg>)


## SQL 쿼리

이제 SQL 쿼리를 실행해보자. 대다수의 SQL 쿼리는 직관적인 이름을 가지고 있기 때문에 거의 헤맬일이 없다.

### CREATE 

`CREATE` 는 말 그대로 DB나 테이블 같은 객체를 새로 생성한다.

```sql
CREATE DATABASE PEOPLE;
USE PEOPLE;
```
위의 코드는 *PEOPLE* DB를 생성하고 다음에 실행할 쿼리를 *PEOPLE* DB에 적용하게끔 한다. 

![Alt text](<Screenshot 2023-09-05 175834.jpg>)
_<i>PEOPLE</i>  DB가 새로 생성된 것이 보인다._

![Alt text](<Screenshot 2023-09-05 180306.jpg>)
_CUI 상에서도 확인할 수 있다._

> phpMyAdmin 같은 GUI가 없는 CUI에서는 `show databases;` 쿼리로 DB 목록을 볼 수 있다.
{: .prompt-tip }

이렇게 생성한 *PEOPLE* DB를 관계형 데이터베이스(RDBMS)로 만들기 위해서는 테이블을 추가해야한다. 

`CREATE`를 이용해 *PEOPLE* DB에 테이블 *Users*을 추가해보자.

```sql
CREATE TABLE Users(
    name VARCHAR(128),
    email VARCHAR(128)
);
```

*Users*를 만들때 2개의 열(column) *name*과 *email*을 추가했다.
`VARCHAR(128)`은 *name*과 *email*이 최대 128자의 utf-8 문자를 받아들일 수 있게끔 지정한다.

![Alt text](<Screenshot 2023-09-06 001103.jpg>)
_테이블이 잘 생성된 것을 확인할 수 있다._


### DESCRIBE 

```sql
DESCRIBE Users;
```

말 그대로 선택한 객체의 관한 기본적인 정보를 요청하는 쿼리이다. 

위의 쿼리는 *Users* 테이블에 관한 정보를 출력한다. 

![Alt text](<Screenshot 2023-09-06 001332.jpg>)
_위에서 phpMyAdmin으로 봤던 내용들을 그대로 볼 수 있다._

> *Users*는 *PEOPLE* DB내에 존재하는 테이블이기 때문에 사전에 `USE PEOPLE;`로 현재 작업중인 DB를 지정해야한다.
{: .prompt-warning }


### INSERT

`INSERT` 쿼리는 DB에 데이터를 추가한다. 이는 DB 테이블에 행(row)을 추가하는 방식으로 이루어진다.

```sql
INSERT INTO Users (name, email) VALUES ('Chuck', 'csev@umich.edu')
```

![Alt text](<Screenshot 2023-09-06 002505.jpg>)


### DELETE
`DELETE` 쿼리는 특정 객체를 제거하는데 사용된다. 제거할 객체를 지정하는데 `WHERE` 쿼리를 같이 사용하는데 다음과 같다.

```sql
DELETE FROM Users WHERE email='csev@umich.edu'
```
위 쿼리는 *Users* 테이블에서 조건에 맞는 데이터를 삭제할 것이다. `WHERE` 이 일종의 조건문(conditional statement)으로 작용한다. 

![Alt text](<Screenshot 2023-09-06 003754.jpg>)

![Alt text](<Screenshot 2023-09-06 003905.jpg>)
_성공적으로 데이터가 제거된 것을 볼 수 있다._


### UPDATE
`UPDATE` 쿼리는 이미 존재하는 객체를 수정하는데 사용된다. `DELETE`과 같이 수정할 객체를 지정하는데 `WHERE` 쿼리를 같이 사용한다.

```sql
UPDATE Users SET name='Charles' WHERE email='csev@umich.edu'
```

`DELETE`과 구문이 거의 비슷하다. `SET` 쿼리로 *email* 값이 'csev@umich.edu'인 데이터의 *name* 값을 'Charles'로 set 한 것.

![Alt text](<Screenshot 2023-09-06 005424.jpg>)


### SELECT
`SELECT` 쿼리는 쉽게 말해 마우스 드래그다. 전체 데이터를 지정하거나 `WHERE` 쿼리와 조합해 조건에 맞는 데이터만 지정할 수 있다.

```sql
SELECT * FROM Users WHERE email='csev@umich.edu'
```

별 **\*** 문자는 "0개 이상의 아무 문자"를 의미하는 와일드카드 문자 중 하나다. 즉, 위의 쿼리는 조건에 맞는 이메일을 가진 모든 데이터를 지정한다. 

![Alt text](<Screenshot 2023-09-06 010011.jpg>)

특정 데이터를 `SELECT`로 지정했다면 여러가지 작업을 할 수 있다. 


#### ORDER BY
`ORDER BY` 는 데이터를 정렬할 때 사용한다. 우선 `SELECT`로 정렬할 데이터를 지정하고 어떤 값을 기준으로 정렬할지 정한다. 또한 `ASC` 또는 `DESC`을 붙여 오름차나 내림차 순으로 정렬할 수도 있다.

```sql
SELECT * FROM Users ORDER BY email DESC
```
위 쿼리는 
1. 데이터 전체를 
2. 이메일을 기준으로 
3. 내림차 순으로 

정렬한다.

![Alt text](<Screenshot 2023-09-06 011056.jpg>)
_내림차 순으로 잘 정렬된 테이블을 확인할 수 있다._


#### LIKE
`LIKE` 는 와일드카드 문자를 사용하여 특정 조건에 맞는 값을 가진 데이터를 찾는데 사용한다. 

와일드카드 문자라는건 특별한 의미를 가지고 있는 문자인데, 대표적으로 위에서 사용했던 별 * 문자가 있다. 

```sql
SELECT * FROM Users WHERE name LIKE '%E%'
```

'%C%'는 아무데나 'c가 포함된' 단어를 뜻한다. *name* 에 e가 포함되어 있기만 하면 선택된다. 

![Alt text](<Screenshot 2023-09-06 012603.jpg>)


#### LIMIT
`LIMIT` 은 "어디서부터 어디까지" 데이터를 지정하는지 제한하는데 사용한다.

```sql
SELECT * FROM Users ORDER BY email LIMIT 1,2;
```

위의 쿼리는 *Users* 의 2번째와 3번째 행을 *email* 값으로 정렬한다.

> SQL또한 프로그래밍 세계의 전통대로 배열의 인덱싱은 0부터 시작한다. 
{: .prompt-tip }

![Alt text](<Screenshot 2023-09-06 013436.jpg>)

#### COUNT
굳이 데이터를 불러오지 않고 갯수만 세고 싶다면 `SELECT`에 `COUNT`를 붙여서 쿼리를 실행할 수 있다.

```sql
SELECT COUNT(*) FROM Users;
SELECT COUNT(*) FROM Users WHERE email='cute@umich.edu'
```

![Alt text](<Screenshot 2023-09-06 014019.jpg>)
_데이터의 구체적 정보없이 갯수만 나오는 것을 확인할 수 있다._

추가로 *email* 이 'cute@umich.edu' 인 데이터가 없다는 것을 눈치챘는가? SQL DB에 존재하지 않는 데이터를 요청해도 <u>에러가 뜨지 않는다</u>. 단지 결과값이 없을 뿐이다. 

## 마치며...

척 아저씨에 의하면 이번 포스팅에서 다뤘던 SQL 쿼리면 **SQL의 절반은** 배운거나 다름없다고 한다. 

왜 SQL이 첫번째 프로그래밍 언어로 배우기 좋지 않은지 이해가 될 것 같다. 이렇게 쉽고 직관적인 언어에 익숙해져 있다가 C를 배운다고 생각하면 욕쟁이 할머니마냥 구시렁댈게 뻔하다. 

여튼 다음 포스팅에서는 테이블과 다른 테이블 간의 교류작업을 다루겠다. 

(*end of post*)

---

[^1]: 윈도우 기준이므로 다른 운영체제 사용자면 맞는 커맨드라인을 이용하자.