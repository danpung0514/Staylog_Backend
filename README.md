<div align="center">
  <h1>🏠 Staylog</h1>
  <img width="880" height="480" alt="edit_Gemini_Generated_Image_f0wzzrf0wzzrf0wz" src="https://github.com/user-attachments/assets/912266e3-8efc-4adc-b332-b1297d2558ca" /><br/>
  <strong>리뷰형 커뮤니티 기반 숙소 예약 웹 서비스</strong>
  <p>사용자가 여행지와 관련된 리뷰와 정보를 공유하고, 최적의 숙소를 탐색 및 예약할 수 있는 통합 플랫폼입니다.</p>
</div>

## 📌 개요
**"신뢰할 수 있는 리뷰, 실패 없는 여행의 시작: 올인원 숙소 예약 플랫폼”**

![main_page](https://github.com/user-attachments/assets/5fb4c1d0-c329-4726-b989-e99f77df0582)

- **프로젝트 팀 구성**: 9명 (백엔드, 프론트엔드 풀스택 개발자)
- **프로젝트 기간**: 2025.10.13 ~ 2025.11.12
- **주요 링크**: 
  [**Backend**](https://github.com/Acorn-Team-404/Staylog_Backend) | 
  [**FrontEnd**](https://github.com/Acorn-Team-404/Staylog_Frontend) | 
  [**배포 사이트(2026-02-15 배포 중단)**]()

---

## 🏗️ 시스템 아키텍처

Staylog는 **비용 효율성**과 **보안**의 균형을 맞추기 위해 **컨테이너 기반(Container-Native)** 환경과 **EC2 단일 인스턴스** 구조를 채택했습니다.

<img width="880" height="480" alt="edit_Staylog Architecture" src="https://github.com/user-attachments/assets/c799308b-4368-4442-ab0b-7d624daa9e6a" />

- **컨테이너 격리 네트워크 (Docker Network)**: 웹(Nginx), 앱(Spring Boot), 데이터베이스(Oracle)를 내부 사설망(Private Bridge)으로 격리하여, 외부에서의 불필요한 DB 직접 접근을 원천 차단하고 컨테이너 간의 보안 통신을 보장.

- **리버스 프록시 게이트웨이 (Nginx)**: 정적 리소스(React 빌드 파일)는 웹 서버가 직접 처리하여 WAS의 부하를 줄이고, API 요청만 백엔드로 포워딩(Forwarding)하여 단일 진입점 관리 및 CORS 이슈 해결.

- **실전형 결제-예약 동기화 (End-to-End Payment Flow)**: 단순 모의 결제가 아닌 실제 PG사 API를 연동하여, 결제 성공 시에만 예약이 확정되도록 구현함으로써 '결제'와 '데이터 저장' 간의 트랜잭션 정합성을 확보한 실제 서비스 흐름 완성.

- **보안 중심의 직접 배포 전략 (Secure Direct Deployment)**: Public Registry(DockerHub) 사용 시 발생할 수 있는 이미지 유출 보안 위험을 방지하고 불필요한 외부 의존성을 제거하기 위해, 빌드된 아티팩트를 암호화된 채널(SSH)을 통해 운영 서버로 직접 전송하는 파이프라인 구축.

---

## ✨ 핵심 기능

- **원스톱 예약 & 결제 시스템**: 객실 선택부터 **토스(Toss) 페이먼츠** 연동 결제까지 끊김 없는(Seamless) 예약 흐름을 제공하며, 결제 성공 여부에 따른 실시간 예약 확정 로직 구현.

- **고성능 이미지 통합 관리**: 숙소 및 리뷰에 필수적인 이미지를 안정적으로 처리. **비관적 락(Pessimistic Lock)** 기술을 도입해 동시 다발적인 업로드 환경에서도 이미지 순서의 정합성을 완벽하게 보장.

- **위치 기반 스마트 탐색**: **카카오맵 API**를 활용하여 여행지 주변 숙소를 지도 위에서 직관적으로 파악할 수 있는 사용자 친화적 검색 인터페이스.

- **신뢰 기반 리뷰 커뮤니티**: 실제 투숙객만 작성 가능한 클린 리뷰 시스템과 여행의 추억을 기록하는 **저널(Journal) 게시판**. 댓글/대댓글 기능을 통해 호스트와 여행자 간의 활발한 소통 커뮤니티 형성.

- **호스트 전용 통합 대시보드**: 숙소 및 객실의 **등록/수정/삭제** 전 과정을 관리하는 CMS(Content Management System) 구축. 직관적인 예약 현황판을 통해 호스트의 효율적인 운영 및 매출 관리 지원.

- **끊김 없는 반응형 UI/UX**: 데스크탑, 태블릿, 모바일 등 다양한 디바이스 환경에 최적화된 **반응형 웹(Responsive Web)** 구현. 마이페이지를 통해 예약 내역과 개인 정보를 손쉽게 관리.

- **실시간 알림 및 마케팅 엔진**: 신규 회원 대상 환영 **할인 쿠폰** 자동 발급 시스템 구현. 예약 확정/취소 등 주요 상태 변경 시 **실시간 알림**을 전송하여 서비스 재방문율 강화.

---

## 🛠 기술 스택 (Tech Stack)

### 💻 Development
| 카테고리 | 스택 |
| :-- | :-- |
| **Frontend** | <img src="https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=React&logoColor=white"/> <img src="https://img.shields.io/badge/JavaScript%20(ES6)-F7DF1E?style=flat-square&logo=javascript&logoColor=black"> <img src="https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=TypeScript&logoColor=white"/> <img src="https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white"/> <img src="https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white"/> <img src="https://img.shields.io/badge/Axios-5A29E4?style=flat-square"/> <img src="https://img.shields.io/badge/Bootstrap-7952B3?style=flat-square&logo=Bootstrap&logoColor=white"/> |
| **Backend** | <img src="https://img.shields.io/badge/SpringBoot-6DB33F?style=flat-square&logo=SpringBoot&logoColor=white"/> <img src="https://img.shields.io/badge/Java-007396?style=flat-square&logo=Java&logoColor=white"/> <img src="https://img.shields.io/badge/Spring_Security-6DB33F?style=flat-square&logo=SpringSecurity&logoColor=white"/> <img src="https://img.shields.io/badge/JWT-black?style=flat-square&logo=JSONWebTokens&logoColor=white"/> <img src="https://img.shields.io/badge/MyBatis-000000?style=flat-square&logo=MyBatis&logoColor=white"/> |
| **Database** | <img src="https://img.shields.io/badge/Oracle_DB-F80000?style=flat-square&logo=Oracle&logoColor=white"/> |

### 🚀 DevOps & Tools
| 카테고리 | 스택 |
| :-- | :-- |
| **Infrastructure** | <img src="https://img.shields.io/badge/AWS_EC2-FF9900?style=flat-square&logo=AmazonEC2&logoColor=white"/> <img src="https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=Docker&logoColor=white"/> <img src="https://img.shields.io/badge/Nginx-009639?style=flat-square&logo=Nginx&logoColor=white"/> |
| **CI/CD** | <img src="https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=GitHubActions&logoColor=white"/> |
| **Collaboration** | <img src="https://img.shields.io/badge/Git-F05032?style=flat-square&logo=Git&logoColor=white"/> <img src="https://img.shields.io/badge/Notion-000000?style=flat-square&logo=Notion&logoColor=white"/> <img src="https://img.shields.io/badge/Figma-000000?style=flat-square&logo=figma&logoColor=white"/> |

---

## 📊 ERD
<img width="100%" alt="ERD" src="https://github.com/user-attachments/assets/eb41ad02-3615-4a58-918e-74bf235f9cc7" />

---

## 🧑‍💻 주요 기여 파트 (My Contributions)

### **1. 핵심 도메인 설계 및 동시성 제어**

- **숙소/객실 및 미디어 도메인 Full-Stack 개발**: DB 모델링부터 API, UI 구현까지 서비스의 뼈대가 되는 핵심 기능을 전담.
- **동시성 문제 해결**: 다중 이미지 업로드 시 순서가 뒤섞이는 경쟁 상태(Race Condition)를 비관적 락(Pessimistic Lock)과 별도의 카운터 테이블을 도입하여 제어함으로써, 데이터 정합성 보장.

### 2. 대용량 데이터 처리 및 성능 최적화 (Performance Tuning)

**① 에디터 이미지 처리 프로세스 전면 개편 (Base64 → URL-based)**

- **[문제]**: 기존 ToastUI 에디터 사용 시 이미지가 Base64 문자열 형태로 본문에 포함되어, 게시글 하나만 조회해도 DB I/O 부하가 심각하고 데이터 크기가 비대해지는 문제 발생.
- **[해결]**: **Quill 에디터** 도입 및 **이미지를 Pre-upload** 하는 방식으로 전환. 이미지를 서버에 먼저 전송하여 URL을 발급받고 본문에는 `img src` 태그만 저장하는 구조로 개선하여 성능 최적화.

**② 조회 성능 획기적 개선 (N+1 문제 해결)**

- **[성과]**: 숙소 목록 등 대량의 데이터 조회 시 발생하는 **N+1 문제**를 `IN` 절을 활용한 **Batch Loading** 기법으로 해결하여, 쿼리 발생 횟수를 데이터 개수(N)에서 1회로 단축.

**③ 개발 생산성 향상을 위한 범용 'Image Assembler' 개발**

- **[구현]**: Java Generics와 함수형 인터페이스(`BiConsumer`, `Function`)를 활용하여, 특정 도메인에 종속되지 않는 **범용 이미지 주입기(Assembler)** 유틸리티 구현.
- **[협업 기여]**: 타 도메인(리뷰, 이벤트 등) 담당 팀원들이 복잡한 매핑 로직 없이 `assembleImages()` 메서드 호출 한 번으로 API 응답에 이미지를 주입(Injection)할 수 있도록 지원하여 **개발 생산성(DX)** 증대.

### **3. DevOps 및 인프라 구축 (Architecture & Infra)**

- **Docker 기반 격리 네트워크 설계**: Web(Nginx), WAS(Spring), DB(Oracle)를 내부망(Docker Network)으로 격리하여 외부 접근을 차단하고 보안성을 강화한 컨테이너 아키텍처 설계.
- **CI/CD 파이프라인**: **GitHub Actions** 빌드 아티팩트(.tar)를 운영 서버로 직접 전송(SCP)하는 방식을 통해, 외부 레지스트리 비용을 절감하고 보안성을 높인 **최적화된 CI/CD 환경** 구축.

---

## 🔍 상세 구현 내용

### ① 이미지 통합 관리 시스템
- 이미지 등록, 수정, 삭제 기능을 단일 인터페이스에서 처리하며, 사용자가 **노출 순서를 직접 조정**할 수 있는 기능을 구현했습니다.
![edit_image](https://github.com/user-attachments/assets/5f27ae36-5121-4120-ad78-068b9ef14aed)

### ② 텍스트 에디터 최적화 (컴포넌트화)
- **재사용성**: 프로젝트 전반에서 사용 가능한 독립적 에디터 컴포넌트를 구축했습니다.
- **성능 개선**: 대용량 이미지 처리 시 브라우저 부하를 줄이기 위해, 이미지를 서버에 선-업로드 후 반환된 URL을 삽입하는 로직을 적용했습니다.
![new_review](https://github.com/user-attachments/assets/d36a84b6-59aa-4599-91ec-118b122d7b8e)

### ③ 숙소 및 객실 등록/수정 모듈
- 복잡한 등록 폼을 효율적으로 관리하기 위해 텍스트 에디터와 이미지 캐러셀 등록 부분을 별도 컴포넌트로 분리하여 유지보수성을 높였습니다.
![new_room2](https://github.com/user-attachments/assets/33f1f057-9f06-44ee-b4e4-58ceaf7658ca)

---

## 🛠 트러블 슈팅 & 구조 개선

### 🚀 이미지 순서(카운터) 관련 동시성 문제 해결
**1. 문제 상황: `SELECT MAX(...) + 1` 방식의 한계**
- 여러 요청이 동시에 들어올 경우 동일한 `displayOrder`를 조회하여 데이터 정합성이 깨지는 현상 발생.

**2. 해결 전략: 중앙 집중형 카운터 테이블 도입**
- 별도의 `IMAGE_TARGET_COUNTER` 테이블을 두어 순번 관리를 전담시킴.

**3. 로직 진화 과정**
- **비관적 잠금(Pessimistic Locking)**: `SELECT ... FOR UPDATE`를 통해 특정 대상의 카운터 행을 잠가 동시성 문제 완벽 해결.
- **범위 예약(Range Reservation)**: 업로드 개수만큼 번호를 한 번에 선점하여 DB I/O 감소 및 순서 보장.
- **예외 복구**: `DuplicateKeyException` 발생 시 `while` 루프를 통한 재시도 로직으로 레이스 컨디션 방어.

**4. 결론**
- 비관적 잠금과 시퀀스 블록 예약 개념을 결합하여 데이터 정합성과 성능을 모두 확보했습니다.

### 🚀 Image 불러올 때의 N+1 쿼리 문제 개선
**1. 문제 상황**
- 목록 조회 시 각 항목마다 이미지 쿼리가 실행되어 쿼리 횟수가 급증하는 N+1 문제 발생.

**2. 해결 전략: `ImageAssembler`를 통한 배치 로딩(Batch Loading)**
- 서비스 간 결합도를 낮추고 성능을 최적화하기 위해 도입.

**3. 설계 강점**
- **Generic & Functional**: 특정 DTO에 종속되지 않는 제네릭 설계와 Java 함수형 인터페이스 활용으로 높은 재사용성 확보.
- **배치 조회**: `IN` 절을 사용하여 단 한 번의 쿼리로 모든 이미지 데이터를 로딩.

**4. 개선 결과**
- 쿼리 횟수를 `1 + N`에서 `1 + 1`로 고정하여 DB 부하를 획기적으로 최소화했습니다.

---

## 📈 향후 개선 사항
- **고아 이미지 관리**: 에디터 작성 중 중단된 이미지를 처리하기 위해 스케줄러 기반의 자동 삭제 로직 추가 예정.
- **썸네일 최적화**: 미디어 쿼리에 따른 이미지 리사이징 및 썸네일 생성 로직 도입 예정.

---
## 👥 팀원 소개 (Contributors)

| 프로필 | 이름 | GitHub | 담당 파트 |
| :--: | :-- | :--: | :-- |
| <img src="https://github.com/danpung0514.png" width="50"> | **고윤제(팀장)** | [@danpung0514](https://github.com/danpung0514) | Git 전략 수립<br/>CICD 환경 구축<br/>이미지 업로드<br/>객실 등록/수정 |
| <img src="https://github.com/danjae1.png" width="50"> | **임*호(부팀장)** | [@danjae1](https://github.com/danjae1) | 공통코드 테이블 설계<br/>응답 구조 단일화<br/>로그인, 토큰 인증/인가<br/>외부 api 연동 결제 기능, 숙소 검색 기능 |
| <img src="https://github.com/Blossornn.png" width="50"> | **고*석** | [@Blossornn](https://github.com/Blossornn) | 관리자 페이지<br/>예약현황 관리 |
| <img src="https://github.com/Zevvdev.png" width="50"> | **김*은** | [@Zevvdev](https://github.com/Zevvdev) | 리뷰 게시판<br/>저널 게시판 |
| <img src="https://github.com/ryn0604.png" width="50"> | **김*린** | [@ryn0604](https://github.com/ryn0604) | 숙소 상세페이지<br/>예약폼<br/>댓글 및 답글 기능 |
| <img src="https://github.com/Starlights91.png" width="50"> | **오*나** | [@Starlights91](https://github.com/Starlights91) | 마이페이지<br/>반응형 UI/UX |
| <img src="https://github.com/infreeJ.png" width="50"> | **이*혁** | [@infreeJ](https://github.com/infreeJ) | 실시간 알림<br/>할인 쿠폰<br/>회원가입 |
| <img src="https://github.com/izero33.png" width="50"> | **정*영** | [@izero33](https://github.com/izero33) | 객실 상세페이지<br/>카카오 지도 API<br/>예약 캘린더 |
| <img src="https://github.com/cshchun.png" width="50"> | **천*현** | [@cshchun](https://github.com/cshchun) | 관리자 페이지<br/>객실 등록/수정 |

<a href="https://github.com/Acorn-Team-404/Staylog_Backend/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=Acorn-Team-404/Staylog_Backend" />
</a>
