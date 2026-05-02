
# MyBrandName — AI 브랜딩 어시스턴트

MyBrandName은 스타트업이 몇 분 만에 완전한 브랜드 아이덴티티
(로고, 스토리, 마케팅 자료)를 만들 수 있도록 돕는 AI 기반 플랫폼입니다.

## ✨ 주요 기능

- 🤖 **AI 기반 브랜딩** - OpenAI를 사용해 로고, 브랜드 스토리, 마케팅 자료를 즉시 생성
- 🔐 **인증 시스템** - Supabase 기반의 안전한 로그인 및 회원가입
- 💾 **데이터베이스** - 사용자, 브랜드, 자산, 구독 데이터 저장
- 🎨 **프론트엔드** - TypeScript, Vite, TailwindCSS로 구축된 반응형 UI
- ⚙️ **백엔드 API** - Node.js + Express로 AI 생성, 인증, 데이터 관리 처리
- 💳 **구독 관리** - Stripe 통합으로 플랜 업그레이드 및 결제 처리
- 🔄 **CI/CD** - GitHub Actions를 통한 자동화된 테스트 및 빌드
- 📦 **배포 준비 완료** - Vercel(프론트) + Render(백엔드) + Supabase 통합

## 🛠 기술 스택

| 분야 | 기술 |
|------|------|
| **런타임** | Node.js + Express.js |
| **언어** | TypeScript |
| **프론트엔드** | Vite + Tailwind CSS |
| **데이터베이스 & 인증** | Supabase |
| **AI 서비스** | OpenAI API |
| **CI/CD** | GitHub Actions |
| **호스팅** | Vercel (프론트) + Render (백엔드) |

## 🚀 빠른 시작

### 사전 요구사항

- Node.js 16 이상
- Supabase 프로젝트 (인증, 데이터베이스, 스토리지용)
- OpenAI API 키
- Stripe 계정

### 설치 방법

1. **저장소 클론**
```bash
git clone https://github.com/nuelcas/mybrandname.git
cd mybrandname
```


## 🏗 아키텍처 개요

### 프론트엔드
- TypeScript + Vite + Tailwind CSS로 구축
- Supabase 인증, 백엔드 API (AI 생성), Stripe (결제) 연결

### 백엔드
- Node.js + Express로 구축
- Supabase를 통한 인증, AI 콘텐츠 생성, 데이터베이스 작업 처리

### Supabase 테이블

| 테이블 | 용도 |
|--------|------|
| `users` | 사용자 계정 저장 |
| `brands` | 생성된 브랜드 정보 저장 |
| `assets` | 저장된 이미지/파일 링크 |
| `subscriptions` | 플랜 및 결제 상태 추적 |



## 📡 API 엔드포인트 예제

### 인증 라우트

| 엔드포인트 | 메소드 | 설명 |
|-----------|--------|------|
| `/api/auth/signup` | POST | 신규 사용자 등록 |
| `/api/auth/login` | POST | 사용자 로그인 |

### 브랜딩 라우트

| 엔드포인트 | 메소드 | 설명 |
|-----------|--------|------|
| `/api/brand/logo` | POST | AI 로고 생성 |

#### 요청 예제:
```json
POST /api/brand/logo
{
  "brandName": "NovaTech",
  "industry": "Tech",
  "style": "Modern Minimal"
}
```

## 📜 행동 강령

긍정적이고 포용적인 커뮤니티 유지를 위해 모든 기여자는 다음을 준수해야 합니다:

- ✅ 다른 사람과 상호작용할 때 존중하고 친절하며 인내심 있게 대하기
- ✅ 피드백을 환영하고 건설적인 토론에 참여하기
- ✅ 차별적이거나 공격적인 언어 피하기
- ✅ 비판보다는 협업과 문제 해결에 집중하기
- ❌ 다른 기여자에게 적절히 신용 부여하기

위반 사항이나 우려 사항은 관리자에게 비공개로 보고해 주세요.

## 🚀 배포

| 컴포넌트 | 플랫폼 | 참고사항 |
|---------|--------|---------|
| 프론트엔드 | Vercel/Netlify | 환경 변수 추가 |
| 백엔드 | Render/Railway | Supabase & AI 키 추가 |
| 데이터베이스 | Supabase | Auth + Storage + Database |

<br>
<br>
<br>

## 1. 서비스소개 
### 서비스명
- Spring Boot Security를 이용한 코딩 교육 플랫폼 <br>
- (부제) Spring Boot Security와 JWT를 활용한 RESTful 게시판 API 서비스 <br>

### 서비스설명
- 본 프로젝트는 스프링(Spring) 프레임워크와 MVC 3Tier 아키텍처를 기반으로 한 커뮤니케이션 프로젝트입니다. <br>
- 사용자 간 손쉽게 소통하고, 효율적으로 커뮤니티 기능을 활용할 수 있는 웹 애플리케이션 개발을 목표로 합니다. <br>
- 그룹 채팅, 메시지, 게시글 작성, 좋아요, 댓글·답글, 조회수, 검색, 페이징, 게시글 작성자 프로필, 좌석 발권, 자료 검색, 회원 관리 등의 기능을 제공합니다. <br>
- WebSocket과 비동기 통신(AJAX)을 활용한 실시간 갱신을 구현했습니다. <br>
- Bootstrap 3과 직관적인 JSP 기반 UI를 통해 사용자 친화적인 화면을 구성했습니다. <br>

### 프로젝트기간
- 2026.02 ~ 2026.04 <br>
<br>

## 2. 기술스택 
### 2-1. Backend
- Framework: Spring Boot 2.7.3 <br>
- Security: Spring Security (Role-based Access Control) <br>
- Language: Java 8 (JDK 1.8) <br>
- Build Tool: Maven <br>
- ORM/Data Access: Spring Data JPA, MyBatis <br>

### 2-2. Database
- RDBMS: MySQL <br>
- Connector: MySQL Connector Java <br>

### 2-3. Frontend & View
- View Engine: JSP (Java Server Pages) <br>
- Library: JSTL, Spring Security Taglibs (로그인 세션 정보 표시) <br>
- Embedded Server: Tomcat (with Jasper for JSP rendering) <br>

### 2-4. Tools & Utilities
- Lombok <br>
- Spring DevTools <br><br>


## 3. Authentication & Security (Spring Security 스프링보안)
- 본 프로젝트는 Spring Security를 활용하여 인증 및 인가 시스템을 구축하였음. <br>
- 사용자 데이터는 Spring Data JPA를 통해 관리하고 모든 비밀번호는 보안을 위해 암호화되어 저장됨. <br>


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
- 비밀번호 암호화 : BCrypt 방식 등을 지원하는 DelegatingPasswordEncoder 사용 <br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/3b6063b9-0420-47c4-bfe4-c73486bd603e" width="800" />
</p>

- 권한별 접근 제어 <br>
 `/, /member/**` : 누구나 접근 가능 <br>
 `/board/**` : 로그인한 사용자만 접근 가능 <br>

- 커스텀 로그인/로그아웃 : 우리가 만든 /member/login 폼을 사용하도록 설정 <br>
- CSRF 비활성화 : REST API 및 테스트 편의를 위해 설정 <br>

#### 2) UerDetailsServiceImpl
- UserDetailsService 인터페이스를 구현 <br>
- memberRepository를 통해 DB에서 username으로 회원 정보를 찾는다 <br>
- 예외처리 : <br>
 사용자가 없을 경우 `UsernameNotFoundException 발생` <br>
 탈퇴한 계정(enabled=false)일 경우 `DisabledException 발생` <br>

#### 3) CustomUser (Security 전용 유저 객체)
- Spring Security의 User 클래스를 상속받아 구현 <br>
- DB의 Member 엔티티 정보를 Security의 Authentication 객체에 저장하기 위한 어댑터 역할을 합니다 <br>
- 사용자의 권한을 ROLE_ADMIN, ROLE_INSTRUCTOR, ROLE_STUDENT와 같은 형태로 변환하여 부여한다 <br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/9e16a972-3d3a-4698-b2d8-2b35d51916e2" width="300" />
</p>

### 3-3. 주요보안 기능 구현 세부사항 

#### 1) 비밀번호 암호화 ((BCrypt)
- 회원가입 시 사용자의 비밀번호를 그대로 저장하지 않고, PasswordEncoder를 사용하여 해시 암호함. <br>
- 회원가입 컨트롤러: @Autowired된 PasswordEncoder를 사용하여 가입 로직에서 즉시 암호화 처리. <br>
- 로그인 검증: 사용자가 입력한 평문 비밀번호와 DB에 저장된 암호화된 비밀번호를 Security가 내부적으로 비교하여 인증 수행. <br>

#### 2) 권한별 접근 제어 (Authorization)
- 페이지별로 접근할 수 있는 권한을 다르게 설정하여 보안을 강화했습니다. <br>
- PermitAll: 메인 페이지 및 회원 관련 기능(/member/**)은 비로그인 사용자도 접근 가능. <br>
- Authenticated: 게시판 관련 기능(/board/**)은 로그인한 인증된 사용자만 접근 가능. <br>

#### 3) 커스텀 유저 디테일 서비스
- 세션에 사용자 정보(이름, 이메일 등)를 효율적으로 보관하기 위해 CustomUser를 구현 <br>
- SecurityContextHolder에 저장된 CustomUser를 통해 로그인한 사용자의 정보를 어디서든 편리하게 참조할 수 있습니다. <br>
- 계정 활성화 여부(Enabled) 체크 로직을 포함하여, 탈퇴하거나 정지된 계정의 로그인을 차단합니다. <br>

#### 4) 로그인/회원가입 프로세스 요약
<p align="center">
  <img src="https://github.com/user-attachments/assets/73445c71-e8fa-4752-8464-c2c141d8bc5e" width="500" />
</p>
<br>


## 4. 시스템 아키텍처 (하이브리드 데이터 접근 구조 : JPA + MyBatis)
- JPA 흐름 : Client → Controller → Service → Repository Interface(JPA) → DB <br>
- MyBatis 흐름 : Client → Controller → Service → Mapper Interface → Mapper.xml → DB <br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/e8366817-ec03-4683-8404-595ad5d63551" width="600" />
</p>

## 5. DataBase E-R Diagram
<p align="center">
  <img src="https://github.com/user-attachments/assets/6bc555a7-54d4-4f2f-a2b4-e19410141885" width="800" />
</p>
<br>

## 6. 서비스 흐름도
<p align="center">
  <img src="https://github.com/user-attachments/assets/0bfa8858-1c77-43ee-8fba-4231de1a9fe5" width="500" />
</p>


## 7. 주요기능설명

### 7-1. 권한별 기능 제어(Technical Description)
#### 1) 핵심 기술 구현 요약 <br>
- Spring Security와 JSTL/EL을 활용하여 위와 같은 역할 기반 접근 제어(RBAC) 모델을 설계 <br>
- 사용자 역할(Role)에 따라 시스템 자원(URL, API, 데이터)에 대한 접근 권한을 세밀하게 통제하여 보안성을 강화하였음 <br>
- 데이터 바인딩(EL) : SecurityContext 내 Principal 객체에 실시간 접근하여 사용자 정보를 효율적으로 참조하였음 <br>
- 조건부 렌더링(JSTL) : 권한 계층에 따라 메뉴 및 버튼 활성화 여부를 결정하는 태그 기반 로직을 설계하여 코드 가독성과 유지보수성을 확보하였음<br>

#### 2) 상세 권한 및 역할 정의 <br>
#### 2)-1. 관리자(ADMIN) <br> 
- 시스템 전반의 제어 및 운영 정책을 총괄하는 최상위 권한 <br>
- 통합 관제 : 전체 게시판(강의, Q&A, 커뮤니티, 강사 전용 커뮤니티 등) 및 게시물에 대한 접근 및 관리 권한을 가집니다. <br>
- 회원 및 과정 관리 : 운영 정책에 따라 관리자 페이지를 통해 관리자를 제외한 회원의 정보 열람이 가능하며, 회원의 권한 등급 및 수강 교육과정을 동적으로 변경할 수 있습니다.<br>
- 콘텐츠 정화 : 부적절한 게시글 및 댓글을 강제 삭제할 수 있으며, 삭제 시 데이터 무결성을 위해 "관리자에 의해 삭제된 게시글/댓글입니다"라는 안내 문구가 표기됩니다. <br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/4ea3c6e2-8f6d-4511-ba7f-9a560d89c2fc" width="900" />
</p>


#### 2)-2. 운영부(STAFF) <br> 
- 학생 지원 서비스를 담당하는 권한 <br>
- 부서별 역할 수행 : 교육운영, 취업지원, 홍보 등 각 부서의 목적에 맞춰 전체 교육과정의 커뮤니티에 접근하여 공지사항 등록 및 홍보 활동을 수행합니다. <br>

#### 2)-3. 강사 (INSTRUCTOR) <br> 
- 학습 콘텐츠 생산 및 교육 서비스 제공을 담당하는 교육 권한 <br>
- 과정 중심 접근 : 본인이 배정된 특정 교육과정의 강의, Q&A, 오픈채팅, 커뮤니티 게시판에만 한정적으로 접근하여 보안성을 유지합니다. <br>
- 학습 지원 : 강의 자료 및 수업 내용을 등록하고, 댓글 및 Q&A 답글을 통해 수강생의 학습 질문에 답변합니다.<br>
- 가독성 강화 : 강사가 작성한 게시글 및 답변은 수강생이 쉽게 인지할 수 있도록 강조색으로 차별화되어 표시됩니다. <br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/f845fdf5-53f5-431d-bd83-bb249d231234" width="900" />
</p>


#### 2)-4. 수강생 (STUDENT) <br> 
▪ 학습 콘텐츠를 소비하고 커뮤니티 활동에 참여하는 핵심 사용자 <br>
▪ 권한 승인 기반 : 회원가입 후 GUEST 상태에서 관리자의 승인을 거쳐 STUDENT 권한을 획득해야 정식 서비스 이용이 가능합니다. <br>
▪ 차등적 활동 권한 <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ▪ 강의 게시판 : 강의 수강, 수업 자료 다운로드, 댓글 및 좋아요 작성이 가능하지만, 자료의 보호를 위해 게시물 등록, 답글쓰기, 수정, 삭제는 제한됩니다. <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ▪ Q&A 게시판 : 학습 관련 질문 등록이 가능하지만 강사의 전문적인 답변을 보장하기 위해 답글 쓰기 기능은 제한됩니다. <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ▪ 커뮤니티 : 회원간 원활한 소통을 위해 모든 게시판 활동(쓰기, 수정, 삭제 등)이 허용됩니다. <br>

#### 2)-5. 승인대기 (GUEST) <br> 
- 회원가입은 완료했으나 서비스 이용 권한을 대기 중인 상태 <br>
- 접근 제한 : 관리자가 사용자 정보를 확인하여 수강생 또는 강사로 권한을 부여하기 전까지는 서비스 이용이 제한되는 준회원 상태 <br>

#### 2)-6. 이용제한 (PENALTY) <br> 
- 운영 정책 위반으로 인해 서비스 이용이 정지된 상태 <br>
- 이용 제한: 관리자에 의해 지정되며, 로그인은 가능하나 게시물 작성 및 조회 등 핵심 서비스 이용이 차단된 상태 <br>

<br>

### 7-2.다중 파일업로드 및 서버 저장 시스템 <br>
#### 1) 핵심 기술 구현 요약 <br>
- 게시글 작성 시 사용자가 첨부한 여러 개의 미디어 파일(이미지, 문서 등)을 서버 로컬 파일 시스템에 안전하게 저장하고, 이를 DB와 매핑하여 관리하는 기능을 구현했습니다<br>
- `MultipartFile` 인터페이스를 사용하여 클라이언트로부터 전송된 데이터를 효율적으로 수신 및 처리합니다.<br>
- 동일한 파일명 업로드 시 데이터 덮어쓰기를 방지하기 위해 `System.currentTimeMillis()`를 활용하여 파일의 고유성을 확보하였습니다.<br>
- `File.mkdirs()`를 활용해 물리적 저장 경로가 존재하지 않을 경우 서버가 자동으로 디렉토리를 생성하도록 설계하여 운영 안정성을 높였습니다<br>
- 서버 부하를 줄이기 위해 파일 본체는 로컬 스토리지에 저장하고, 데이터베이스에는 파일명 및 경로 정보만을 저장하는 표준화된 업로드 아키텍처를 따랐습니다<br>

#### 2) 게시판별 맞춤형 파일 필터링 <br>
- 사용자가 파일 선택 단계에서부터 게시판 목적에 맞는 형식만 선택할 수 있도록 HTML5의 accept 속성을 활용하여 프론트엔드 제어 및 UX를 개선했습니다.<br>
- 강의 게시판 (`accept="video/*"`): 학습 콘텐츠의 일관성을 위해 동영상 파일만 업로드 가능하도록 제한하여 강의 중심의 게시판 성격을 강화했습니다.<br>
- Q&A 게시판 (`accept="image/*"`): 코드 오류나 실행 화면 스크린샷 등 텍스트로 설명하기 어려운 상황을 시각적으로 공유할 수 있도록 이미지 파일만 허용하여 원활한 소통을 유도했습니다.<br>


### 7-3.파일 다운로드 시스템 <br>
#### 1)가상 경로 매핑을 통한 보안 강화 (`WebMvcConfigurer`) <br>
- 서버의 실제 저장 경로를 숨기고 가상 주소를 사용하여 외부의 직접적인 파일 시스템 접근을 차단하여 보안성을 높였습니다 <br>
- `addResourceHandler` : 브라우저의 요청 주소에 따라 서버 내 실제 파일 위치를 찾아 연결해주는 브라우징 구조를 설계했습니다.<br>

#### 2) 안정적인 전송 환경 (인코딩 및 응답 제어) <br>
- `UriUtils.encode`를 적용해 한글 파일명 깨짐 방지 처리하여 안정적으로 다운로드 가능하게 구현했습니다.<br>
- Content-Disposition: attachment 설정을 통해 브라우저가 파일을 실행(이미지 미리보기 등)하지 않고 즉시 저장하도록 처리했습니다.<br>

#### 3) 사용자 중심의 파일명 복구 로직 <br>
- 저장 시 사용된 `등호(=)`를 기준으로 문자열을 분리하여, 다운로드 시에는 시스템 식별자를 제외한 순수 원본 파일명만 추출하여 사용자에게 제공합니다.<br>
- 일반적인 언더바(_) 대신 `등호(=)`를 구분자로 사용했습니다. 이는 사용자가 입력한 파일명에 언더바가 포함되어 있을 경우, 실제 파일명과 시스템용 식별자가 혼동되어 데이터가 유실되거나 이름이 잘리는 현상을 방지하기 위한 의도적인 설계입니다.<br>

### 7-4. 댓글 및 대댓글(답글) 기능 <br>
#### 1) 주요 특징 (Key Features) <br>
- **비동기 처리 (AJAX)** - 페이지 새로고침 없이 댓글 등록, 삭제, 대댓글 조회가 가능한 UX를 제공 <br>
- **계층형 데이터 구조** - `GROUP`, `SEQUENCE`, `LEVEL` 컬럼을 사용하여 원본 댓글과 대댓글 간의 부모-자식 관계를 논리적으로 구현 <br>
- **보안 및 권한 제어** - 작성자 본인 또는 관리자(ADMIN) 계정만 삭제가 가능하도록 프론트엔드와 백엔드에서 2중으로 검증<br>
- **상태 유지 삭제** - 데이터를 실제로 DB에서 지우지 않고 AVAILABLE 상태값을 변경하여 "삭제된 댓글입니다"라는 메시지를 남기는 방식<br>
`AVAILABLE == 'ADMIN'` : "관리자에 의해 삭제된 댓글입니다." 메시지 출력 <br>
`AVAILABLE == '0'` : "작성자에 의해 삭제된 댓글입니다." 메시지 출력 <br>

#### 2) DB 설계 및 로직 <br>
- 계층형 구조를 구현하기 위해 `selectKey` 로직을 사용<br>
- **댓글 그룹화 (`GROUP`)** - 원본 댓글과 그에 달린 대댓글을 하나의 그룹으로 묶습니다. <br>
- **정렬 순서 (`SEQUENCE`)** - 그룹 내에서 댓글이 보여지는 순서를 결정합니다. 새 대댓글이 중간에 삽입될 경우 기존 순서를 +1 UPDATE 하여 순서를 유지합니다.<br>
- **계층 깊이 (`LEVEL`)** - 원본 댓글은 0, 대댓글은 1로 구분 했습니다.<br>

#### 3) MyBatis를 활용한 계층 구조 생성 <br>
- 원본 댓글 등록 시 MAX(CMT_IDX)를 조회해 다음 그룹 번호를 자동으로 할당합니다.<br>
<p align="center">
  <img src=src="https://github.com/user-attachments/assets/8b04e7fd-6002-4e82-8649-bd7be7884930" width="900" />
</p>













