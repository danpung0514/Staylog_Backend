<div align="center">
<h2>Staylog</h2>
리뷰형 커뮤니티 기반 숙소 예약 웹 서비스
</div>

## 📌 개요
![main_page](https://github.com/user-attachments/assets/5fb4c1d0-c329-4726-b989-e99f77df0582)

> 사용자가 여행지와 관련된 리뷰와 정보를 공유할 수 있고 숙소를 탐색하고 예약할 수 있는 리뷰 기반 커뮤니티 웹 서비스 입니다.

- **프로젝트 팀 구성**: 백엔드, 프론트엔드 풀스택 개발자 9명
- **프로젝트 기간**: 2025.10.13 ~ 2025.11.12 (추가 개선 진행중)

## 🔗 링크
- [**Backend Repository**](https://github.com/Acorn-Team-404/Staylog_Backend)
- [**FrontEnd Repository**](https://github.com/Acorn-Team-404/Staylog_Frontend)
- [**배포 링크**](https://staylog.store)

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

## 🧑‍💻 내가 구현한 부분
- **백엔드/프론트엔드 전 과정 개발 담당**

### 1. 이미지 등록/수정 기능

- 이미지 등록, 수정, 삭제를 한 곳에서 처리하며, 사용자가 이미지 노출 순서를 원하는 대로 조정할 수 있도록 구현했습니다.

![edit_image](https://github.com/user-attachments/assets/5f27ae36-5121-4120-ad78-068b9ef14aed)

### 2. 텍스트 에디터 (이미지 삽입 최적화)
- **컴포넌트화**: 재사용 가능한 에디터 컴포넌트 구축.
- **문제 해결**: 기존 Base64 인코딩 방식의 성능 문제를 해결하기 위해, 이미지 업로드 시 서버에 즉시 저장하고 반환된 URL을 삽입하는 방식으로 개선했습니다.

![new_review](https://github.com/user-attachments/assets/d36a84b6-59aa-4599-91ec-118b122d7b8e)

### 3. 숙소 및 객실 등록/수정
- 텍스트 에디터와 대표 이미지 등록(캐러셀) 부분을 독립된 컴포넌트로 분리하여 코드 재사용성을 극대화했습니다.

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
