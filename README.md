# 자재 관리 시스템

이 프로젝트는 Node.js, Express, MySQL을 사용하여 구축된 간단한 자재 관리 웹 애플리케이션입니다. 사용자는 이 시스템을 통해 자재 정보를 등록, 조회, 수정, 삭제할 수 있습니다.

## 주요 기능

- **자재 목록 조회**: 등록된 모든 자재의 목록을 확인합니다.
- **자재 상세 정보**: 각 자재의 상세 정보를 조회합니다.
- **자재 등록**: 새로운 자재 정보를 시스템에 추가합니다.
- **자재 정보 수정**: 기존 자재 정보를 수정합니다.
- **자재 정보 삭제**: 불필요한 자재 정보를 삭제합니다.

## 실행 방법

### 1. 데이터베이스 설정

- MySQL 데이터베이스에 `testdb` 데이터베이스를 생성합니다.
- `testdb` 데이터베이스에 아래 SQL을 실행하여 `material` 테이블을 생성합니다.

```sql
CREATE TABLE material (
    material_id INT AUTO_INCREMENT PRIMARY KEY,
    material_code VARCHAR(255),
    material_name VARCHAR(255),
    category VARCHAR(255),
    specification TEXT,
    unit VARCHAR(50),
    unit_price INT,
    stock_qty INT,
    safety_stock INT,
    supplier_name VARCHAR(255),
    warehouse_location VARCHAR(255),
    inbound_date DATE,
    material_status VARCHAR(50),
    manager_name VARCHAR(255),
    manager_phone VARCHAR(255),
    note TEXT,
    created_at DATETIME
);
```
- `server.js` 파일의 `mysql.createConnection` 부분에 자신의 데이터베이스 접속 정보를 입력합니다.

### 2. 종속성 설치

프로젝트 루트 디렉터리에서 다음 명령어를 실행하여 필요한 Node.js 모듈을 설치합니다.

```bash
npm install express mysql2
```

### 3. 서버 실행

다음 명령어를 사용하여 웹 서버를 시작합니다.

```bash
node server.js
```

서버가 시작되면 웹 브라우저에서 `http://localhost:3000`으로 접속할 수 있습니다.

## 프로젝트 구조

- **server.js**: Express를 사용하여 웹 서버를 설정하고, API 라우팅 및 데이터베이스와의 통신을 처리하는 핵심 파일입니다.
- **templates/**: HTML 템플릿 파일들이 위치하는 디렉터리입니다.
  - `material-list.html`: 자재 목록 페이지의 템플릿입니다.
  - `material-write.html`: 자재 등록 페이지의 템플릿입니다.
  - `material-detail.html`: 자재 상세 정보 페이지의 템플릿입니다.
  - `material-edit.html`: 자재 수정 페이지의 템플릿입니다.
  - `material-message.html`: 성공 또는 오류 메시지를 표시하는 페이지의 템플릿입니다.
- **static/**: CSS 파일, 이미지 등 정적 파일들이 위치하는 디렉터리입니다.
  - `style.css`: 웹사이트의 전반적인 스타일을 정의하는 CSS 파일입니다.
