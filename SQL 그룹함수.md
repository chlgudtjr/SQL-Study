# 2021.01.08 (SQL 그룹함수)

### 1. 아래가 에러가 나는 이유는?

```sql
SELECT DEPTNO,ENAME, SUM(SAL), AVG(SAL) FROM EMP GROUP BY DEPTNO;
```

→ group by는 어떤 컬럼 값을 기준으로 그룹함수를 적용해야할지 기술해야 한다.

하지만 위 예는 group by절에 명시하지 않은 컬럼을 select절에 사용하고 있으므로 오류가 발생한다.

group by절을 사용할 때 select절에 사용된 모든컬럼을 반드시 명시해야한다.

**수정**

```sql
SELECT DEPTNO,ENAME, SUM(SAL), AVG(SAL) FROM EMP GROUP BY DEPTNO,ENAME;
```

---

### 2. 그룹 함수의 종류는?

 **1. SUM**  : 해당 컬럼의 행들의 합계를 구한다.

EX) select SUM(sal) from emp;

 **2. AVG**  :  해당 컬럼의 행들의 평균을 구한다.

EX) select AVG(sal) from emp;

 **3. MIN / MAX**  : 해당컬럼의 최소값(MIN)과 최대값(MAX)을 구한다.

EX) select MIN(sal), MAX(sal) from emp;

 **4. COUNT** : 조건을 만족시키는 행의 갯수를 구한다.

EX) select COUNT(sal) from emp;

---

### 3. 오라클에서 형의 종류와 변환 함수에 대하여 설명하시오.

 **1. 숫자형  :  TO_NUMBER**

- 문자형을 숫자형으로 변환하는 함수이다.

EX)  select TO_NUMBER('20,000', '99,999');

 **2. 문자형 : TO_CHAR**

- 날짜형 혹은 숫자형을 문자형으로 변환하는 함수이다.

EX) select sysdate TO_CHAR(sysdate, 'yyyy-mm-dd') from dual;

 **3. 날짜형 :  TO_DATE**

- 문자형을 날짜형으로 변환하는 함수이다.

EX) select ename, hiredate from emp where hiredate = TO_DATE(19810220, 'yyyymmdd');

---

### 4. decode 함수에 대하여 설명하시오.

> DECODE

- 조건에 따라 데이터를 다른 값이나 컬럼 값을 추출 하고자 할 때 사용한다.
- decode함수 안에 decode함수를 중첩 사용할 수 있다.
- 자바의 switch문과 같은 기능을 가지고있다.

**EX)** select deptno, DECODE(deptno,10, 'A', 20, 'B', 'DEFAULT') from emp order by deptno;

---

### 5. CASE 함수에 대하여 설명하시오.

> CASE

- 여러가지 경우에서 하나를 선택하는 함수이다.
- 다양한 비교연산자를 이용하여 조건 제시 및 범위 지정할 수 있다.
- if else문과 같은 기능을 가지고있다.

**EX) select ename, deptno, case when deptno = 10 then 'ACCOUNTING'**

when  deptno = 20 then 'RESEARCH'

when deptno = 30 then 'SALES'

when deptno = 40 then 'OPERATIONS' 

end as ename from emp;

---

### 6. 아래를 프로그래밍 하시오.

1. 객체 생성 하도록 할 것.
2. input 박스 두 개 생성하여-가로 세로
3. 결과를 뿌리는 페이지
- HTML 소스파일

    ```html
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="EUC-KR">
    <title>Insert title here</title>

    </head>
    <body>
    	<form action = "firstTest.jsp" method = "post">
    		<h2>가로,세로 값구하기!</h2>
    		가로 : <input type = "text" name = "width">
    		가로 : <input type = "text" name = "height">
    		<input type = "submit" value  = "전송">
    	</form>
    </body>
    </html>
    ```

- JSP 소스파일

    ```html
    <%@ page language="java" contentType="text/html; charset=EUC-KR"
        pageEncoding="EUC-KR"%>
    <jsp:useBean id = "rec" class = "edu.bit.ex.Rec" scope = "page"></jsp:useBean>
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="EUC-KR">
    <title>Insert title here</title>
    </head>
    <body>
    	<% 
    		String wid = request.getParameter("width");
    		String hei = request.getParameter("height");
    		
    		int w = Integer.parseInt(wid);
    		int h = Integer.parseInt(hei);
    	%>
    	<table border = "1">
    	<tr>
    		<td>가로 : <%= w %></td>
    	</tr>
    	<tr>	
    		<td>세로 : <%= h %></td>
    	</tr>
    	<tr>
    		<td>총합 : <%= rec.getArea(w, h) %></td>
    	</tr>
    </body>
    </html>
    ```

- JAVA Bean 소스파일

    ```java
    package edu.bit.ex;

    public class Rec {
    	private int width;
    	private int height;
    	
    	public void Rec() {
    		
    	}

    	public int getWidth() {
    		return width;
    	}

    	public void setWidth(int width) {
    		this.width = width;
    	}

    	public int getHeight() {
    		return height;
    	}

    	public void setHeight(int height) {
    		this.height = height;
    	}
    	
    	public int getArea(int width, int height) {
    		return width * height;
    	}
    }
    ```

- 결과

![11](https://user-images.githubusercontent.com/75012998/104139758-f30e7700-53f0-11eb-9a93-9e47dacb5fd5.png)

![22](https://user-images.githubusercontent.com/75012998/104139759-f43fa400-53f0-11eb-8244-14017d97dc16.png)

---

### 7. MVC 모델에 대하여 설명하시오.

> MVC(Model, View, Controller)

- 개발할 때 3가지 형태로 나누어 개발하는 방법이다.

 **1. Model**

- 프로그램이 목표하는 작업을 원활하게 수행하기 위해 필요한 물리적 개체,규칙,작업 등의 요소 들을 구분되는 역할로 정의해놓은것

**Model 1패턴**

→ MVC에서 View와 Controller가 같이 있는 상태

![12](https://user-images.githubusercontent.com/75012998/104140288-1a1a7800-53f4-11eb-8555-0735be321b14.png)

장점 : 개발 속도가 빠르다.

단점 :  유지 보수하기 어렵다.

**Model 2 패턴**

→ MVC에서 Model, View, Controller가 모두 모듈화(부품화)되어있는 형태

![23](https://user-images.githubusercontent.com/75012998/104140289-1ab30e80-53f4-11eb-860d-1bd0b102399d.png)

장점 : 유지 보수하기 쉽다.

단점 : 개발 속도가 느리다.

**2. View**

- 사용자가 보는 화면에 입출력 과정 및 결과를 보여주기 위한 역할이다.

 **3. Controller**

- Model과 View를 연결시켜주는 다리 역할을 한다.

**MVC 패턴**

![34](https://user-images.githubusercontent.com/75012998/104140287-18e94b00-53f4-11eb-9c55-f33dd25201a5.png)
