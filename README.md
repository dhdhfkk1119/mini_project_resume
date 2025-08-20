# 📠 JOIN(공고 지원 사이트)

## 개발프로그램 및 세부사항 

#### 개발 프로그램 : IntellJ Community
#### 개발 언어 및 프레임 워크 : JAVA(SpringBoot) - Mustahce 엔진 사용
#### 개발 DB : MySQL(8.0) , MySQLWorkBench
#### 데이터베이스 연결 : ORM(JPA)
#### 개발 인원 : 4명 
#### Build Tool : Gradle
#### 개발 기간 : 6/24 ~ 7/7 일 (18일)


## 📖 프로젝트 주제 및 내용

JOIN은 취업 준비생들이 겪는 어려움을 해소하고, 취업
성공률을 높이기 위해 세상에 존재하는 다양한 취업 정보를
한 곳에 모아 제공하는 웹 플랫폼입니다 .
사용자는 기업 공고, 채용 정보, 이력서 작성 팁, 면접 후기 등
실질적인 취업 관련 자료를 쉽게 검색하고, 자신의 상황에
맞는 맞춤형 정보를 얻을 수 있습니다.
또한, 회원가입 기능을 통해 기업과 일반 구직자가 각각의
권한으로 공고 등록, 지원, 좋아요, 마이페이지 기능 등을
사용할 수 있도록 하여, 사용자 친화적인 맞춤형 서비스를
구현합니다.



# 📄 프로젝트 소개

### 💻 프로젝트: 온라인 구인/구직 플랫폼 "Join"

* **프로젝트 주제**: 취업 구직 사이트 (사람인과 유사)
* **개발 기간**: 2024.06.24 ~ 2024.07.07 (약 2주)
* **개발 인원**: 3명
* **프로젝트 목표**: 구인/구직을 원하는 취업 준비생들에게 기업에 대한 정보를 제공하여 효율적인 구직 활동을 돕는 웹 서비스 개발


### ✨ 내가 담당한 주요 기능 및 구현
이 프로젝트에서 제가 주도적으로 설계하고 구현한 기능은 다음과 같습니다.

* **메인 페이지 및 마이페이지**:
    * **기능**: 전체 구인공고를 최신순으로 정렬하여 보여주며, 일반/기업 회원을 위한 마이페이지와 헤더/푸터 등 공통 레이아웃을 구성했습니다.
    * **구현**: Spring MVC의 **`Controller`**를 통해 데이터를 처리하고, **Mustache** 템플릿 엔진을 활용하여 동적인 웹 페이지를 렌더링했습니다.

* **로그인/회원가입 기능**:
    * **기능**: 일반 회원과 기업 회원의 가입 및 로그인을 처리합니다.
    * **구현**: 로그인 시 **`HttpSession`**에 `SessionUser` 객체를 저장하여 사용자 인증을 관리했습니다. 또한, 회원가입 시에는 **JavaScript(Fetch API)**를 이용해 아이디 중복을 실시간으로 확인하는 비동기 통신 로직을 구현했습니다.

* **구인공고 등록 및 관리**:
    * **기능**: 기업 회원이 구인공고를 작성, 수정, 삭제하고, 등록된 공고 목록을 조회할 수 있습니다.
    * **구현**: 로그인된 기업 회원만 접근할 수 있도록 **인터셉터**를 구성하여 권한을 제어했습니다. `RecruitController` 내에서 **`@PathVariable`**을 통해 특정 공고를 식별하고, 비동기 처리를 위한 **`@ResponseBody`**를 활용하여 데이터만 JSON 형태로 반환하는 API를 구현했습니다.

* **구인 공고 지원 및 좋아요 기능**:
    * **기능**: 일반 회원이 공고에 지원하거나 '좋아요'를 누를 수 있습니다.
    * **구현**: **`@PostMapping`**을 통해 좋아요 토글 기능을 구현했으며, 중복 지원을 방지하기 위해 서비스 레이어에서 확인 로직을 추가했습니다.

---

### 🛠️ 기술 스택 및 의존성

| 구분        | 사용 기술 |
|-------------|------------|
| Language    | Java 21 |
| Framework   | Spring Boot 3.x |
| ORM         | Spring Data JPA |
| Template    | Mustache |
| Database    | MySQL |
| Build Tool  | Gradle |
| Editor      | Toast UI Editor (이미지 업로드 지원) |
| HTML 파싱   | Jsoup (댓글 내용 정제 처리) |
| 데이터베이스 연결 | ORM(JPA) |
| Auth        | 세션 기반 로그인 (`SessionUser`) |

**주요 의존성**:
* **Spring Boot Starter (Web, Data JPA)**: 웹 애플리케이션 및 JPA 기반의 데이터베이스 연동을 위해 사용했습니다.
* **Spring Boot Starter Validation**: `@Valid` 어노테이션을 사용하여 DTO의 유효성 검증을 처리했습니다.
* **Spring Security Crypto**: `PasswordEncoder`를 활용해 사용자 비밀번호를 안전하게 해싱했습니다.
* **Lombok**: 보일러플레이트 코드를 줄여 개발 생산성과 코드 가독성을 높였습니다.

---

### 🗂️ 개발 의존성 
```java
dependencies {
	// lombok 의존성 추가
	compileOnly 'org.projectlombok:lombok'
	annotationProcessor 'org.projectlombok:lombok'
	// 테스트용 lombok 의존성 추가
	testCompileOnly 'org.projectlombok:lombok'
	testAnnotationProcessor 'org.projectlombok:lombok'

	// JPA 의존성 설정(ORM -- 자바 진영 --> JPA(스펙:인터페이스) --> 하이버 네이트
	implementation 'org.springframework.boot:spring-boot-starter-data-jpa'
	implementation 'org.springframework.boot:spring-boot-starter-mustache'
	implementation 'org.springframework.boot:spring-boot-starter-web'
	implementation 'org.jsoup:jsoup:1.17.2'


	implementation group: 'org.apache.commons', name: 'commons-lang3', version: '3.10'

	developmentOnly 'org.springframework.boot:spring-boot-devtools'
	runtimeOnly 'com.h2database:h2'
	runtimeOnly 'com.mysql:mysql-connector-j'

	testImplementation 'org.springframework.boot:spring-boot-starter-test'
	testRuntimeOnly 'org.junit.platform:junit-platform-launcher'

	// https://mvnrepository.com/artifact/org.apache.commons/commons-lang3
	implementation("org.apache.commons:commons-lang3:3.10")

	// 비밀번호 암호화 passwordEncoder
	implementation 'org.springframework.security:spring-security-crypto:5.7.1'

	// @NotBlank, @NotNull, @Email 등과 같은 유효성 검사 애노테이션 사용
	implementation 'org.springframework.boot:spring-boot-starter-validation'

}
```
### 🎞️ 구현 영상 및 이미지 

### 일반 유저 회원 가입 
![memberSign](https://github.com/user-attachments/assets/2d8f7294-27da-410f-816e-7fe237871cbc)

### 기업 유저 회원 가입 
![naverSign](https://github.com/user-attachments/assets/5dd86dab-1441-4f1d-91c4-39e93694572c)

### 로그인 
![login](https://github.com/user-attachments/assets/ad9dd389-1ed7-458c-b90b-ee3ff293fd3c)

### 프로필 이미지 업로드 
![profile-update](https://github.com/user-attachments/assets/3953bc55-b76d-4121-90e3-83e9244854df)

### 채용 공고 등록하기
![recruit](https://github.com/user-attachments/assets/968f59d4-f58d-4ebe-b3de-b36407c4ecb0)

### 공고 좋아요 및 지원하기 
![likeAndApply](https://github.com/user-attachments/assets/e751811c-ffc6-452a-9376-2fed158f9673)

### 전체적인 시현 영상 
유튜브 링크 



