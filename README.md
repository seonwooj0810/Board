# Board

Spring Boot + JPA 기반 게시판 만들기 학습 프로젝트입니다. 게시판 CRUD와 함께 AOP, 인터셉터, 전역 예외 처리, 페이징, 엑셀 다운로드 등 실무에서 자주 쓰는 기능을 함께 학습했습니다.

> 기존: Thymeleaf, MySQL, JPA, MyBatis 기반 게시판 (커밋 이력상 MyBatis → JPA로 전환)

## 사용 기술

- Java
- Spring Boot 2.7.5 (`spring-boot-starter-web`, `spring-boot-starter-data-jpa`, `spring-boot-starter-thymeleaf`)
- MySQL (`mysql-connector-j`)
- MyBatis (`mybatis-spring-boot-starter`) — 커밋 이력상 일부 제거/JPA 전환 진행
- Thymeleaf Layout Dialect
- Apache POI (`poi`, `poi-ooxml`) — 엑셀 처리
- Lombok, Spring Boot DevTools
- Gradle

## 학습한 내용

- **게시판 CRUD**: 목록/상세/작성 (`board/controller`, `templates/board/list·view·write.html`)
  - 페이지 컨트롤러(`BoardPageController`)와 API 컨트롤러(`BoardApiController`) 분리
  - DTO / Entity 분리 (`dto/Board*`, `entity/Board`), JPA `@Entity` + `@GeneratedValue(IDENTITY)`
- **회원(home) 기능**: 가입 폼·성공/실패 화면, 주소 팝업 (`home/*`, `templates/home/*`)
- **페이징**: 공통 파라미터/페이지네이션 (`paging/CommonParams`, `Pagination`)
- **AOP**: 로깅 Aspect (`aop/LoggerAspect`)
- **인터셉터**: 요청 로깅 (`interceptor/LoggerInterceptor`, `config/WebMvcConfig`)
- **전역 예외 처리**: `CustomException`, `ErrorCode`, `ErrorResponse`, `GlobalExceptionHandler`
- **엑셀 다운로드**: Apache POI 활용 (`CarExcelDto`, test `excelTest`)
- 설정 분리: `DatabaseConfig`, `HeaderConfig`, `WebMvcConfig`, `logback-spring.xml`

## 프로젝트 구조

```
src/main/java/com/study
├── BoardApplication.java
├── CarExcelDto.java
├── aop/LoggerAspect.java
├── board/ (controller, dto, entity, model)
├── home/ (controller, dto, entity, model)
├── config/ (DatabaseConfig, HeaderConfig, WebMvcConfig)
├── exception/ (CustomException, ErrorCode, ErrorResponse, GlobalExceptionHandler)
├── interceptor/LoggerInterceptor.java
└── paging/ (CommonParams, Pagination)
src/main/resources
├── mappers/                  # MyBatis 매퍼 XML
├── templates/ (board, home, layout)
└── logback-spring.xml
```
