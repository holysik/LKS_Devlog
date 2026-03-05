# 🧠 Devlog — My Contribution Portfolio

> 더 나은 시스템을 향해 도전하며, 끊임없이 성장을 추구하는 개발자 이규식입니다.

---

## 🔎 Project Overview

**Devlog**는 개발자들이 기술 기록과 성장 이야기를 함께 나누는 커뮤니티 플랫폼입니다.  
본 저장소는 팀 프로젝트 Devlog에서 **제가 직접 설계·구현한 영역과 문제 해결 과정**을 정리한  
개인 포트폴리오 문서 저장소입니다.

- 🧑‍💻 Role: FullStack Developer
- 🗓 Period: 2025.12.01 – 2026.01.09
- 👥 Team: 5 members
- 🔗 Team Repository: [Devlog Team_Repo](https://github.com/Team-ZeroBoost/Devlog)

---


## 🧑‍💻 My Role & Responsibility

## 👑 주요 기여

### 💬 실시간 채팅 아키텍처 설계
- 실시간 채팅 서버 아키텍처 설계 및 구현  
- WebSocket / STOMP 메시지 흐름 설계  
- 채팅 읽음 처리 및 동시 접속자 동기화 로직 구현  
- 동시성 제어 기반 채팅방 상태 실시간 갱신 구조 설계  
- 메시지 검색 및 검색 결과 즉시 이동 구조 설계  

### 🔔 이벤트 기반 알림 처리 구조 설계
- 팔로우·댓글·좋아요·멘션 이벤트 통합 알림 처리 구조 설계  
- 알림 조회·정렬·유형 분리 데이터 모델링 및 API 설계  
- 알림 클릭 시 대상 페이지 이동 라우팅 구조 설계  

### 🧬 사용자 성장 로직 설계
- EXP·레벨·포인트 데이터 모델링 및 자동 레벨업 로직 설계  
- 주간 활동 리포트 / 인기글 / IT 뉴스 배치 발송 구조 설계  

### 🗄 데이터 접근 및 트랜잭션 전략
- Oracle 기반 DB 구조 설계 
- JPA + MyBatis 혼합 운용 구조 설계  

---


## 🧪 문제 해결

### 💥 Case: 읽음 상태 정합성 및 동시성 문제

#### 🧩 Problem
다수 사용자가 동시에 채팅방에 입장·퇴장하거나 메시지를 읽는 상황에서  
읽음 카운트가 실제 상태와 일치하지 않는 문제가 발생했습니다.  

#### 🔎 Cause
- 읽음 카운트를 "현재 접속자 수"와 같은 순간 상태에 의존해 계산  
- 입장·퇴장·읽음 이벤트가 서로 다른 흐름에서 처리되며 상태 불일치 발생  
- 메모리 기반 접속자 정보와 DB 상태 간 정합성 유지 기준이 명확하지 않음  
  
#### 🛠 Solution
- 읽음 상태 기준을 접속자 수가 아닌,  
  사용자별 `lastReadMessage` 기준점으로 재설계  
- 해당 기준 이후의 메시지에 대해서만 미확인 수를 계산하도록 로직 변경  
- 읽음 처리 흐름을 단일 기준(서버 상태)으로 통합해 정합성 확보  

#### ✅ Result
- 동시 접속 및 입·퇴장 상황에서도 읽음 카운트가 정확히 유지  
- 접속자 수 변화와 무관하게 사용자별 읽음 상태 일관성 확보  
- 읽음 처리 로직이 단순화되어 유지보수성과 확장성 개선   


---

## 📸 주요 기능 화면
- 채팅 
 <img width="500" height="300" alt="{49078D6B-1A5B-4A37-A5F4-F6A343E39BD9}" src="https://github.com/user-attachments/assets/eff5ea18-bd81-4908-b079-de5420e3ef83" />

- 알림
 <img width="458" height="535" alt="{9AFFE007-C31C-471D-BF35-3D587999DE7D}" src="https://github.com/user-attachments/assets/d84a7ae6-12d2-47fe-a4e6-2c921abb7f91" />

- 메일 발송
 <img width="500" height="300" alt="{5C36BD5C-4AB0-4870-9E99-7D350869A9B3}" src="https://github.com/user-attachments/assets/ffe2c348-8904-4c26-96ac-022e67b044ac" />


---



## 🚀 What I Learned

- **실시간 시스템 설계 경험**  
  WebSocket / STOMP 기반 메시지 흐름을 설계하고 구현하며  
  실시간 이벤트 처리와 상태 동기화 구조에 대한 이해를 높였습니다.

- **서비스 흐름을 고려한 백엔드 설계 관점**  
  개별 기능 구현에 머무르지 않고  
  채팅, 알림, 사용자 활동 데이터가 서비스 전체 흐름 속에서  
  어떻게 연결되고 동작하는지 구조적으로 고민하는 경험을 했습니다.

---

## 📬 Contact

- Email: holysik.dev@gmail.com

