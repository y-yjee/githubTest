# KD손해보험 관리자 백엔드 프로젝트
Java + Spring Legacy + Oracle 기반의 보험사 관리자 페이지

---

## #0. 프로젝트 개요
**프로젝트 이름**: 보험사 보험 업무 자동화 (KD손해보험 관리자 시스템)

**프로젝트 목적 및 개요**:  
KD손해보험의 보험 업무 진행을 위한 **관리자 페이지를 구현하는 사이트** 구축. 관리자가 효율적으로 고객, 상품, 계약 등의 데이터를 관리하고, 전반적인 보험 업무 프로세스를 자동화 및 간소화하는 데 기여함을 목표로 함. 
스프링 레거시(Spring Legacy) 기반으로 안정적인 시스템을 구축하고, 사용자 친화적인 인터페이스를 제공하여 관리자 업무 생산성을 향상시킴.

**프로젝트 기간**: 전체 기간: 2025.07.08 ~ 2025.08.11

---

## 기술 스택

### 프론트엔드 (View / JSP 기반)
- **뷰엔진**: JSP (JavaServer Pages), HTML5  
- **템플릿 태그**: JSTL, EL  
- **스타일링**: Bootstrap, CSS3  
- **JavaScript**: 순수 JS 또는 jQuery  
- **AJAX**: jQuery AJAX 또는 Fetch API  

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=white)
![Bootstrap](https://img.shields.io/badge/Bootstrap-563D7C?style=for-the-badge&logo=bootstrap&logoColor=white)
![jQuery](https://img.shields.io/badge/jQuery-0769AD?style=for-the-badge&logo=jquery&logoColor=white)

---

### 백엔드 (Spring 기반)
- **백엔드 프레임워크**: Spring Framework (Spring Legacy)
- **언어**: Java
- **ORM**: MyBatis
- **보안**: Spring Security  
- **API**: REST API
- **데이터베이스 연동**: Oracle DB, JDBC + MyBatis, HikariCP
- **SQL 작성**: Mapper XML

![Spring](https://img.shields.io/badge/Spring-6DB33F?style=for-the-badge&logo=spring&logoColor=white)
![Java](https://img.shields.io/badge/Java-007396?style=for-the-badge&logo=java&logoColor=white)
![MyBatis](https://img.shields.io/badge/MyBatis-1E4A69?style=for-the-badge&logo=mybatis&logoColor=white)
![Spring Security](https://img.shields.io/badge/Spring_Security-6DB33F?style=for-the-badge&logo=springsecurity&logoColor=white)
![Oracle](https://img.shields.io/badge/Oracle_DB-F80000?style=for-the-badge&logo=oracle&logoColor=white)
![JDBC](https://img.shields.io/badge/JDBC-0082FC?style=for-the-badge&logo=java&logoColor=white)
![HikariCP](https://img.shields.io/badge/HikariCP-66FF66?style=for-the-badge&logo=hikari&logoColor=white)

---

### 빌드 도구 / 개발 환경
- **IDE**: Eclipse  
- **빌드 도구**: Maven  
- **서버**: Apache Tomcat  
- **버전 관리**: Git / GitHub  
- **패키징**: WAR  

![Eclipse](https://img.shields.io/badge/Eclipse-2C2255?style=for-the-badge&logo=eclipse&logoColor=white)
![Maven](https://img.shields.io/badge/Maven-C71A36?style=for-the-badge&logo=maven&logoColor=white)
![Tomcat](https://img.shields.io/badge/Apache_Tomcat-F8DC75?style=for-the-badge&logo=apachetomcat&logoColor=black)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)

---

## #1. 설명

### 시스템 아키텍처
시스템 아키텍처는 클라이언트와 서버 간의 관계 및 데이터 흐름을 설명합니다.  
아키텍처는 다음과 같은 계층으로 나눠집니다:
- **클라이언트 (브라우저)**: 사용자가 데이터를 입력하고 결과를 출력받는 사용자 인터페이스.
- **웹 서버**: 사용자 요청을 받아 웹 애플리케이션 서버로 전달.
- **웹 애플리케이션 서버(WAS)**: 요청 처리 및 비즈니스 로직 수행 (Spring Framework 사용).
- **데이터베이스**: Oracle DB로 사용자 데이터와 시스템 데이터를 저장.

### 시스템 다이어그램
다음 이미지는 시스템 아키텍처를 설명하는 다이어그램입니다.

![시스템 아키텍처](https://github.com/user-attachments/assets/4473b1d2-2f72-4336-ba9f-422d00708de0)
![시스템 흐름도](https://github.com/user-attachments/assets/c85c149c-dd1d-4115-82b8-cc52547255b3)
---

## #2. 요구 사항 분석
- **로그인 기능**: 관리자 로그인을 하지 않으면 메인화면 이동 불가. 로그인된 사용자만 고객/피보험자/계약/공지사항 CRUD 허용.
- **고객 관리**: 고객 등록 시 필수 항목: 고객 ID, 비밀번호, 고객 이름, 생년월일, 성별, 연락처. 
  - 고객 정보 수정은 고객 ID, 생년월일, 성별, 권한, 등록일 제외 수정 가능.
  - 피보험자 미등록 시 고객 삭제 처리 가능.
- **피보험자 관리**: 피보험자 등록 시 필수 항목: ID, 이름, 생년월일, 성별.
- **계약 관리**: 계약 번호는 자동 등록, 계약 시작일 필수 입력.
- **공지사항 관리**: 공지사항 제목, 내용 필수 입력. 중요 공지 여부 설정 가능.

---

## #3. 워크플로우 영상
각 기능별 워크플로우 영상은 아래와 같습니다. 각 링크를 클릭하여 해당 기능의 실행 과정을 확인할 수 있습니다.

### 1. 로그인
로그인 화면을 통해 사용자 인증을 처리하는 과정입니다.  
<a href="https://github.com/user-attachments/assets/fdf8c9ce-6521-43a4-99b9-085c7c7da329">
  로그인 영상
</a>

### 2. 고객 관리
고객 목록 조회, 고객 등록, 수정, 삭제 기능을 보여주는 영상입니다.  
먼저 두 명의 고객을 등록한 후, 한 명은 수정 후 삭제하고,  
다른 한 명은 이후 피보험자 등록에서 선택할 수 있도록 목록에 남깁니다.  
<a href="https://github.com/user-attachments/assets/8bcd7ab3-ecab-4030-a1ae-37d0a0df6c62">
  고객 관리 영상
</a>

### 3. 피보험자 관리
피보험자 목록 조회, 신규 등록, 정보 수정, 삭제 과정을 시연합니다.  
한 명의 고객을 선택하여 두 명의 피보험자를 등록한 뒤,  
한 명은 잘못 입력된 이름과 성별을 수정하고,  
다른 한 명은 삭제합니다.  
마지막에는 계약 등록 시 사용할 피보험자를 목록에 남겨둡니다.  
<a href="https://github.com/user-attachments/assets/6f9a2c6b-1716-4572-b60b-4d108225fceb">
  피보험자 관리 영상
</a>

### 4. 계약 관리
계약 등록
계약 등록 페이지에서 고객 검색 버튼을 클릭하여 팝업창에서 고객을 선택합니다.<br>
선택된 고객의 피보험자 목록이 자동으로 불러와지면, 드롭다운에서 피보험자를 선택하여 이름을 자동으로 입력합니다.<br>
보험 상품명을 선택하고, 계약 시작일은 오늘 날짜로, 계약 종료일은 임의의 1~2년 뒤 날짜로 설정합니다.<br>
계약 상태를 ACTIVE로 설정한 후 등록 버튼을 클릭하여 목록에서 신규 계약 등록 여부를 확인합니다.

계약 수정
목록에서 방금 등록한 계약의 수정 버튼을 클릭합니다.
보험 상품명을 다른 항목으로 변경합니다.(예: 실손보험 → 암보험)<br>
저장 버튼을 클릭하여 목록에서 수정된 내용을 확인합니다.

계약 삭제
목록에서 수정한 계약의 삭제 버튼을 클릭합니다.
삭제 확인 후 목록에서 해당 계약이 제거되었는지 확인합니다.<br>
<a href="https://github.com/user-attachments/assets/30fbc9cb-e2d6-4730-b5f1-fda84c3316e2">
  계약 관리 영상
</a>

### 5. 공지사항 관리
공지사항 목록 조회, 등록, 수정, 삭제 과정을 시연합니다.  
두 건의 공지를 등록한 뒤, 한 건은 내용 추가 및 중요 공지로 수정하고,  
다른 한 건은 상세보기 화면에서 삭제를 진행합니다.  
<a href="https://github.com/user-attachments/assets/0e4147af-21f3-44ed-bd30-3a39b8b2132c">
  공지사항 관리 영상
</a>

---

## 📄 데이터베이스 설계 (ERD)
![ERD](https://github.com/user-attachments/assets/0f1a88da-d62d-468b-befd-a6b009c5152c)

---
