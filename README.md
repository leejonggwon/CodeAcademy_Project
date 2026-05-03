
# MyBrandName — AI 브랜딩 어시스턴트

MyBrandName은 스타트업이 몇 분 만에 완전한 브랜드 아이덴티티
(로고, 스토리, 마케팅 자료)를 만들 수 있도록 돕는 AI 기반 플랫폼입니다.
d
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
- Coda Academy(코드아케데미)
- Spring Boot Security와 JWT 기반의 RBAC(역할 기반 권한 제어)를 적용한 RESTful 코딩 교육 관리 플랫폼(LMS) <br>

### 프로젝트 개요
- CodeAcademy는 Spring Boot를 기반으로 설계된 차세대 코딩 교육 관리 시스템(LMS)입니다 <br>
- 교육 현장에서 필수적인 역할별 권한 제어와 실시간 소통 기능을 RESTful API 환경에서 구현한 통합 플랫폼입니다 <br>

### 핵심 기술 
- **보안 및 인가 (Security & Auth)** - Spring Boot Security와 JWT를 결합하여 사용자 인증의 보안성을 높였으며, RBAC(Role-Based Access Control)를 통해 관리자, 강사, 수강생 각 역할에 최적화된 메뉴와 기능을 제공합니다 <br>
- **효율적인 데이터 구조 (RESTful API)** - 모든 커뮤니티 기능(게시판, 댓글, 대댓글)을 RESTful API로 설계하여 프론트엔드와의 통신 효율을 극대화하고 데이터 무결성을 확보했습니다 <br>
- **실시간 소통 (Real-time Interaction)** - Native WebSocket을 활용한 그룹별 오픈채팅 기능을 통해 교육생 간의 활발한 피드백과 실시간 질의응답 환경을 구축했습니다 <br>

### 프로젝트기간
- 2026.02 ~ 2026.04 <br>
<br>

## 2. 기술스택 
### 2-1. Backend
- **Framework** - Spring Boot 2.7.3 <br>
- **Security** - Spring Security (Role-based Access Control) <br>
- **Language** - Java 8 (JDK 1.8) <br>
- **Build Tool** - Maven <br>
- **ORM/Data Access** - Spring Data JPA, MyBatis <br>

### 2-2. Database
- **RDBMS** - MySQL <br>
- **Connector** - MySQL Connector Java <br>

### 2-3. Frontend & View
- **View Engine** - JSP (Java Server Pages) <br>
- **Library** - JSTL, Spring Security Taglibs (로그인 세션 정보 표시) <br>
- **Embedded Server** - Tomcat (with Jasper for JSP rendering) <br>

### 2-4. Tools & Utilities
- Lombok <br>
- Spring DevTools <br><br>


## 3. Authentication & Security (Spring Security 스프링보안)
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

#### 2) UerDetailsServiceImpl
- UserDetailsService 인터페이스를 구현 <br>
- memberRepository를 통해 DB에서 username으로 회원 정보를 찾는다 <br>
- **예외처리**  <br>
 사용자가 없을 경우 `UsernameNotFoundException 발생` <br>
 탈퇴한 계정(enabled=false)일 경우 `DisabledException 발생` <br>

#### 3) CustomUser (Security 전용 유저 객체)
- Spring Security의 `User` 클래스를 상속받아 구현한다 <br>
- DB의 Member 엔티티 정보를 Security의 Authentication 객체에 저장하기 위한 어댑터 역할을 한다 <br>
- 사용자의 권한을 `ROLE_ADMIN`, `ROLE_INSTRUCTOR`, `ROLE_STUDENT`와 같은 형태로 변환하여 부여한다 <br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/9e16a972-3d3a-4698-b2d8-2b35d51916e2" width="300" />
</p>

### 3-3. 주요보안 기능 구현 세부사항 

#### 1) 비밀번호 암호화 ((BCrypt)
- 회원가입 시 사용자의 비밀번호를 그대로 저장하지 않고, PasswordEncoder를 사용하여 `해시 암호화`한다 <br>
- **회원가입 컨트롤러** - @Autowired된 PasswordEncoder를 사용하여 가입 로직에서 즉시 암호화 처리한다 <br>
- **로그인 검증** - 사용자가 입력한 평문 비밀번호와 DB에 저장된 암호화된 비밀번호를 Security가 내부적으로 비교하여 인증 수행한다 <br>

#### 2) 권한별 접근 제어 (Authorization)
- 페이지별로 접근할 수 있는 권한을 다르게 설정하여 보안을 강화했습니다 <br>
- **PermitAll** - 메인 페이지 및 회원 관련 기능`(/member/**)`은 비로그인 사용자도 접근 가능 <br>
- **Authenticated** - 게시판 관련 기능`(/board/**)`은 로그인한 인증된 사용자만 접근 가능 <br>

#### 3) 커스텀 유저 디테일 서비스
- 세션에 사용자 정보(이름, 이메일 등)를 효율적으로 보관하기 위해 `CustomUser`를 구현한다 <br>
- `SecurityContextHolder`에 저장된 `CustomUser`를 통해 로그인한 사용자의 정보를 어디서든 편리하게 참조할 수 있다 <br>
- 계정 활성화 여부(Enabled) 체크 로직을 포함하여, 탈퇴하거나 정지된 계정의 로그인을 차단한다 <br>

#### 4) 로그인/회원가입 프로세스 요약
<p align="center">
  <img src="https://github.com/user-attachments/assets/73445c71-e8fa-4752-8464-c2c141d8bc5e" width="500" />
</p>
<br>


## 4. 시스템 아키텍처 (하이브리드 데이터 접근 구조 : JPA + MyBatis)
- **JPA 흐름** - Client → Controller → Service → Repository Interface(JPA) → DB <br>
- **MyBatis 흐름** - Client → Controller → Service → Mapper Interface → Mapper.xml → DB <br>

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




# 주요기능설명 #

## 1. 권한별 기능 제어(Technical Description)
### 1-1. 핵심 기술 구현 요약 <br>
- Spring Security와 JSTL/EL을 활용하여 위와 같은 역할 기반 접근 제어(RBAC) 모델을 설계 <br>
- 사용자 역할(Role)에 따라 시스템 자원(URL, API, 데이터)에 대한 접근 권한을 세밀하게 통제하여 보안성을 강화하였음 <br>
- **데이터 바인딩(EL)** - SecurityContext 내 Principal 객체에 실시간 접근하여 사용자 정보를 효율적으로 참조하였음 <br>
- **조건부 렌더링(JSTL)** - 권한 계층에 따라 메뉴 및 버튼 활성화 여부를 결정하는 태그 기반 로직을 설계하여 코드 가독성과 유지보수성을 확보하였음<br>
<br>

### 1-2. 상세 권한 및 역할 정의 <br>
#### 1) 관리자(ADMIN) <br> 
- 시스템 전반의 제어 및 운영 정책을 총괄하는 최상위 권한 <br>
- **통합 관제** - 전체 게시판(강의, Q&A, 커뮤니티, 강사 전용 커뮤니티 등) 및 게시물에 대한 접근 및 관리 권한을 가집니다. <br>
- **회원 및 과정 관리** - 운영 정책에 따라 관리자 페이지를 통해 관리자를 제외한 회원의 정보 열람이 가능하며, 회원의 권한 등급 및 수강 교육과정을 동적으로 변경할 수 있습니다.<br>
- **콘텐츠 정화** - 부적절한 게시글 및 댓글을 강제 삭제할 수 있으며, 삭제 시 데이터 무결성을 위해 "관리자에 의해 삭제된 게시글/댓글입니다"라는 안내 문구가 표기됩니다. <br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/3a9e9944-c521-45fd-8b01-7021b7700a56" width="900" />
  <br>
  [관리자 계정 - 관리자페이지]
</p>
<br>


#### 2) 운영부(STAFF) <br> 
- 학생 지원 서비스를 담당하는 권한 <br>
- **부서별 역할 수행** - 교육운영, 취업지원, 홍보 등 각 부서의 목적에 맞춰 전체 교육과정의 커뮤니티에 접근하여 공지사항 등록 및 홍보 활동을 수행합니다. <br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/1e5eb11d-0719-4b4a-ab8d-0fdef4587c69" width="900" />
  <br>
  [운영부 계정 - 커뮤니티]
</p>


#### 3) 강사 (INSTRUCTOR) <br> 
- 학습 콘텐츠 생산 및 교육 서비스 제공을 담당하는 교육 권한 <br>
- **과정 중심 접근** - 본인이 배정된 특정 교육과정의 강의, Q&A, 오픈채팅, 커뮤니티 게시판에만 한정적으로 접근하여 보안성을 유지합니다. <br>
- **학습 지원** - 강의 자료 및 수업 내용을 등록하고, 댓글 및 Q&A 답글을 통해 수강생의 학습 질문에 답변합니다.<br>
- **가독성 강화** - 강사가 작성한 게시글 및 답변은 수강생이 쉽게 인지할 수 있도록 강조색으로 차별화되어 표시됩니다. <br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/6cb3b321-4340-406d-a9dd-92476daec6d6" width="900" />
  <br>
  [강사 계정 - 강의 게시글 업로드 및 수정]
</p>


#### 4) 수강생 (STUDENT) <br> 
- 학습 콘텐츠를 소비하고 커뮤니티 활동에 참여하는 핵심 사용자 <br>
- **권한 승인 기반** - 회원가입 후 GUEST 상태에서 관리자의 승인을 거쳐 STUDENT 권한을 획득해야 정식 서비스 이용이 가능합니다. <br>
- **차등적 활동 권한** <br>
    **강의 게시판** - 강의 수강, 수업 자료 다운로드, 댓글 및 좋아요 작성이 가능하지만, 자료의 보호를 위해 게시물 등록, 답글쓰기, 수정, 삭제는 제한됩니다. <br>
    **Q&A 게시판** - 학습 관련 질문 등록이 가능하지만 강사의 전문적인 답변을 보장하기 위해 답글 쓰기 기능은 제한됩니다. <br>
    **커뮤니티** - 회원간 원활한 소통을 위해 모든 게시판 활동(쓰기, 수정, 삭제 등)이 허용됩니다. <br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/1c9bf984-640e-4e68-8439-a546a57e4f14" width="900" />
  <br>
  [수강생 계정 - Q%A 게시글 업로드 및 수정]
</p>
<br>


#### 5) 승인대기 (GUEST) <br> 
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
</p>

<br>

## 3. 파일 다운로드 시스템 <br>
### 3-1. 가상 경로 매핑을 통한 보안 강화 (`WebMvcConfigurer`) <br>
- 서버의 실제 저장 경로를 숨기고 가상 주소를 사용하여 외부의 직접적인 파일 시스템 접근을 차단하여 보안성을 높였습니다 <br>
- `addResourceHandler` : 브라우저의 요청 주소에 따라 서버 내 실제 파일 위치를 찾아 연결해주는 브라우징 구조를 설계했습니다.<br>

### 3-2. 안정적인 전송 환경 (인코딩 및 응답 제어) <br>
- `UriUtils.encode`를 적용해 한글 파일명 깨짐 방지 처리하여 안정적으로 다운로드 가능하게 구현했습니다.<br>
- Content-Disposition: attachment 설정을 통해 브라우저가 파일을 실행(이미지 미리보기 등)하지 않고 즉시 저장하도록 처리했습니다.<br>

### 3-3. 사용자 중심의 파일명 복구 로직 <br>
- 저장 시 사용된 `등호(=)`를 기준으로 문자열을 분리하여, 다운로드 시에는 시스템 식별자를 제외한 순수 원본 파일명만 추출하여 사용자에게 제공합니다.<br>
- 일반적인 언더바(_) 대신 `등호(=)`를 구분자로 사용했습니다. 이는 사용자가 입력한 파일명에 언더바가 포함되어 있을 경우, 실제 파일명과 시스템용 식별자가 혼동되어 데이터가 유실되거나 이름이 잘리는 현상을 방지하기 위한 의도적인 설계입니다.<br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/424a445c-e51d-410d-8171-fd3b362237b8" width="900" />
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












