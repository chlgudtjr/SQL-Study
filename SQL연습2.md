# 2021.01.14(SQL연습2)


### 1. DB 관련하여 아래를 정리하시오.

```sql
--게시판 DB 설계(특히 댓글관련 컬럼)

--list 뽑아내는 sql

--댓글 달기 위한 sql

--수정 sql

--게시판 글 insert sql
```

- **정답 소스코드**

    ```sql
    --A1.게시판 DB 설계(특히 댓글관련 컬럼)
    ??
    --A2.list 뽑아내는 sql
    select bId,bName,bTitle,bContent,bDate,bHit,bGruop,bStep,bIndent from mvc_board
    order by bGroup desc, bStep asc;

    --A3.댓글 달기 위한 sql
    insert into mvc_board (bId,bName,bTitle,bContent,bGroup,bStep,bIndent) value
    (mvc_board_seq.nextval,?,?,?,?,?,?);

    --A4.수정 sql
    update mvc_board set bName = ?, bTitle = ?, bContent = ? where bId = ?;

    --A5.게시판 글 insert sql
    insert into mvc_board (bId,bName,bTitle,bContent,bGroup,bStep,bIndent) value
    mvc_board_seq.nextval(?,?,?,0, mvc_board_seq.currval,0,0);
    ```

---

### 2. 아래 쿼리를 푸시오.

```sql
-- 자신의 급여가 평균 급여보다 많고 이름에 T가 들어가는 사원과 동일한 부서에 근무하는 모든 사원의 사원 번호, 이름 및 급여를 출력하라.

-- Dallas에서 근무하는 사원과 직업이 일치하는 사원의 이름,부서이름, 및 급여를 출력하시오
```

- 정답 소스코드

    ```sql
    --A1.
    select empno, ename, sal from emp where (sal > (select avg(sal) from emp))
    and (deptno in (select deptno from emp where ename like '%T%'));
    --A2.
    select e.ename, d.dname, e.sal from emp e,dept d where loc in
    (select loc from dept where loc = 'DALLAS');
    ```
