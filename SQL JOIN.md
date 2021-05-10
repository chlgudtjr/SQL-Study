# 2021.01.09(SQL-JOIN)


### 1. join의 종류에 대하여 설명하시오.

> JOIN

- 여러 테이블에 흩어져 있는 정보 중에서 사용자가 필요한 정보만 가져와서 가상의 테이블처럼 만들어서 결과를 보여준다.

**종류**

 **1.  EQUI JOIN** 

- 두 개의 테이블 간의 칼럼 값들이 정확하게 일치하는 경우에 사용

 **2. NON-EQUI JOIN** 

- 두 개의 테이블 간의 칼럼 값들이 정확하게 일치하지 않은 경우에 사용

 **3. SELF JOIN**

- 같은 테이블에 행들을 join하는데 사용

 **4. OUTER JOIN** 

- 두 개의 테이블 간의 join을 하였을 때 join의 조건에 만족하지 않은 경우에도 그 데이터들을 보고자 하는 경우에 (+)연산자를 사용

---

### 2. 아래를 sql 문으로 처리 하시오.

```sql
-- EMP테이블을 EMPLOYEE와 MANAGER로 별칭을 지정한 후 특정 사원의 매니저가 누구인지 알아내는 쿼리문

-- 사원 정보를 출력할 때, 각 사원이 소속된 부서의 상세 정보를 출력하기 위해 두 개의 테이블을 조인하는 쿼리문

-- 부서의 최대값과 최소값을 구하되, 최대 급여가 2900 이상인 부서만 출력하는 쿼리문

-- 부서별 사원의 수와 커미션을 받는 사원의 수를 계산하는 쿼리문

-- 소속 부서별 급여 총액과 평균 급여를 구하는 쿼리
```

- **정답 소스코드**

    ```sql
    --Q1.
    select employee.ename || '의 매니저는' || manager.ename || '입니다/'
    from emp employee, emp manager
    where employee.mgr = manager.empno;

    --Q2.
    select * from emp,dept;

    --Q3.
    select deptno, min(sal), max(sal) from emp group by deptno having max(sal) >= 2900;

    --Q4.
    select deptno, count(deptno),count(comm) from emp group by deptno;

    --Q5.
    select job, sum(sal),avg(sal) from emp group by job;
    ```

---
