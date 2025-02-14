tags: #CS #DB #view

---
# view
- 하나 이상의 기본 테이블로부터 유도된, 이름을 가지는 가상 테이블 
	- 사용자에게 접근이 허용된 자료만을 제한적으로 보여주기 위해 사용
- 저장장치 내에 물리적으로 존재하지 않지만 사용자에게 있는 것처럼 간주된다.
- 데이터 보정작업, 처리과정 시험 등 임시적인 작업을 위한 용도로 활용된다.
- 조인문의 사용 최소화로 사용상의 편의성을 최대화 한다.

# 뷰의 특징
1. 기본 테이블로부터 유도된 테이블이기 때문에 기본 테이블과 같은 형태의 구조를 사용하며, 조작도 기본테이블과 거의 같음
2. 가상테이블이기 때문에 물리적으로 구현되어 있지 않음
3. 데이터의 논리적 독립성을 제공할 수 있음
4. 필요한 데이터만 뷰로 정의해서 처리할 수 있기 때문에 관리가 용이하고 명령문이 간단해짐
5. 뷰를 통해서만 데이터에 접근하게 하면 뷰에 나타나지 않는 데이터를 안전하게 보호하는 효율적인 기법으로 사용 가능
6. 기본 테이블의 기본키를 포함한 속성 집합으로 뷰를 구성해야지만 삽입, 삭제, 갱신, 연산이 가능
7. 일단 정의된 뷰는 다른 뷰의 정의에 기초가 될 수 있음
8. 뷰가 정의된 기본 테이블이나 뷰를 삭제하면 그 테이블이나 뷰를 기초로 정의된 다른 뷰도 자동으로 삭제

# 장단점
## 장점
1. 논리적 데이터 독립성을 제공
2. 동일 데이터에 대해 동시에 여러 사용자의 상이한 응용이나 요구를 지원
3. 사용자의 데이터관리를 간단하게 해 준다.
4. 접근 제어를 통한 자동 보안이 제공된다.

## 단점
1. 독립적인 인덱스를 가질 수 없다.
2. ALTER VIEW문을 사용할 수 없다. (뷰의 정의를 변경할 수 없다.)
3. 뷰로 구성된 내용에 대한 삽입, 삭제, 갱신, 연산에 제약이 따른다.

# 예제
- 정의문
```sql
--문법--
CREATE VIEW 뷰이름[(속성이름[,속성이름])]AS SELECT문;

--고객 테이블에서 주소가 서울시인 고객들의 성명과 전화번호를 서울고객이라는 뷰로 만들어라--
CREATE VIEW 서울고객(성명, 전화번호)
AS SELECT 성명 전화번호
FROM 고객
WHERE 주소 = '서울시';
```

- 삭제문
```sql
--문법--
DROP VIEW 뷰이름 RESTRICT or CASCADE

--서울고객이라는 뷰를 삭제해라--
DROP VIEW 서울고객 RESTRICT;
```