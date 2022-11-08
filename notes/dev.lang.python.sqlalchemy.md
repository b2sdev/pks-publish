---
id: dysy9z4ix70igtpptywbaj9
title: SQLAlchemy
desc: ''
updated: 1666970571227
created: 1536878940227
---

## SQLAlchemy ORM (Object Relational Mapper)

### What
- 파이썬에서 데이터베이스를 쉽고 효율적으로 다룰 수 있는 환경을 제공하는 도구

### How
- 파이썬과 데이터베이스를 연결해 상위 레벨에서 SQL을 사용할 수 있게 해줌
    - 파이썬의 클래스와 클래스의 객체를 관계형 데이터베이스의 테이블과 그 테이블의 레코드로 연관지음

### Note
- 만약 저수준의 SQL로 데이터베이와 직접 상호 작용해야하면 SQLAlchemy Core의 SQL Expression Language를 사용할 수 있음

## SQLAlchemy 사용법

### SQLAlchemy 설치
```shell
pip install SQLAlchemy
```

### 데이터베이스에 접속
```python
from sqlalchemy.orm import scoped_session, sessionmaker, relationship, backref

# 데이터베이스에 접속하기 위해 데이터베이스 엔진을 추상화한 Engine 객체를 얻는다
engine = sa.create_engine('mysql+pymysql://root:password@34.239.103.110/testdb') #'sqlite:///site.db'

# 연결된 데이터베이스를 다루기 위한 세션 객체를 얻는다.
# 이 세션을 이용해 데이터베이스 쿼리, 커넥션, 트랜잭션 등 데이터베이스와 관련된 모든 작업을 처리한다. bind 인자에 연결할 데이터베이스 엔진을 설정한다.
session = scoped_session(sessionmaker(bind=engine))
```

### Base 클래스 만들기
```python
from sqlalchemy.ext.declarative import declarative_base

Base = declarative_base()
```

### Model 만들기
```python
import sqlalchemy as sa

# users 테이블을 아래와 같이 모델링한다
class User(Base):
    # User 클래스와 매핑될 물리적인 데이터베이스 테이블명
    __tablename__ = 'user'
    id = sa.Column(sa.Integer, primary_key=True)
    username = sa.Column(sa.String(45), unique=True, nullable=False)
    email = sa.Column(sa.String(80), unique=True, nullable=False)
    password = sa.Column(sa.String(45), nullable=False)
    
    # 객체에 어떤 값이 들어있는지 출력 (디버깅, 로깅 용)
    def __repr__(self):
            return f"User('{self.user_name}', '{self.email}')"
```

### 데이터베이스 테이블 생성
```python
# 앞서 초기화한대로 데이터베이스 테이블을 생성한다.
Base.metadata.create_all(engine)
```

SQLAlechemy에서 자동으로 아래와 같은 데이터베이스 테이블 스키마를 새성하는 SQL 문을 실행한 것처럼 테이블을 만들어준다.

```sql
CREATE TABLE users(
id INTEGER NOT NULL,
username VARCHAR(50),
email VARCHAR(80),
password VARCHAR(55),
PRIMARY KEY (id),
UNIQUE (username)
);
```

## References
- 주성식, 홍성민, 파이썬 웹 프로그래밍, 위키북스
- https://docs.sqlalchemy.org/en/latest/orm/examples.html

## Note
아래 자료도 추가 확인할 것
- https://www.sqlalchemy.org/
- http://flask-sqlalchemy.pocoo.org/2.3/
