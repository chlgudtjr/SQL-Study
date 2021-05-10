# 2021.01.07 SQL 연습 1

### 1. 아래를 SQL문으로 표기 하시오.

- 문제

    ```sql
    --Q1. 부서 번호(DEPTNO)가 20인 사원에 관한 정보만 출력

    --Q2. 이름(ENAME)이 FORD인 사람의 사번(empno), 이름(ename), 급여(SAL)를 출력하는 쿼리문

    --Q3. 1982년 1월 1일 이후에 입사한 사원을 출력하는 쿼리문

    --Q4. job 이 manage 이고 10번 부서인 사원

    --Q5. job 이 manage 이거나 10번 부서인 사원

    --Q6. 10번 부서가 아닌 사원

    --Q7. 급여가 2000~3000 사이의 사원을 검색하는 쿼리문

    --Q8. 급여가 2000 미만이거나 3000 초과인 사원을 검색하는 쿼리문

    --Q9. 1987년에 입사한 사원을 출력하는 쿼리문

    --Q10. 커미션(COMM)이 300 혹은 500 혹은 1400인 사원이 있는지 검색하는 쿼리문

    --Q11. 커미션(COMM)이 300 혹은 500 혹은 1400이 아닌 사원이 있는지 검색하는 쿼리문

    --Q12. 이 F로 시작하는 사람을 찾는 쿼리문

    --Q13. 위치 상관 없이 이름 중에 A가 들어있는 사람을 찾는 쿼리문

    --Q14. 이름이 N으로 끝나는 사람을 찾는 쿼리문

    --Q15. 이름의 두 번째 글자가 A인 사원을 찾는 쿼리문

    --Q16. 이름의 세 번째 글자가 A인 사원을 찾는 쿼리문

    --Q17. 이름에 A를 포함하지 않는 사람만 검색하는 쿼리문

    --Q18. 사원들의 급여를 오름차순으로 정렬하는 쿼리문

    --Q19. 가장 최근에 입사한 사원부터 출력하는 쿼리문

    --Q20. 사원들이 소속되어 있는 부서의 번호를 출력하는 쿼리문

    --Q21. 아래와 같이 출력하시오.
    SMITH is a CLERK
    ALLEN is a SALESMAN
    WARD is a SALESMAN
    JONES is a MANAGER
    MARTIN is a SALESMAN
    BLAKE is a MANAGER
    CLARK is a MANAGER
    KING is a PRESIDENT
    TURNER is a SALESMAN
    JAMES is a CLERK
    FORD is a ANALYST
    MILLER is a CLERK
    ```

- 정답 소스코드

    ```sql
    --A1.
    select * from emp where deptno = 20;
    --A2.
    select empno,ename,sal from emp where ename ='FORD';
    --A3.
    select * from emp where hiredate >= '1982/01/01';
    --A4.
    select * from emp where job = 'MANAGER' and deptno = 10;
    --A5.
    select * from emp where job = 'MANAGER' or deptno = 10;
    --A6.
    select * from emp where deptno <> 10;
    --A7.
    select * from emp where sal between 2000 and 3000;
    --A8.
    select * from emp where sal not between 2000 and 3000;
    --A9.
    select * from emp where hiredate between '1987/01/01' and '1987.12.31';
    --A10.
    select * from emp where comm in(300,500,1400);
    --A11.
    select * from emp where comm not in(300,500,1400);
    --A12.
    select * from emp where ename like 'F%';
    --A13.
    select * from emp where ename like '%A%';
    --A14.
    select * from emp where ename like '%N';
    --A15.
    select * from emp where ename like '_A%';
    --A16.
    select * from emp where ename not like '__A%';
    --A17.
    select * from emp where ename not like '%A%';
    --A18.
    select * from emp order by sal asc;
    --A19.
    select * from emp order by hiredate desc;
    --A20.
    select distinct deptno from emp;
    --A21.
    select ename || ' is a ' || job from emp;
    ```

---

### 2. 아래 문제를 푸시오.

![Untitled](https://user-images.githubusercontent.com/75012998/103884510-0afca700-5122-11eb-9a1d-dc114df69b3c.png)

- 1번 JSP 소스코드

    ```java
    <%@ page language="java" contentType="text/html; charset=EUC-KR"
        pageEncoding="EUC-KR"%>
    <jsp:useBean id ="UserBean" class = "edu.bit.ex.UserBean" scope = "page"></jsp:useBean>
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="EUC-KR">
    <title>Insert title here</title>
    	<style>
    		button{
    			width : 100px;
    			height : 30px;
    			margin-left : 280px;
    		}
    		
    		a{
    			text-decoration : none;
    		}
    		.result{
    			border : 1px solid black;
    			width : 700px;
    			height : 100px;
    			line-height : 100px;
    			background-color : beige;
    			font-size : 30px;
    			font-family : fantasy;
    			color : #FFC6C3;
    			text-align : center;
    		}
    		
    		 img{
    			width : 250px;
    			height : 250px;
    			
    		}
    	
    	</style>
    	
    </head>
    <body>
    	
    	<%
    		UserBean.setPlayer(Integer.parseInt(request.getParameter("player")));
    		UserBean.setCom((int)(Math.random()*3) + 1);
    		
    		if(UserBean.getCom() == 1){
    			%>
    			COM : <img src = "https://img.lovepik.com/element/40135/5246.png_300.png">
    			<%
    		}else if(UserBean.getCom() == 2){
    			%>
    			COM : <img src = "https://data.ac-illust.com/data/thumbnails/a6/a6864b8e323722d8f0b6ad20be822f52_t.jpeg">
    			<%
    		}else{
    			%>
    			COM : <img src = "https://file.edupre.co.kr/plan/clips/thumb/5/clips_20150820135918_6456.jpg.thumb.300">
    			<%
    		}
    		
    		if(UserBean.getPlayer() == 1){
    			%>
    			Player : <img src = "https://img.lovepik.com/element/40135/5246.png_300.png">
    			<%
    		}else if(UserBean.getPlayer() == 2){
    			%>
    			Player : <img src = "https://data.ac-illust.com/data/thumbnails/a6/a6864b8e323722d8f0b6ad20be822f52_t.jpeg">
    			<%
    		}else{
    			%>
    			Player : <img src = "https://file.edupre.co.kr/plan/clips/thumb/5/clips_20150820135918_6456.jpg.thumb.300">
    			<%
    		}
    		
    		
    		%>
    		<%
    		switch(UserBean.getPlayer()){
    		case 1:
    			if(UserBean.getPlayer() == 1){
    				if(UserBean.getCom() == 2){
    					%>
    					<div class = "result"><%="결과 : Player 승리~" %></div>
    					<%
    				}else if(UserBean.getCom() == 3){
    					%>
    					<div class = "result"><%="결과 : Player 패배...ㅠㅠ" %></div>
    					<%
    				}else{
    					%>
    					<div class = "result"><%="결과 : 무승부" %></div>
    				<%
    				}
    				break;
    			}
    		
    		case 2:
    			if(UserBean.getPlayer() == 2){
    				if(UserBean.getCom() == 3){
    					%>
    					<div class = "result"><%="결과 : Player 승리~" %></div>
    					<%
    				}else if(UserBean.getCom()== 1){
    					%>
    					<div class = "result"><%="결과 : Player 패배...ㅠㅠ" %></div>
    					<%
    				}else{
    					%>
    					<div class = "result"><%="결과 : 무승부" %></div>
    				<%
    				}
    				break;
    			}
    		case 3:
    			if(UserBean.getPlayer() == 3){
    				if(UserBean.getCom() == 1){
    					%>
    					<div class "result"><%="결과 : Player 승리~" %></div>
    					<%
    				}else if(UserBean.getCom() == 2){
    					%>
    					<div class "result"><%="결과 : Player 패배...ㅠㅠ" %></div>
    					<%
    				}else{
    					%>
    					<div class "result"><%="결과 : 무승부" %></div>
    				<%
    				}
    				break;
    			}
    		}
    	
    	%>
    	
    	<button><a href = "Game.html">다시하기</a></button>
    </body>
    </html>
    ```

- 1번 HTML & CSS 소스코드

    ```java
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="EUC-KR">
    <title>Insert title here</title>
    	<style>
    		#boad{
    			border : 1px solid beige;
    			width : 600px;
    			height : 350px;
    			background-color : #FFC6C3
    		}
    		
    		#boad div:nth-child(1){
    			border : 7px groove beige;
    			text-align : center;
    			margin : 0 auto;
    			margin-top : 15px;
    			width : 300px;
    			height : 50px;
    			line-height : 50px;
    			font-size : 25px;
    			font-family : fantasy;
    			font-weight : bold;
    			color : beige;
    		}
    		
    		#boad div img{
    			border : 6px dashed beige;
    			margin-top : 15px;
    			margin-left : 45px;
    			width : 500px;
    			height : 150px;
    		}
    		
    		#boad div:nth-child(3){
    			border : 6px double beige;
    			text-align : center;
    			margin : 0 auto;
    			width : 500px;
    			height : 40px;
    			line-height : 40px;
    		}
    		
    		
    	</style>
    </head>
    <body>
    	<form action = "NewGame.jsp" method = "post">
    	<div id = "boad">
    		<div>가위 바위 보 게임!</div>
    		<div><img src = "https://data.ac-illust.com/data/thumbnails/4f/4f63b32d7d43ea2cb231c0724200cf8e_t.jpeg"></div>
    		<div>
    			<select name = "player">
    				<option value = "2">가위</option>
    				<option value = "1">바위</option>
    				<option value = "3">보</option>
    			</select>
    		<input type ="submit" value = "경기시작">
    		</div>
    	</div>
    </body>
    </html>
    ```

- 1번 Java 소스코드

    ```java
    package edu.bit.ex;

    public class UserBean {
    	private int player;
    	private int com;
    	public int getPlayer() {
    		return player;
    	}
    	public void setPlayer(int player) {
    		this.player = player;
    	}
    	public int getCom() {
    		return com;
    	}
    	public void setCom(int com) {
    		this.com = com;
    	}
    }
    ```

- 

    ![Untitled 1](https://user-images.githubusercontent.com/75012998/103884500-089a4d00-5122-11eb-9012-9f5528cd1179.png)

    ![Untitled 2](https://user-images.githubusercontent.com/75012998/103884506-09cb7a00-5122-11eb-9aaf-b369204f1aa0.png)

---

- 2번 JSP 소스코드

    ```sql
    <%@ page language="java" contentType="text/html; charset=EUC-KR"
        pageEncoding="EUC-KR"%>
    <%@ page import = "java.sql.*" %>
    <jsp:useBean id = "Employee" class = "edu.bit.ex.Employee" scope = "page" ></jsp:useBean>
    <%!
    	Connection connection;
    	Statement statement;
    	ResultSet resultSet;
    	
    	 String driver = "oracle.jdbc.driver.OracleDriver";
    	 String url = "jdbc:oracle:thin:@localhost:1521:xe";
    	 String uid = "scott";
    	 String upw = "tiger";
    	 String query = "select * from emp";
    	
    %>

    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="EUC-KR">
    <title>Insert title here</title>
    </head>
    <body>

    	<%
    		try{
    			Class.forName(driver);
    			
    			connection = DriverManager.getConnection(url,uid,upw);
    			statement = connection.createStatement();
    			resultSet = statement.executeQuery(query);
    			

    			
    			%>
    			<table border = "1">
    				<tr>
    					<td>EMPNO</td>
    					<td>ENAME</td>
    					<td>JOB</td>
    					<td>MRG</td>
    					<td>HIREDATE</td>
    					<td>SAL</td>
    					<td>COMM</td>
    					<td>DEPTNO</td>
    				</tr>
    			<% 
    			while(resultSet.next()){
    				Employee.setEmpno(resultSet.getString("empno"));
    				Employee.setEname(resultSet.getString("ename"));
    				Employee.setJob(resultSet.getString("job"));
    				Employee.setMrg(resultSet.getString("mgr"));
    				Employee.setHiredate(resultSet.getString("hiredate"));
    				Employee.setSal(resultSet.getString("sal"));
    				Employee.setComm(resultSet.getString("comm"));
    				Employee.setDeptno(resultSet.getString("deptno"));
    				%>
    				
    				<tr>
    				<td><%=Employee.getEmpno() %></td>
    				<td><%=Employee.getEname() %></td>
    				<td><%=Employee.getJob() %></td>
    				<%
    				if(Employee.getMrg() != null){
    				%>	
    					<td><%=Employee.getMrg() %></td>
    				<%
    				}else{
    				%>
    					<td></td>
    				<%	
    				}
    				%>
    				<td><%=Employee.getHiredate() %></td>
    				<td><%=Employee.getSal() %></td>
    				<%
    				if(Employee.getComm() != null){
    				%>
    				<td><%=Employee.getComm() %></td>
    				<%
    				}else{
    				%>	
    				<td></td>
    				<%	
    				}
    				%>
    				<td><%=Employee.getDeptno() %></td>
    				</tr>
    				<%
    			}
    			
    		}catch(Exception e){
    			
    		}finally{
    			
    			try{
    				if(resultSet != null) resultSet.close();
    				if(statement != null) statement.close();
    				if(connection != null) connection.close();
    			}catch(Exception e){}
    			
    		}

    	%>
    	</table>
    </body>
    </html>
    ```

- 2번 Java 소스코드

    ```java
    package edu.bit.ex;

    public class Employee {
    	private String empno;
    	private String ename;
    	private String job;
    	private String mrg;
    	private String hiredate;
    	private String sal;
    	private String comm;
    	private String deptno;

    	public String getEmpno() {
    		return empno;
    	}

    	public void setEmpno(String empno) {
    		this.empno = empno;
    	}

    	public String getEname() {
    		return ename;
    	}

    	public void setEname(String ename) {
    		this.ename = ename;
    	}

    	public String getJob() {
    		return job;
    	}

    	public void setJob(String job) {
    		this.job = job;
    	}

    	public String getMrg() {
    		return mrg;
    	}

    	public void setMrg(String mrg) {
    		this.mrg = mrg;
    	}

    	public String getHiredate() {
    		return hiredate;
    	}

    	public void setHiredate(String hiredate) {
    		this.hiredate = hiredate;
    	}

    	public String getSal() {
    		return sal;
    	}

    	public void setSal(String sal) {
    		this.sal = sal;
    	}

    	public String getComm() {
    		return comm;
    	}

    	public void setComm(String comm) {
    		this.comm = comm;
    	}

    	public String getDeptno() {
    		return deptno;
    	}

    	public void setDeptno(String deptno) {
    		this.deptno = deptno;
    	}
    	
    	
    }
    ```

- 결과

    ![Untitled 3](https://user-images.githubusercontent.com/75012998/103884508-0a641080-5122-11eb-90de-9df2105fc688.png)
