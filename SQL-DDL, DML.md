# 2021.01.13 (SQL-DDL,DML))

### 1. 아래를 sql 문으로 나타내시오.

```sql
--1> 부서테이블의 모든 데이터를 출력하라.

--2> EMP테이블에서 각 사원의 직업, 사원번호, 이름, 입사일을 출력하라.

--3> EMP테이블에서 직업을 출력하되, 각 항목(ROW)가 중복되지 않게 출력하라.

--4> 급여가 2850 이상인 사원의 이름 및 급여를 표시하는 출력하라.

--5> 사원번호가 7566인 사원의 이름 및 부서번호를 표시하는 출력하라.

--6> 급여가 1500이상 ~ 2850이하의 범위에 속하지 않는 모든 사원의 이름 및 급여를 출력하라.

--7> 1981년 2월 20일 ~ 1981년 5월 1일에 입사한 사원의 이름,직업 및 입사일을 출력하라.
  -- 입사일을 기준으로 해서 오름차순으로 정렬하라.

--8> 10번 및 30번 부서에 속하는 모든 사원의 이름과 부서 번호를 출력하되,
  -- 이름을 알파벳순으로 정렬하여 출력하라.

--9> 10번 및 30번 부서에 속하는 모든 사원 중 급여가 1500을 넘는 사원의
  -- 이름 및 급여를 출력하라.(단 컬럼명을 각각 employee 및 Monthly Salary로 지정하시오)

--10> 관리자가 없는 모든 사원의 이름 및 직위를 출력하라.

--11> 커미션을 받는 모든 사원의 이름, 급여 및 커미션을 출력하되, 급여를 기준으로
   -- 내림차순으로 정렬하여 출력하라.

--12> 이름의 세 번째 문자가 A인 모든 사원의 이름을 출력하라.

--13> 이름에 L이 두 번 들어가며 부서 30에 속해있는 사원의 이름을 출력하라.

--14> 직업이 Clerk 또는 Analyst 이면서 급여가 1000,3000,5000 이 아닌
   -- 모든 사원의 이름, 직업 및 급여를 출력하라.

--15> 사원번호, 이름, 급여 그리고 15%인상된 급여를 정수로 표시하되 컬럼명을
   -- New Salary로 지정하여 출력하라.

--16> 15번 문제와 동일한 데이타에서 급여 인상분(새 급여에서 이전 급여를 뺀 값)을 추가해서
   -- 출력하라.(컬럼명은 Increase로 하라).

--17> 모든 사원의 이름(첫 글자는 대문자로, 나머지 글자는 소문자로 표시) 및 이름 길이를
   -- 표시하는 쿼리를 작성하고 컬럼 별칭은 적당히 넣어서 출력하라.

--18> 사원의 이름과 커미션을 출력하되, 커미션이 책정되지 않은
   -- 사원의 커미션은 'no commission'으로 출력하라.
 
--19> 모든 사원의 이름,부서번호,부서이름을 표시하는 질의를 작성하라.(DECODE)
```

- 정답 SQL문

    ```sql
    --A1.
    select * from dept;

    --A2.
    select ename,job,deptno,hiredate from emp;

    --A3.
    select distinct job from emp;

    --A4.
    select ename,sal from emp  where sal > = 2850;

    --A5.
    select ename,empno from emp where empno = 7566;

    --A6.
    select ename,sal from emp where sal between 1500 and 2850;

    --A7.
    select ename,job,hiredate from emp where hiredate between '1981/02/20' and '1981/05/01';

    --A8.
    select ename,deptno from emp where deptno = 10 or deptno = 30 order by ename asc ;

    --A9.
    select ename "employee" , sal "Monthly Salary" from emp 
    where sal > 1500 and (deptno = 10 or deptno = 30);

    --A10.
    select ename,job from emp where job != 'MANAGER';

    --A11.
    select ename,sal,comm from emp group by ename,sal,comm order by sal desc;

    --A12.
     select ename from emp where ename like '__A%';

    --A13.
    select deptno,ename from emp where ename like '%L%L%' and deptno = 30;

    --A14.
    select ename,job,sal from emp where job = 'ANALYST' or job = 'CLERK' and 
    (sal <> 1000 and sal <> 3000 and sal <> 5000);

    --A15.
    select deptno, job, trunc(sal * 1.15 )"New Salary" from emp;

    --A16.
    select deptno, job, trunc(sal * 1.15 )"New Salary" ,sal * 0.15 "Increase" from emp;

    --A17.
    select initcap(ename)"Name", length(ename)"Length" from emp;

    --A18.
    select ename, nvl(to-char(comm), 'no commision') from emp;

    --A19.
    ????
    ```
