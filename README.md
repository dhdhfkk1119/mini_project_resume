
# 📠 JOIN(공고 지원 사이트)
---
## 개발프로그램 및 세부사항 
#### 개발 프로그램 : IntellJ Community
#### 개발 언어 및 프레임 워크 : JAVA(SpringBoot) - Mustahce 엔진 사용
#### 개발 DB : MySQL(8.0) , MySQLWorkBench
#### 데이터베이스 연결 : ORM(JPA)
#### 개발 인원 : 4명 
#### Build Tool : Gradle
#### 개발 기간 : 6/24 ~ 7/7 일 (18일)
---

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


---

## 🔧 주요 기능

### 📄 게시판

- 게시글 목록 조회 (페이징, 정렬, 검색 포함)
- 게시글 상세 보기
- 게시글 작성, 수정, 삭제
- 게시글 좋아요 / 좋아요 취소
- 내가 쓴 게시글 목록 조회
- 내가 좋아요한 게시글 목록 조회
- 내가 댓글 단 게시글 목록 조회
- 이미지 업로드 (Toast UI Editor) -> 너무 어려워서 중도 포기 벽느낌

### 💬 댓글

- 댓글 작성 (부모/자식 댓글 구조)
- 댓글 수정 / 삭제
- 비밀댓글 기능 (`isSecret` 처리)
- 본인만 댓글 수정/삭제 가능

### 🔐 인증

- 로그인 기반 인증 처리
- 본인만 수정/삭제 가능하도록 인가 처리
- 로그인하지 않으면 글쓰기/댓글 작성 불가

---

## 🧩 화면-API 매핑표

| 화면 (기능)               | HTTP Method | URL                                         | Controller Method         | 로그인 필요 |
|---------------------------|-------------|---------------------------------------------|----------------------------|--------------|
| 게시글 목록 페이지        | GET         | `/board/list`                               | `listBoards()`             | ❌           |
| 게시글 상세 페이지        | GET         | `/board/{id}`                               | `viewBoard()`              | ❌           |
| 게시글 작성 페이지        | GET         | `/board/new`                                | `newBoardForm()`           | ✅           |
| 게시글 작성 처리          | POST        | `/board`                                    | `createBoard()`            | ✅           |
| 게시글 수정 페이지        | GET         | `/board/{id}/edit`                          | `editBoardForm()`          | ✅           |
| 게시글 수정 처리          | POST        | `/board/{id}/edit`                          | `updateBoard()`            | ✅           |
| 게시글 삭제 처리          | POST        | `/board/{id}/delete`                        | `deleteBoard()`            | ✅           |
| 게시글 좋아요 토글        | POST        | `/board/{boardId}/like`                     | `toggleLike()`             | ✅           |
| 내가 쓴 글 목록           | GET         | `/board/my-list`                            | `myBoards()`               | ✅           |
| 내가 좋아요한 글 목록      | GET         | `/board/likes`                              | `likedBoard()`             | ✅           |
| 내가 댓글 단 글 목록       | GET         | `/board/comments`                           | `myComments()`             | ✅           |
| 나의 게시글 목록 (페이징) | GET         | `/board/my-boards`                          | `myBoardsPaging()`         | ✅           |
| 게시글 전체 목록 (검색)   | GET         | `/board/boards`                             | `boardList()`              | ❌           |
| 댓글 작성 (Board)         | POST        | `/board/{boardId}/comment`                  | `writeComment()`           | ✅           |
| 댓글 작성 (Comment 전용)  | POST        | `/comments/{boardId}/comment`               | `writeComment()`           | ✅           |
| 댓글 수정                 | POST        | `/comments/{id}/edit`                       | `editComment()`            | ✅           |
| 댓글 삭제                 | POST        | `/comments/{id}/delete`                     | `deleteComment()`          | ✅           |

---

## 4. 🛠 기술 스택

| 구분        | 사용 기술 |
|-------------|------------|
| Language    | Java 17 |
| Framework   | Spring Boot 3.x |
| ORM         | Spring Data JPA |
| Template    | Mustache |
| Database    | MySQL |
| Build Tool  | Gradle |
| Editor      | Toast UI Editor (이미지 업로드 지원) |
| HTML 파싱   | Jsoup (댓글 내용 정제 처리) |
| Auth        | 세션 기반 로그인 (`SessionUser`) |

---


### 로그인을 해야만 글쓰기 가능
![로그인 인증 알림](https://github.com/user-attachments/assets/98568c58-6e14-44b7-b3f4-cff2716bb8c5)

### 글쓰기 기능
![글쓰기](https://github.com/user-attachments/assets/4f9b26ec-09c8-4911-9c85-3b8afccb94f8)

### 글 삭제 기능
![글 삭제 기능](https://github.com/user-attachments/assets/fbf463d6-343f-4624-918f-2d4abc0827fa)

### 댓글 달기,수정,삭제,답글 기능
![댓글 수정,삭제,답글](https://github.com/user-attachments/assets/b9d4564c-ab59-476e-98a2-038d429bdf01)

### 좋아요, 비밀 댓글 기능
![좋아요,비밀댓글](https://github.com/user-attachments/assets/1f2f45ab-38a0-4e59-8fa6-73a4d08ac490)

### 페이징 정렬,조회,검색 기능
![페이징 정렬,조회,검색](https://github.com/user-attachments/assets/93c13e22-08c6-4a0f-be9f-02218f5fa245)

### 내가 댓글단 게시물,찜한,내 게시물 조회
![회원정보에서 경로 설정](https://github.com/user-attachments/assets/52e2383a-9bb3-4ad6-804f-0849a72959a5)




