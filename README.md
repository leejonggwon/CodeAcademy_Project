# 1. 서비스소개 
### 서비스명
- Coda Academy(코드아케데미)
- Spring Boot Security와 JWT 기반의 RBAC(역할 기반 권한 제어)를 적용한 RESTful 코딩 교육 관리 플랫폼(LMS) <br>

<br>

### 프로젝트 개요
- CodeAcademy는 Spring Boot를 기반으로 설계된 차세대 코딩 교육 관리 시스템(LMS)입니다 <br>
- 교육 현장에서 필수적인 역할별 권한 제어와 실시간 소통 기능을 RESTful API 환경에서 구현한 통합 플랫폼입니다 <br>

<br>

### 핵심 기술 
- **보안 및 인가 (Security & Auth)** - Spring Boot Security와 JWT를 결합하여 사용자 인증의 보안성을 높였으며, RBAC(Role-Based Access Control)를 통해 관리자, 강사, 수강생 각 역할에 최적화된 메뉴와 기능을 제공합니다 <br>
- **효율적인 데이터 구조 (RESTful API)** - 모든 커뮤니티 기능(게시판, 댓글, 대댓글)을 RESTful API로 설계하여 프론트엔드와의 통신 효율을 극대화하고 데이터 무결성을 확보했습니다 <br>
- **실시간 소통 (Real-time Interaction)** - Native WebSocket을 활용한 그룹별 오픈채팅 기능을 통해 교육생 간의 활발한 피드백과 실시간 질의응답 환경을 구축했습니다 <br>

<br>

### 프로젝트기간
- 2026.02 ~ 2026.04 <br>
<br>

### 시연영상
adadadadadadadaadad <br>
<br>

# 2. 기술스택 
### 2-1. Backend
- **Framework** - Spring Boot 2.7.3 <br>
- **Security** - Spring Security (Role-based Access Control) <br>
- **Language** - Java 8 (JDK 1.8) <br>
- **Build Tool** - Maven <br>
- **ORM/Data Access** - Spring Data JPA, MyBatis <br>

<br>

### 2-2. Database
- **RDBMS** - MySQL <br>
- **Connector** - MySQL Connector Java <br>

<br>

### 2-3. Frontend & View
- **View Engine** - JSP (Java Server Pages) <br>
- **Library** - JSTL, Spring Security Taglibs (로그인 세션 정보 표시) <br>
- **Embedded Server** - Tomcat (with Jasper for JSP rendering) <br>

<br>

### 2-4. Tools & Utilities
- Lombok <br>
- Spring DevTools <br>

<br>

# 3. Authentication & Security (Spring Security 스프링보안)
- 본 프로젝트는 Spring Security를 활용하여 인증 및 인가 시스템을 구축하였습니다 <br>
- 사용자 데이터는 Spring Data JPA를 통해 관리하고 모든 비밀번호는 보안을 위해 암호화되어 저장됩니다 <br>


### 3-1. Spring Security  핵심 아키텍처 및 흐름
1. 사용자가 로그인 폼에 ID/PW 입력 후 제출 → <br>
2. UerDetailsServiceImpl에서 DB의 회원 정보를 조회 → <br>
3. 조회된 정보를 CustomUser에 담아 반환 → <br>
4. Spring Security가 입력된 PW와 DB의 암호화된 PW를 비교(PasswordEncoder) → <br>
5. 인증 성공 시 SecurityContextHolder에 유저 정보 저장 후 세션 생성 → <br>
6. defaultSuccessUrl인 /board/list로 이동 <br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/a051a59d-f7cf-45c0-8b7a-957b6aa7b26f" width="800" />
</p>

<br>

### 3-2. 클래스별 상세 역할
#### 1) SecurityConfiguration (보안 설정)
- **비밀번호 암호화** - BCrypt 방식 등을 지원하는 DelegatingPasswordEncoder 사용 <br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/3b6063b9-0420-47c4-bfe4-c73486bd603e" width="800" />
</p>

- **권한별 접근 제어** <br>
 `/, /member/**` - 누구나 접근 가능 <br>
 `/board/**` - 로그인한 사용자만 접근 가능 <br>

- **커스텀 로그인/로그아웃** - 우리가 만든 /member/login 폼을 사용하도록 설정 <br>
- **CSRF 비활성화** - REST API 및 테스트 편의를 위해 설정 <br>

<br>

#### 2) UerDetailsServiceImpl
- UserDetailsService 인터페이스를 구현 <br>
- memberRepository를 통해 DB에서 username으로 회원 정보를 찾는다 <br>
- **예외처리**  <br>
 사용자가 없을 경우 `UsernameNotFoundException 발생` <br>
 탈퇴한 계정(enabled=false)일 경우 `DisabledException 발생` <br>

 <br>

#### 3) CustomUser (Security 전용 유저 객체)
- Spring Security의 `User` 클래스를 상속받아 구현한다 <br>
- DB의 Member 엔티티 정보를 Security의 Authentication 객체에 저장하기 위한 어댑터 역할을 한다 <br>
- 사용자의 권한을 `ROLE_ADMIN`, `ROLE_INSTRUCTOR`, `ROLE_STUDENT`와 같은 형태로 변환하여 부여한다 <br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/9e16a972-3d3a-4698-b2d8-2b35d51916e2" width="450" />
</p>

<br>

### 3-3. 주요보안 기능 구현 세부사항 

#### 1) 비밀번호 암호화 ((BCrypt)
- 회원가입 시 사용자의 비밀번호를 그대로 저장하지 않고, PasswordEncoder를 사용하여 `해시 암호화`한다 <br>
- **회원가입 컨트롤러** - @Autowired된 PasswordEncoder를 사용하여 가입 로직에서 즉시 암호화 처리한다 <br>
- **로그인 검증** - 사용자가 입력한 평문 비밀번호와 DB에 저장된 암호화된 비밀번호를 Security가 내부적으로 비교하여 인증 수행한다 <br>

<br>

#### 2) 권한별 접근 제어 (Authorization)
- 페이지별로 접근할 수 있는 권한을 다르게 설정하여 보안을 강화했습니다 <br>
- **PermitAll** - 메인 페이지 및 회원 관련 기능`(/member/**)`은 비로그인 사용자도 접근 가능 <br>
- **Authenticated** - 게시판 관련 기능`(/board/**)`은 로그인한 인증된 사용자만 접근 가능 <br>

<br>

#### 3) 커스텀 유저 디테일 서비스
- 세션에 사용자 정보(이름, 이메일 등)를 효율적으로 보관하기 위해 `CustomUser`를 구현한다 <br>
- `SecurityContextHolder`에 저장된 `CustomUser`를 통해 로그인한 사용자의 정보를 어디서든 편리하게 참조할 수 있다 <br>
- 계정 활성화 여부(Enabled) 체크 로직을 포함하여, 탈퇴하거나 정지된 계정의 로그인을 차단한다 <br>

<br>

#### 4) 로그인/회원가입 프로세스 요약
<p align="center">
  <img src="https://github.com/user-attachments/assets/73445c71-e8fa-4752-8464-c2c141d8bc5e" width="600" />
</p>

<br>


# 4. 시스템 아키텍처 (하이브리드 데이터 접근 구조 : JPA + MyBatis)
- **JPA 흐름** - Client → Controller → Service → Repository Interface(JPA) → DB <br>
- **MyBatis 흐름** - Client → Controller → Service → Mapper Interface → Mapper.xml → DB <br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/e8366817-ec03-4683-8404-595ad5d63551" width="700" />
</p>

<br>

# 5. DataBase E-R Diagram
<p align="center">
  <img src="https://github.com/user-attachments/assets/c518f700-e1cb-4a3b-9140-161e00fa2ed3" width="900" />
</p>
<br>


# 6. 서비스 흐름도
<p align="center">
  <img src="https://github.com/user-attachments/assets/b502355a-d0b0-46e6-858a-24df2dc94103" width="800" />
</p>


<br>

# 7.주요기능설명 #

## 1. 권한별 기능 제어(Technical Description)
### 1-1. 핵심 기술 구현 요약 <br>
- Spring Security와 JSTL/EL을 활용하여 위와 같은 역할 기반 접근 제어(RBAC) 모델을 설계 <br>
- 사용자 역할(Role)에 따라 시스템 자원(URL, API, 데이터)에 대한 접근 권한을 세밀하게 통제하여 보안성을 강화하였음 <br>
- **데이터 바인딩(EL)** - SecurityContext 내 Principal 객체에 실시간 접근하여 사용자 정보를 효율적으로 참조하였음 <br>
- **조건부 렌더링(JSTL)** - 권한 계층에 따라 메뉴 및 버튼 활성화 여부를 결정하는 태그 기반 로직을 설계하여 코드 가독성과 유지보수성을 확보하였음<br>
<br>

### 1-2. 상세 권한 및 역할 정의 <br>
### 1) 관리자(ADMIN) <br> 
- 시스템 전반의 제어 및 운영 정책을 총괄하는 최상위 권한 <br>
- **통합 관제** - 전체 교육과정 (강의, Q&A, 커뮤니티, 강사 전용 커뮤니티 등) 및 게시물에 대한 접근 및 관리 권한을 가집니다. <br>
- **회원 및 과정 관리** - 운영 정책에 따라 관리자 페이지를 통해 관리자를 제외한 회원의 정보 열람이 가능하며, 회원의 권한 등급 및 수강 교육과정을 동적으로 변경할 수 있습니다.<br>
- **콘텐츠 정화** - 부적절한 게시글 및 댓글을 강제 삭제할 수 있으며, 삭제 시 데이터 무결성을 위해 "관리자에 의해 삭제된 게시글/댓글입니다"라는 안내 문구가 표기됩니다. <br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/3ac9a603-38ab-4ae8-a157-43162619b3ac" width="900" />
</p>
<p align="center">
  <img  src="https://github.com/user-attachments/assets/d84c120e-767a-457c-a3c2-0ea9487369d4" width="900" />
  <br>
  [관리자 계정 - 관리자페이지]
</p>

<br>

### 2) 운영부(STAFF) <br> 
- 학생 지원 서비스를 담당하는 권한 <br>
- **부서별 역할 수행** - 교육운영, 취업지원, 홍보 등 각 부서의 목적에 맞춰 전체 교육과정의 커뮤니티에 접근하여 공지사항 등록 및 홍보 활동을 수행합니다. <br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/1e5eb11d-0719-4b4a-ab8d-0fdef4587c69" width="900" />
  <br>
  [운영부 계정 - 커뮤니티 게시글 업로드 및 수정]
</p>

<br>

### 3) 강사 (INSTRUCTOR) <br> 
- 학습 콘텐츠 생산 및 교육 서비스 제공을 담당하는 교육 권한 <br>
- **과정 중심 접근** - 본인이 배정된 특정 교육과정의 강의, Q&A, 오픈채팅, 커뮤니티 게시판에만 한정적으로 접근하여 보안성을 유지합니다. <br>
- **학습 지원** - 강의 자료 및 수업 내용을 등록하고, 댓글 및 Q&A 답글을 통해 수강생의 학습 질문에 답변합니다.<br>
- **가독성 강화** - 강사가 작성한 게시글 및 답변은 수강생이 쉽게 인지할 수 있도록 강조색으로 차별화되어 표시됩니다. <br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/6cb3b321-4340-406d-a9dd-92476daec6d6" width="900" />
  <br>
  [강사 계정 - 강의 게시글 업로드 및 수정]
</p>

<br>

### 4) 수강생 (STUDENT) <br> 
- 학습 콘텐츠를 소비하고 커뮤니티 활동에 참여하는 핵심 사용자 <br>
- **권한 승인 기반** - 회원가입 후 GUEST 상태에서 관리자의 승인을 거쳐 STUDENT 권한을 획득해야 정식 서비스 이용이 가능합니다. <br>
- **차등적 활동 권한** <br>
    **강의 게시판** - 강의 수강, 수업 자료 다운로드, 댓글 및 좋아요 작성이 가능하지만, 자료의 보호를 위해 게시물 등록, 답글쓰기, 수정, 삭제는 제한됩니다. <br>
    **Q&A 게시판** - 학습 관련 질문 등록이 가능하지만 강사의 전문적인 답변을 보장하기 위해 답글 쓰기 기능은 제한됩니다. <br>
    **커뮤니티** - 회원간 원활한 소통을 위해 모든 게시판 활동(쓰기, 수정, 삭제 등)이 허용됩니다. <br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/1c9bf984-640e-4e68-8439-a546a57e4f14" width="900" />
  <br>
  [수강생 계정 - Q&A 게시글 업로드 및 수정]
</p>
<br>


### 5) 승인대기 (GUEST) <br> 
- 회원가입은 완료했으나 서비스 이용 권한을 대기 중인 상태 <br>
- **접근 제한** - 관리자가 사용자 정보를 확인하여 수강생 또는 강사로 권한을 부여하기 전까지는 서비스 이용이 제한되는 준회원 상태 <br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/f049caba-de2b-472a-9610-3b4567d68a8c" width="900" />
  <br>
  [승인대기 계정]
</p>
<br>


### 6) 이용제한 (PENALTY) <br> 
- 운영 정책 위반으로 인해 서비스 이용이 정지된 상태 <br>
- **이용 제한** - 관리자에 의해 지정되며, 로그인은 가능하나 게시물 작성 및 조회 등 핵심 서비스 이용이 차단된 상태 <br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/578f9ea5-8df2-49b9-9a52-e6f65373d9d7" width="900" />
  <br>
  [이용제한 계정]
</p>
<br>


## 2. 다중 파일업로드 및 서버 저장 시스템 <br>
### 2-1. 핵심 기술 구현 요약 <br>
- 게시글 작성 시 사용자가 첨부한 여러 개의 미디어 파일(이미지, 문서 등)을 서버 로컬 파일 시스템에 안전하게 저장하고, 이를 DB와 매핑하여 관리하는 기능을 구현했습니다<br>
- `MultipartFile` 인터페이스를 사용하여 클라이언트로부터 전송된 데이터를 효율적으로 수신 및 처리합니다.<br>
- 동일한 파일명 업로드 시 데이터 덮어쓰기를 방지하기 위해 `System.currentTimeMillis()`를 활용하여 파일의 고유성을 확보하였습니다.<br>
- `File.mkdirs()`를 활용해 물리적 저장 경로가 존재하지 않을 경우 서버가 자동으로 디렉토리를 생성하도록 설계하여 운영 안정성을 높였습니다<br>
- 서버 부하를 줄이기 위해 파일 본체는 로컬 스토리지에 저장하고, 데이터베이스에는 파일명 및 경로 정보만을 저장하는 표준화된 업로드 아키텍처를 따랐습니다<br>
<br>

### 2-2. 게시판별 맞춤형 파일 필터링 <br>
- 사용자가 파일 선택 단계에서부터 게시판 목적에 맞는 형식만 선택할 수 있도록 HTML5의 accept 속성을 활용하여 프론트엔드 제어 및 UX를 개선했습니다.<br>
- 강의 게시판 (`accept="video/*"`): 학습 콘텐츠의 일관성을 위해 동영상 파일만 업로드 가능하도록 제한하여 강의 중심의 게시판 성격을 강화했습니다.<br>
- Q&A 게시판 (`accept="image/*"`): 코드 오류나 실행 화면 스크린샷 등 텍스트로 설명하기 어려운 상황을 시각적으로 공유할 수 있도록 이미지 파일만 허용하여 원활한 소통을 유도했습니다.<br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/70bc813a-8006-45a8-b3f1-5617380fca6e" width="900" />
  <br>
  [파일 업로드]
</p>

<br>

## 3. 파일 다운로드 시스템 <br>
### 3-1. 가상 경로 매핑을 통한 보안 강화 (`WebMvcConfigurer`) <br>
- 서버의 실제 저장 경로를 숨기고 가상 주소를 사용하여 외부의 직접적인 파일 시스템 접근을 차단하여 보안성을 높였습니다 <br>
- `addResourceHandler` : 브라우저의 요청 주소에 따라 서버 내 실제 파일 위치를 찾아 연결해주는 브라우징 구조를 설계했습니다.<br>

<br>

### 3-2. 안정적인 전송 환경 (인코딩 및 응답 제어) <br>
- `UriUtils.encode`를 적용해 한글 파일명 깨짐 방지 처리하여 안정적으로 다운로드 가능하게 구현했습니다.<br>
- Content-Disposition: attachment 설정을 통해 브라우저가 파일을 실행(이미지 미리보기 등)하지 않고 즉시 저장하도록 처리했습니다.<br>

<br>

### 3-3. 사용자 중심의 파일명 복구 로직 <br>
- 저장 시 사용된 `등호(=)`를 기준으로 문자열을 분리하여, 다운로드 시에는 시스템 식별자를 제외한 순수 원본 파일명만 추출하여 사용자에게 제공합니다.<br>
- 일반적인 언더바(_) 대신 `등호(=)`를 구분자로 사용했습니다. 이는 사용자가 입력한 파일명에 언더바가 포함되어 있을 경우, 실제 파일명과 시스템용 식별자가 혼동되어 데이터가 유실되거나 이름이 잘리는 현상을 방지하기 위한 의도적인 설계입니다.<br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/424a445c-e51d-410d-8171-fd3b362237b8" width="900" />
  <br>
  [파일 다운로드]
</p>

<br>

## 4. 댓글 및 대댓글(답글) 기능 <br>
### 4-1. 주요 특징 (Key Features) <br>
- **비동기 처리 (AJAX)** - 페이지 새로고침 없이 댓글 등록, 삭제, 대댓글 조회가 가능한 UX를 제공 <br>
- **계층형 데이터 구조** - `GROUP`, `SEQUENCE`, `LEVEL` 컬럼을 사용하여 원본 댓글과 대댓글 간의 부모-자식 관계를 논리적으로 구현 <br>
- **보안 및 권한 제어** - 작성자 본인 또는 관리자(ADMIN) 계정만 삭제가 가능하도록 프론트엔드와 백엔드에서 2중으로 검증<br>
- **상태 유지 삭제** - 데이터를 실제로 DB에서 지우지 않고 AVAILABLE 상태값을 변경하여 "삭제된 댓글입니다"라는 메시지를 남기는 방식<br>
`AVAILABLE == 'ADMIN'` : "관리자에 의해 삭제된 댓글입니다." 메시지 출력 <br>
`AVAILABLE == '0'` : "작성자에 의해 삭제된 댓글입니다." 메시지 출력 <br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/6b585f9e-3119-445f-812e-d9e6f71ce31a" width="400" />
  <br>
  [작성자 본인이 댓글 삭제시 "작성자에 의해 삭제된 댓글입니다." 메시지 출력]
  <br>
  [관리자가 댓글 삭제시 "관리자에 의해 삭제된 댓글입니다." 메시지 출력]
</p>
<br>

### 4-2. DB 설계 및 로직 <br>
- 계층형 구조를 구현하기 위해 `selectKey` 로직을 사용<br>
- **댓글 그룹화 (`GROUP`)** - 원본 댓글과 그에 달린 대댓글을 하나의 그룹으로 묶습니다. <br>
- **정렬 순서 (`SEQUENCE`)** - 그룹 내에서 댓글이 보여지는 순서를 결정합니다. 새 대댓글이 중간에 삽입될 경우 기존 순서를 +1 UPDATE 하여 순서를 유지합니다.<br>
- **계층 깊이 (`LEVEL`)** - 원본 댓글은 0, 대댓글은 1로 구분 했습니다.<br>
<br>

### 4-3. MyBatis를 활용한 계층 구조 생성 <br>
- 원본 댓글 등록 시 MAX(CMT_IDX)를 조회해 다음 그룹 번호를 자동으로 할당함<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/6c98d151-0c17-4b2d-afdd-3dafb043c888" width="800" />
</p>
<br>

### 4-4. 대댓글 동적 UI 렌더링 (jQuery) <br>
- 서버에서 받은 JSON 데이터를 바탕으로 $.each 반복문을 돌려 HTML을 생성하며, 대댓글 작성 폼은 `toggle()` 함수를 이용해 필요할 때만 나타나도록 구현<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/91bd1a5d-5e53-438e-bff2-590cf848c0f5" width="250" />
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/326e2933-8cb3-46de-9951-6d7a0353f5aa" width="400" />
  <br>
  [댓글과 대댓글 기능]
</p>
<br>


## 5. 실시간 그룹 오픈채팅 시스템 (WebSocket) <br>
### 5-1. 주요 특징 (Key Features) <br>
- **전이중 통신(Full-Duplex)** - 표준 `Native WebSocket API` 활용하여 서버와 클라이언트 간의 실시간 양방향 메시지 전송을 구현 <br>
- **그룹별 세션 관리** - 같은 그룹에 속한 사용자들끼리만 메시지를 주고받을 수 있도록 세션 필터링 로직을 설계 <br>
- **실시간 접속자 리스트** - `ServletContext`를 활용해 서버 전체의 접속자 현황을 관리하고, 사용자의 입장/퇴장 시 실시간으로 접속자 목록이 갱신되도록 구현<br>
- **Handshake 인터셉터** - `HttpSessionHandshakeInterceptor`를 통해 HTTP 세션 정보(로그인 아이디, 그룹명 등)를 웹소켓 세션으로 안전하게 전이시켜 활용<br>
<br>

### 5-2. [Server] 세션 핸들링 및 메시지 브로드캐스팅 <br>
- **접속 관리** - 사용자가 연결되면 `ArrayList<WebSocketSession>`에 저장하고, 입장 메시지를 동일 그룹 사용자들에게 전달한다 <br>
- **메시지 분기 처리** - 메시지 페이로드의 특정 접두사(`#$nickName_`)를 분석하여 입장 알림인지, 일반 채팅 메시지인지 판별하여 처리한다 <br>
- **비정상 종료 대응** - 브라우저 닫기나 네트워크 단절 시 `afterConnectionClosed`를 통해 세션을 즉시 제거하고 퇴장 알림을 보냄으로써 세션 누수를 방지한다 <br>
<br>

### 5-3. [Client] 동적 UI 및 웹소켓 이벤트 처리 <br>
- **이벤트 리스너** - onopen, onmessage, onclose 이벤트를 각각 정의하여 서버와의 연결 상태에 따른 UI 변화를 구현 <br>
- **조건부 렌더링** -서버로부터 받은 메시지가 '나'인 경우와 '타인'인 경우를 구분하여 말풍선 위치와 스타일을 다르게 렌더링 <br>


<p align="center">
  <img src="https://github.com/user-attachments/assets/887b8afc-0955-4332-9ec1-5264d3c2ee67" width="900" />
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/87044bf3-e999-450f-9486-af74dd61c0b4" width="400" />
  <br>
  [실시간 그룹 오픈채팅 기능]
</p>

<br>

## 6. 페이징 시스템 (Paging & Search System) <br>
### 6-1. 주요 구성 요소 <br>
- **Criteria** - `현재 페이지(page)`, `페이지당 게시글 수(perPageNum)`, `검색 조건(type, keyword)` 등 사용자가 요청한 데이터를 담는 객체 <br>
- **PageMaker** - 전체 게시글 수(totalCount)를 기반으로 `시작 페이지`, `끝 페이지`, `이전/다음 버튼 활성 여부`를 계산하는 페이징 연산 객체 <br>
- **Mapper (SQL)** - MySQL의 `LIMIT #{pageStart}, #{perPageNum}`을 사용하여 필요한 범위의 데이터만 효율적으로 조회<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/c995b28e-1319-4ea9-b82f-be5b243011fe"" width="250" />
  <br>
  [Criteria 클래스]
</p>
<br>

### 6-2. 페이징 계산 로직 <br>
- **끝 페이지 번호 (endPage)** - Math.ceil(현재 페이지 / 보여줄 페이지 수) * 보여줄 페이지 수 <br>
- **작 페이지 번호 (startPage)** - (끝 페이지 번호 - 보여줄 페이지 수) + 1 <br>
- **실제 최종 페이지 (tempEndPage)** - Math.ceil(전체 게시글 수 / 페이지당 게시글 수)<br>
- **보정 로직** - 계산된 endPage가 실제 tempEndPage보다 크면, endPage를 실제 마지막 페이지로 변경합니다 <br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/dd7d39df-9dae-439c-aaea-590203700d52" width="600" />
  <br>
  [PageMaker 클래스]
</p>
<br>

### 6-3. 데이터 흐름 (Data Flow) <br>
- **Request** - 사용자가 페이지 번호나 검색어를 클릭하면 Criteria 객체에 바인딩되어 Controller로 전달됩니다 <br>
- **Mapper** - pageStart (계산식: (page-1) * perPageNum)를 활용해 DB에서 해당 구간의 데이터만 조회합니다 <br>
- **Calculation** - totalCount를 조회한 후 PageMaker에 주입하여 하단 페이징 버튼에 필요한 정보를 생성합니다. <br>
- **View** - JSP에서 c:forEach와 c:if를 활용해 계산된 페이지 번호와 이전/다음 버튼을 동적으로 렌더링합니다. <br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/9a034d6c-bf5e-4f30-af9f-c56f4f6b4151" width="600" />
  <br>
  [Mapper (SQL)]
</p>
<br>

### 6-4. 주요 특징 <br>
- **검색 조건 유지** - 페이지를 이동하더라도 사용자가 선택한 검색 `타입(type)`과 `키워드(keyword)`가 input hidden 폼을 통해 계속 유지되도록 설계했습니다 <br>
- **Pagination** - Bootstrap 4의 `.pagination` 클래스를 활용한 UI를 제공하며, 현재 페이지(active 상태)를 시각적으로 구분했습니다 <br>
- **성능 최적화** - 전체 데이터를 가져오지 않고 MySQL의 `LIMIT 구문`을 사용하여 필요한 레코드만 조회함으로써 서버 부하를 최소화했습니다 <br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/15f3b199-cb49-4e4f-9e0f-e9b3d1bbc8a5" width="900" />
  <br>
  [Pagination 페이징 기능]
</p>
<br>


## 7. 검색 필터링 및 페이징 (Search & Pagination) <br>
사용자가 원하는 조건으로 게시글을 필터링하고` MyBatis 동적 SQL`과 `Criteria 패턴`을 적용했습니다 <br>

### 7-1. 핵심 로직 흐름 (Process Flow) <br>

- **파라미터 수집** - JSP에서 선택한 검색 `타입(type)`과 `키워드(keyword)`를 Criteria 객체에 담아 컨트롤러로 전송합니다 <br>
- **동적 SQL 생성** - MyBatis의 `<if> 태그`와 `<sql> 조각`을 활용하여 선택된 타입에 따라 WHERE 절을 동적으로 생성합니다 <br>
- **데이터 조회** - `LIMIT 명령어`를 통해 전체 데이터가 아닌 현재 페이지에 필요한 10개의 게시글만 효율적으로 가져옵니다 <br>
- **UI 유지** - 검색 후에도 사용자가 선택한 검색 조건과 입력값이 사라지지 않도록 `EL(${pageMaker.cri})`을 통해 입력 폼을 유지합니다<br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/f1591379-da31-45f5-926f-29f06a0c99a2" width="600" />
  <br>
  [MyBatis 동적 SQL]
</p>

<br>

### 7-2. 기술적 포인트 <br>

- **MyBatis 동적 SQL** - 중복되는 SQL을 방지하기 위해 <sql> 태그로 검색 로직을 분리하고, 필요한 쿼리에서 <include>하여 결합하는 방식을 사용했습니다 <br>
- **검색 조건 유지** - 검색 실행 후 페이지가 새로고침되어도 사용자가 어떤 조건으로 검색했는지 알 수 있도록 삼항 연산자를 이용해 selected 상태를 제어했습니다 <br>
- **검색 정보 유지** - 페이징 버튼 클릭 시 단순 링크 이동 대신, page, type, keyword 값을 포함한 Hidden Form을 전송(Submit)하는 방식을 채택하여 검색 결과를 끝까지 유지하도록 해결하였습니다<br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/75228965-70ef-4263-8be0-22757ab84a11" width="600" />
  <br>
  [다음 페이지 넘어가도 검색정보 유지]
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/50c21c40-cbf5-40b8-8dda-2652ffff748c" width="900" />
  <br>
  [검색 및 필터링 기능]
</p>

<br>

## 8. 비동기 좋아요(Like) 시스템 <br>
Ajax를 활용하여 페이지 새로고침 없이 실시간으로 작동하는 좋아요 기능을 구현했습니다 <br>

### 8-1. 핵심 로직 흐름 <br>
좋아요 클릭 시, 단순히 숫자만 올리는 것이 아니라 사용자별 상태(좋아요 여부)를 DataBase에서 관리하여 상태에 따라 동적으로 UI가 변경됩니다 <br>

**1. 상태 확인** - 사용자가 좋아요 버튼을 클릭하면 해당 게시물에 대한 사용자의 좋아요 기록(BT_LIKE)이 있는지 확인합니다 <br>
**2. 데이터 처리** <br>
- **기록이 없는 경우** - INSERT를 통해 새로운 좋아요 객체를 생성합니다 <br>
- **기록이 있는 경우** - UPDATE를 통해 LIKE_AVAILABLE 상태값을 변경(0 ↔ 1)합니다 <br>

**3. 카운트 반영** - 게시판 테이블(BT_BOARD)의 LIKE_COUNT를 증감시키고, Ajax를 통해 실시간으로 화면의 공감 숫자를 업데이트합니다 <br>
**4. UI 전환** - 좋아요 상태(1)면 빨간색 버튼, 취소 상태(0)면 라인 버튼으로 즉시 변경됩니다. <br>

<br>

### 8-2. 기술적 특징 <br>
- **RESTful API** - LikeRestController를 통해 클라이언트와 데이터를 JSON 기반으로 주고받습니다 <br>
- **실시간 UI 업데이트 (Ajax)** - success 콜백 함수 내에서 `showLike_count()`, `likeView()` 등을 호출하여 페이지 새로고침 없이 실시간 화면을 갱신합니다 <br>
- **상태 기반 처리** - DataBase에 사용자별 이력을 남겨 추후 '내가 좋아요 한 글 보기' 등의 기능 확장이 가능하도록 설계했습니다 <br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/ae6293ec-0f1d-4bdd-a34d-3745fedd6faf" width="900" />
  <br>
  [좋아요 기능 및 실시간 반영]
</p>

<br>

## 9. 계층형 답글 기능 <br>
원본 글(부모 글)에 대한 답변을 계층 구조로 시각화하고 관리할 수 있는 시스템입니다 <br>

### 9-1. 주요 특징 <br>
- **Threaded Structure** -`Group`, `Sequence`, `Level` 세 가지 필드를 활용하여 답글의 계층과 노출 순서를 정교하게 제어합니다<br>
- **Multi-File Support** - 답글 작성 시에도 원본 글과 동일하게 최대 3개의 파일을 독립적으로 업로드할 수 있습니다 <br>
- **Atomic Logic** - 기존 답글들의 순서를 한 단계씩 밀어내는 Update와 새로운 답글을 삽입하는 Insert를 하나의 트랜잭션으로 처리합니다<br>

<br>

### 9-2. 핵심 메커니즘 (Core Logic) <br>
답글이 달릴 때마다 전체 리스트의 정렬이 깨지지 않도록 로직을 수행합니다<br>

- **부모 정보 상속** - 부모 글의 `Group` 번호를 물려받아 같은 그룹으로 묶습니다 <br>
- **시퀀스 재정렬** - 부모 글보다 아래에 있는 기존 답글들의`Sequence`를 모두 +1 하여 공간을 확보합니다 (`replySeqUpdate`)<br>
- **계층 심화** - 부모 글의 `Level`에 +1을 하여 리스트에서 들여쓰기 처리가 가능하도록 합니다 <br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/9678f401-6cfa-41aa-b14c-ac99b120bfc2" width="400" />
  <br>
  [Reply Core Logic]
</p>
<br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/ce5b062d-69b7-4b15-9d78-256247b7a859" width="900" />
  <br>
  [답글기능 - Q&A 게시판]
</p>
<br>


## 10. 작성자 프로필 카드 <br>
게시글 리스트나 댓글 창에서 작성자의 이름을 클릭하면, 비동기 통신을 통해 해당 사용자의 상세 정보를 모달 형태로 제공하는 기능입니다 <br>

- **비동기 데이터 로딩 (AJAX)** -체 페이지 리로드 없이 클릭한 사용자의 정보를 서버에서 실시간으로 조회하여 사용자 경험(UX)을 극대화했습니다<br>
- **데이터 위임 처리** - 'data-writer'을 활용하여 리스트 렌더링 시점에 사용자 식별값(ID)을 미리 바인딩하고, 이벤트 발생 시 이를 활용해 정확한 데이터를 호출합니다. <br>
- **동적 UI 렌더링** - 서버로부터 받은 JSON 데이터를 바탕으로 프로필 이미지(이미지 없을 시 기본 이미지 대체), 닉네임, 권한(Role) 등을 동적으로 화면에 매핑합니다<br>

<br>

### 동작 흐름 <br>
1. 사용자가 .writer 클래스를 가진 요소를 클릭합니다 → <br>
2. jQuery AJAX가 클릭된 요소의 `data-writer` 속성값을 읽어 서버의 `/member/writerInfo` API로 전송합니다 → <br>
3. 서버는 MyBatis를 통해 DB에서 해당 유저의 정보를 조회한 후 JSON 형태로 반환합니다 → <br>
4. 반환된 데이터를 JavaScript로 가공하여 Bootstrap 모달의 각 필드에 데이터를 주입하고 모달을 띄웁니다 → <br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/4a6305aa-8cd5-44b9-8e8b-b30e05de7e1e" width="900" />
  <br>
  [작성자 프로필 카드 - 게시글 작성자 클릭시]
</p>

<br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/6cd47731-2389-4d68-845a-b0bc3f41851e" width="900" />
  <br>
  [작성자 프로필 카드 - 댓글/대댓글 작성자 클릭시]
</p>


<br>

# 8. 페이지별 기능 가이드 #

## 1. 메인 랜딩 페이지 (Main Landing Page)
- **서비스소개** - Code Academy의 비전과 교육과정을 한눈에 확인할 수 있는 랜딩페이지입니다 <br>
- **강의 카테고리 퀵 뷰** - Backend, Frontend, IT Startup 등 제공 중인 주요 교육과정을 카드 레이아웃으로 시각화하여 정보 접근성을 높였습니다 <br>
- **사용자 인증 관문** - 로그인 및 문의하기 버튼을 상단에 배치하여 서비스 이용의 편의성을 제공합니다 <br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/0fcbc207-5c8b-41c9-92c7-8681b5848cc1"  width="900" />
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/139a8f20-9f62-46ca-a119-343dd90f68f3" width="900" />
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/dbd6b570-20af-4ff3-9bea-8e4b55e8b352" width="900" />
</p>

<br>

## 2. 로그인 및 보안 시스템 (Login & Spring Security)

Spring Security를 활용하여 탄탄한 인증(Authentication) 및 인가(Authorization) 시스템을 구축했습니다.

- **Spring Security** - 사용자 인증 및 권한 부여(Authentication & Authorization)를 처리하며, 세션 관리를 통해 보안성을 확보했습니다<br>
- **Custom Login Form** - 시큐리티 기본 로그인 창 대신 프로젝트 테마에 맞춘 사용자 정의 로그인 페이지를 구현했습니다 <br>
- **비밀번호 시각화 제어 로직 (Manual State Control)** <br>
  - `attr()` 함수를 사용하여 input 태그의 type 속성을 password와 text로 동적 전환하는 로직을 구현했습니다 <br>
  - 상태 변화에 따라 버튼의 텍스트("보이기"/"숨기기")와 Font Awesome 아이콘을 실시간으로 업데이트하여 사용자에게 직관적인 시각적 피드백을 제공합니다 <br>
- **이미지 슬라이드(Carousel)** - Bootstrap4 Carousel을 활용하여 플랫폼의 주요 교육 과정(Back-End, AI 등)을 시각적으로 홍보하는 UI를 구성했습니다 <br>
- **접근 제어 (RBAC)** - 페이지별 권한 설정을 통해 비로그인 사용자의 특정 메뉴 접근을 원천 차단했습니다. <br>

<br>

<p align="center">
  <img  src="https://github.com/user-attachments/assets/ac1a81ae-ee1c-4538-8ea8-dc8a0a41c74c" width="600" />
   <br>
  [로그인페이지]
</p>



<br>

## 3. 회원가입 (Join Page)

### 1. 아이디 중복 확인(Ajax) / 닉네임 중복 확인 <br>
회원가입 시 사용자의 편의성을 높이기 위해 페이지 새로고침 없이 실시간으로 아이디 중복 여부를 확인하는 기능을 구현했습니다 <br>

- **핵심설계의도** <br>
  - **비동기 처리 (Ajax)** - 사용자 경험(UX)을 저해하지 않도록 페이지 전환 없이 데이터를 검증함 <br>
  - **Hybrid Architecture** - MyBatis를 활용해 DB 쿼리의 직관성을 높이고, Spring의 RestController 스타일로 응답을 처리함 <br>
  - **데이터 무결성** - 서버 사이드에서 DB를 직접 조회하여 중복된 아이디 생성을 원천 차단함 <br>
  
<br>

- **동작 흐름** <br>
1. 사용자가 아이디 입력 후 '중복확인' 버튼 클릭 → <br>
2. jQuery Ajax가 /registerCheck 경로로 입력된 username 전송 → <br>
3. Controller에서 Service/Mapper를 통해 DB 조회 → <br>
4. 아이디 존재 여부에 따라 0 또는 1을 반환 → <br>
5. 브라우저에서 반환값에 따라 모달(Modal)창으로 결과 알림 → <br>

### 2. 실시간 아이디 검증 시스템 <br>
사용자가 폼을 제출하기 전에 실시간으로 아이디 형식을 확인하여, 잘못된 데이터 입력을 방지하고 서버의 부담을 줄이도록 구현했습니다 <br>

- **동작 시점** - 사용자가 아이디를 입력할 때마다 onkeyup 함수 실행 <br> 
- **기술** - JavaScript + 정규 표현식 (Regex) <br>
- **목적** - 영문/숫자 조합 및 글자 수(6~20자) 조건을 만족하는지 실시간 피드백 제공 <br>
- **특징** - 서버에 요청을 보내지 않기 때문에 네트워크 자원을 아끼고 사용자에게 즉각적인 반응을 보여줌. <br>
  
<br>

### 3. 비밀번호 검증 및 보안 관리 (Password Management) <br>

#### 3-1. 주요기능 <br>
- **실시간 일치 검사 (passwordCheck)** - 두 개의 입력창(password1, password2)에 입력된 값을 실시간으로 비교하여 일치 여부를 피드백함 <br> 
- **복합 정규표현식 검사** - 보안 강화를 위해 영문, 숫자, 특수문자가 모두 포함된 8~20자 조합만 허용함 <br>
- **UI/UX 편의 기능** - 영문/숫자 조합 및 글자 수(6~20자) 조건을 만족하는지 실시간 피드백 제공 <br>
- **보안 데이터 처리** - 최종적으로 검증된 비밀번호만 hidden 타입의 password 필드에 담아 서버로 전송함. <br>

<br>

#### 3-2. 기술적 세부 사항 <br>
- **정규 표현식 (Regex) 정책** - 비밀번호는 `영문 숫자 특수문자 포함 8~20자`를 만족해야 제출이 가능하도록 설계하였음 <br> 
- **실시간 일치 및 데이터 바인딩** - 사용자가 비밀번호를 입력할 때마다 onkeyup 이벤트가 발생하며, 두 값이 일치할 때만 실제 서버로 전송될 hidden 필드에 값을 복사하여 제출했음 <br>
- **비밀번호 보이기/숨기기 (UX 개선)** - 비밀번호 입력 실수로 인한 로그인 실패를 줄이기 위해 토글 기능을 추가하여 `type="password"`와 `type="text"`를 동적으로 변경하며 아이콘과 버튼 스타일도 함께 변경되도록 구현했다 <br>

<p align="center">
  <img  src="https://github.com/user-attachments/assets/3a59edda-fc5f-495d-8482-9baedc5ddfdf" width="600" />
   <br>
  [회원가입 페이지]
</p>

<br>

## 4. 강의 전용 게시판 
Spring Boot와 AJAX를 활용하여 강사가 강의 영상 및 학습 자료를 공유하고, 수강생이 이를 소비하며 피드백을 주고받을 수 있는 강의 전용 게시판입니다 <br>

- **목적** - 강사와 수강생 간의 원활한 학습 콘텐츠 공유 및 양방향 피드백 지원 <br>
- **핵심 가치** - 역할에 따른 엄격한 기능 제한 및 미디어 중심의 사용자 경험 제공 <br>

<br>

### 1. Role-Based Access Control (RBAC) & UI 맞춤화 <br>
- **권한별 UI 차별화** - Spring Security의 Role 정보를 활용하여 화면 구성을 동적으로 제어합니다 <br>
- **ADMIN / INSTRUCTOR (관리자/강사)** - 강의 콘텐츠 CRUD 및 영상/첨부파일 업로드 권한 보유. (업로드 UI 및 버튼 활성화) <br>
- **STUDENT (수강생)** -학습 콘텐츠 열람, 댓글 작성, 좋아요(공감)를 통한 강의 평가 기능 수행 <br>

<br>

### 2. 미디어 특화 업로드 시스템 (Security & Filtering) <br>
- **2단계 영상 필터링** <br>
  - **HTML5 필터** - `accept="video/*"` 속성을 통해 파일 선택 단계에서 동영상 외 파일 원천 차단 <br>
  - **JavaScript 유효성 검사** - 파일 선택 후 `file.type.startsWith("video/")` 로직을 통해 영상 파일 여부를 재검증하여 데이터 정합성 보장. <br>
- **멀티 첨부파일 구조** - 영상 파일 1개와 일반 학습 자료(첨부파일)를 분리하여 업로드할 수 있는 유연한 구조 설계<br>

<br>

### 3. 게시글 수정 시 첨부파일 관리 <br>
- **동적 버튼 렌더링** - 수정 폼 진입 시, 서버에서 가져온 attached_data(파일명)의 존재 여부를 확인하여 '삭제 버튼'을 동적으로 노출합니다<br>
- **데이터 정합성 유지** <br>
  - 사용자가 '삭제 버튼'을 클릭하면 jQuery의 `.remove()`를 사용하여 폼 내의 hidden input 요소를 즉시 제거합니다 <br>
  - 이를 통해 submit 시 서버에 파일 정보가 전달되지 않도록 하여, 데이터베이스에서도 해당 파일 경로를 비우도록 연동했습니다 <br>
- **사용자 피드백(UX)** - 삭제 버튼 클릭 후 버튼의 상태(텍스트, 스타일)를 즉시 변경하여 사용자가 삭제 작업이 완료되었음을 직관적으로 인지하게 했습니다 <br>

<br>

### 4. 비동기 인터랙션 (Interactive Experience) <br>
- **AJAX 기반 SPI** - jQuery AJAX를 통해 페이지 리로드 없이 게시글 상세 보기, 실시간 댓글 로드, 공감 수 업데이트 등 매끄러운 사용자 인터페이스 구현 <br>
- **동적 폼 제어** - 첨부파일 추가' 버튼 클릭 시 비동기적으로 추가 업로드 필드를 생성하여 사용자 편의성 증대. <br>

<p align="center">
  <img  src="https://github.com/user-attachments/assets/792d0833-0778-4c7b-8097-5367c79d50a6" width="900" />
   <br>
  [강사 계정 - 강의 전용 게시판 업로드 ]
</p>

<br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/75bbada5-270a-48bb-b3d4-69b9192c9cd7" width="900" />
   <br>
  [강사 계정 - 강의 전용 게시판 수정]
</p>

<br>

<p align="center">
  <img  src="https://github.com/user-attachments/assets/c86ba9ca-4d4c-4b91-a2f0-695207bef100" width="900" />
</p>
<p align="center">
  <img  src="https://github.com/user-attachments/assets/e76a901d-030e-4e1a-a830-6712b9c9b75c" width="900" />
  <br>
  [수강생 계정 - 강의 전용 게시판 ]
</p>

<br>

## 5. Q&A 게시판 (Interactive Inquiry System)
수강생의 기술적 질의에 대해 강사와 관리자가 전문적인 피드백을 제공하는 양방향 소통 게시판입니다 <br>

- **엄격한 권한 분리를 통한 답변 신뢰성 확보**  <br>
  - 수강생 간의 답변 혼선을 방지하기 위해 강사와 관리자(Role-Based)에게만 답글 작성 권한을 부여했습니다 <br>
  - Spring Security 태그 라이브러리를 활용해 수강생 화면에서는 답글 작성 버튼을 서버 사이드에서부터 원천 차단했습니다 <br>
  
- **이미지 기반의 질의응답 최적화**  <br>
  - 이미지 기반의 질의응답에 최적화된 업로드 환경을 제공합니다 <br>
  - JavaScript를 활용한 MIME 타입 사전 검증으로 이미지 외 불필요한 파일 업로드를 방지하여 서버 자원을 효율적으로 관리합니다 <br>

<p align="center">
  <img  src="https://github.com/user-attachments/assets/9b6b96b8-62a1-461c-8a0f-9dab863e0e71" width="900" />
</p>
<p align="center">
  <img  src="https://github.com/user-attachments/assets/399d6bd4-305c-41e5-81b8-399062009afb" width="900" />
  <br>
  [Q&A 게시판 - 강사계정 ]
</p>

<br>

## 6. 교육과정별 커뮤니티 게시판 
- 서비스 이용자 간 학습 경험을 공유하고, 서로 도움을 주고받는 자율적인 개발자 커뮤니티 환경을 제공하는 것을 목표로 합니다 <br>
- 공지사항, 취업정보, 스터디 모집, 학습 공유 등 다양한 주제로 자유롭게 글을 작성하고 의견을 나눌 수 있습니다 <br>
- 수업게시판 및 Q&A 게시판과 달리, 수강생 누구나 제약 없이 자유롭게 이용할 수 있습니다 <br>
- 욕설, 비방, 광고 등 게시판 목적에 맞지 않는 글은 운영 정책에 따라 관리자가 게시글 및 댓글을 삭제할 수 있습니다 <br>


<p align="center">
  <img  src="https://github.com/user-attachments/assets/3d7d393d-4ce5-418e-b20c-5413e1209623" width="900" />
</p>
<p align="center">
  <img  src="https://github.com/user-attachments/assets/ff09dea6-4bc6-4514-9e43-0a1dd9a80b86" width="900" />
  <br>
  [커뮤니티 게시판]
</p>

<br>

## 7. 관리자 페이지 (Admin Management System) 
플랫폼의 전체 사용자를 모니터링하고, 회원별 권한 및 교육과정을 실시간으로 제어할 수 있는 중앙 집중형 관리 시스템입니다 <br>

### 1. 보안 및 접근 제어 <br>
Spring Security를 활용한 접근 제어 로직을 적용했습니다 <br>
- **권한 기반 URL 보호** <br>
  - SecurityConfig 설정을 통해 /member/adminPage를 포함한 모든 관리자용 API와 페이지 접근을 ROLE_ADMIN 권한 소유자로 제한했습니다 <br>
  - 권한이 없는 사용자(STUDENT, GUEST 등)가 URL을 직접 입력해 접속을 시도할 경우 로그인 페이지/메인 페이지로 강제 리다이렉트되도록 설계했습니다 <br>
- **UI 동적 제어** <br>  
  Spring Security 태그 라이브러리(`<sec:authorize access="hasRole('ADMIN')">`)를 사용하여, 관리자 메뉴 버튼 자체가 일반 사용자에게는 렌더링되지 않도록 처리했습니다 <br>
 
<br>


### 2. 주요 기능  <br>
- **동적 회원 관리** <br>
  전체 회원 리스트를 비동기(AJAX)로 로드하며, 페이지 새로고침 없이 회원 상태 확인 및 정보 수정이 가능합니다. <br>
- **역할 기반 권한 제어 (RBAC - Role Update)** <br>  
  - GUEST(승인대기), STUDENT(수강생), INSTRUCTOR(강사), STAFF(운영부), PENALTY(이용제한) 등 5단계 권한 체계를 적용했습니다<br>
  - 관리자는 사용자의 권한을 즉시 변경할 수 있습니다
- **멀티 필터링 검색 시스템** <br>  
  - **키워드 검색** - 이름, 아이디, 닉네임 기반의 상세 검색 기능을 제공합니다<br>
  - **권한별 필터링** - 특정 역할을 가진 회원들만 따로 모아볼 수 있는 전용 필터를 구현하여 관리 편의성을 높였습니다<br>

<br>
  
### 3. 기술적 구현특징 <br>  
- **Stateful Pagination** - 페이지 번호를 클릭하거나 검색을 수행할 때, 현재의 검색 타입(type)과 키워드(keyword) 값을 유지하면서 AJAX 통신을 수행합니다 <br>
- **이벤트 위임 기반 렌더링** - `makeView` 함수를 통해 동적으로 생성되는 회원 리스트와 페이지네이션 버튼이 상호작용하며 유연하게 화면을 갱신합니다<br>
- **권한별 시각화** - JavaScript의 `객체 매핑(roleClassMap)`을 활용하여 회원 권한에 따라 각기 다른 배경색을 동적으로 부여합니다 <br>

<p align="center">
  <img  src="https://github.com/user-attachments/assets/7cf759e3-bd42-43b0-9603-e326b1320c0c" width="900" />
</p>
<p align="center">
  <img  src="https://github.com/user-attachments/assets/336e4de2-7521-47c0-9334-4bc6a988e44b" width="900" />
  <br>
  [관리자페이지]
</p>

<br>

## 7. 회원정보수정 
사용자가 본인의 프로필을 관리하고 정보를 최신화할 수 있는 기능을 제공합니다 <br>
Spring Security의 인증 매커니즘을 활용하여 실시간 세션 동기화 하도록 구현하였습니다 <br>

### 1. 세션 실시간 동기화 <br>
- **문제상황** -  DataBase에서 회원 정보를 수정해도 세션 내 `Authentication 객체`는 수정 전 정보를 유지하고 있어 화면에 즉시 반영되지 않는 문제 발생 <br>
- **해결과정** <br>  
1. 현재 세션의 Principal(CustomUser) 객체를 가져와 수정된 데이터를 직접 세팅 → <br>
2. 갱신된 정보를 바탕으로 새로운 `UsernamePasswordAuthenticationToken`을 생성 → <br>
3. SecurityContextHolder에 새 토큰을 꽂아줌으로써 사용자가 재로그인하지 않아도 수정된 정보가 즉시 반영되도록 구현<br>
  <p align="center">
    <img  src="https://github.com/user-attachments/assets/083e0041-adde-4a57-9a45-246c69e1c3eb" width="600" />
  </p>
<br>

### 2. 주요 기능  <br>
- **프로필 이미지 관리** <br>
  - `accept="image/*"` 속성을 통해 이미지 파일만 선택 가능하도록 제한 <br>
  - 파일 선택 여부를 실시간 감지하여 '업로드' 버튼을 활성화/비활성화하는 유효성 검사 적용 <br>
  - '삭제' 버튼 클릭 시 기존 파일을 제거하고 기본 이미지로 복구하는 로직 구현 <br>  
- **비동기 닉네임 중복 체크 (AJAX)** - 현재 사용 중인 닉네임과의 비교 및 DB 중복 조회를 AJAX로 처리하여, 페이지 전환 없이 실시간으로 사용 가능 여부를 확인할 수 있습니다 <br>  
- **데이터 유효성 검사** - 이름, 성별, 이메일 등 필수 입력 항목에 대해 JavaScript에서 공백 및 형식 유효성 검사를 실시하여 비정상적인 데이터 입력을 원천 차단 <br>  

<p align="center">
  <img  src="https://github.com/user-attachments/assets/2be29091-fb95-459f-b482-352f00144f68" width="900" />
  <br>
  [회원정보수정]
</p>

<br>







