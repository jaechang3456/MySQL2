# MySQL
### 1. SQL 문자열 함수들
- concat : 문자열을 합치는 함수, select concat(컬럼명, ' ' ,컬럼명)처럼 사용하면, 컬럼명 공백 컬럼명으로 합쳐진다.
- as : 컬럼명을 바꿔주는 함수이다. select concat(author_fname, ' ' ,author_lname) as 'full name'처럼 사용시, 원래 컬럼명이concat(author_fname, ' ' ,author_lname) 이지만 full name으로 바뀐다.
- substring : 문자열의 일부를 슬라이싱하는 함수이다. select substring(문자열, 시작숫자, 끝숫자); 처럼 사용하며, 문자열의 시작숫자 번호부터 끝숫자 번호까지 가져온다. 이때, 숫자 번호는 python등과 다르게 0부터 시작이 아닌, 1부터 시작한다.
- replace : 문자열의 일부를 바꿔주는 함수이다. select replace(전체문자열, 바꿀문자열, 대체할문자열); 처럼 사용하며, 전체 문자열에서 바꿀문자열이 대체할 문자열로 바뀐다.
- reverse : 문자열의 순서를 거꾸로 하는 함수이다. select reverse(문자열); 처럼 사용하며, 앞에서부터가 아닌 뒤에서부터 출력된다.
- char_length : 문자열의 길이를 나타내주는 함수이다. select char_length(문자열); 처럼 사용하며 문자열의 글자수가 몇개인지 숫자로 출력된다.
- upper : 문자열을 대문자로 나타내주는 함수이다. upper(문자열); 처럼 사용하며, 모든 글자가 대문자가 된다.
- lower : 위의 함수와 반대로 문자열을 소문자로 나타내주는 함수이다. 사용법 및 동작방법은 같다.
- distinct : 유니크한 데이터를 가져와주는 키워드이다. select distinct 컬럼명; 처럼 사용하며, 중복된 값들은 하나의 값으로 출력된다.

### 2. 오름차순, 내림차순 정렬과 여러 컬럼 정렬방법
- MySQL에서 정렬을 하기위해선 order by를 사용한다. 기본적으로 아래와 같이 사용하며,
- select * from 테이블 order by 컬럼명; 원하는 값을 얻기 위해서는 order by를 마지막에 사용해줘야 한다. *순서중요
- 오름차순으로 정렬 하기 위해선, select * from 테이블 order by 컬럼명; 처럼 뒤에 아무거도 붙이지 않거나, select * from 테이블 order by 컬럼명 asc;처럼 사용하고,
- 내림차순으로 정렬하기 위해서는 select * from 테이블 order by 컬럼명 desc;를 붙여줘야한다.
- 또한 , select * from books order by 컬럼1 desc, 컬럼2 asc; 처럼 컬럼1을 내림차순으로 정렬한뒤, 같은 값들은 컬럼2로 오름차순으로 정렬 가능하다. asc는 생략 가능하다.

### 3. Limit와 Offset사용법 (정렬과 함께 사용하는 예도 포함)
- Limit와 Offset은 내가 원하는 위치의 데이터를 원하는 만큼 가져와준다.
- select * from 테이블명 limit 숫자1, 숫자2;
- 위와 같이 사용 가능하며, 숫자1은 입력한 숫자 다음부터의 데이터를 가져오며, 숫자2는 입력한 숫자 만큼의 데이터를 가져온다.
- 예를들어 select * from 테이블명 limit 10, 10; 처럼 사용하면, 테이블에 있는 전체 데이터를 11번째부터, 10개를 가져온다는 뜻이 된다.
- 정렬과 같이 사용할수 있으며, 정렬과 같이 사용하게 되면 등수를 나타내는데 용이하다.
- select * from 테이블명 order by 컬럼명 desc limit 5; 처럼 사용하면 컬럼의 데이터를 내림차순으로 정렬하여, 1번째 데이터부터 5번째 데이터 까지 나타내어, 1~5등을 나타내는 뜻이 된다.

### 4. 포함하는 단어 검색하는 Like 키워드 사용법
- like는 단어를 포함하고 있는지 확인 하는 키워드이다. 아래와 같이 사용 가능하며
- select 컬럼명 from 테이블명 where 컬럼명 like 문자열;
- 포함한다는 조건을 나타내므로 MySQL에서 조건문처럼 쓰이는 Where와 같이 쓰인다.
- 하지만, 위에 처럼 작성하면 문자열이 포함된 것이 아닌 문자열 자체로 판단하기 때문에 다른 글자가 있어도 된다는 %를 사용해 준다. 아래와 같이 사용할 수 있다.
- select 컬럼명 from 테이블명 where 컬럼명 like %문자열%;
- 또한 %와 같은 문자열이 아닌 기능이 있는 문자가 문자열로 적혀있을경우엔 앞에 \붙여 구분하여 준다. 예를 들면
- select 컬럼명 from 테이블명 where 컬럼명 like %\%%; 처럼 사용하면 %를 찾고 싶고, 앞뒤에 다른 글자가 있어도 된다는 %를 의미한다. 또한, 몇자리의 글자를 포함하는지 확인하는 언더 스코어도 사용할수 있다.('__') 

### 5. 숫자 연산 함수
- count : 컬럼값의 갯수를 찾아주는 함수이다. select count(*) from 테이블;
- min : 컬럼값의 최소값을 찾아주는 함수이다. select min(컬럼명) from 테이블;
- max : 컬럼값의 최대값을 찾아주는 함수이다. select max(컬럼명) from 테이블;
- sum : 컬럼값들의 합을 구해주는 함수이다. select sum(컬럼명) from 테이블;
- avg : 컬럼값들의 평균을 구해주는 함수이다. select avg(컬럼명) from 테이블;
- 위에 연산과 관련하여 최대값인 컬럼 하나의 데이터를 찾고 싶다면 select * from 테이블 where 컬럼명 =  (select max(컬럼명) from 테이블 ); 처럼 사용 가능하며, 이를 subquery라고 한다.

### 6. MySQL 시관 관련 처리 방법
- curdate : 현재의 날짜를 가져와 준다.
- curtime : 현재의 시간을 가져와 준다.
- now : 현재의 날짜와 시간을 가져와 준다.
- MySQL에서 날짜를 얻어올땐, day(날짜), 요일을 얻어올땐 dayname(날짜), 요일명을 숫자로 얻어올땐 dayofweek(날짜)등 여러가지가 있다. 시간 관련 처리 함수 및 레퍼런스는 아래 링크를 참고하자.
- https://www.tutorialspoint.com/mysql/mysql-date-time-functions.htm





