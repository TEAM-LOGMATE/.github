## 간편한 설치로 이용하는 로그 모니터링 & 분석 서비스 "LogMate" 💻


<img width="1800" height="1000" alt="랜딩페이지 landing" src="https://github.com/user-attachments/assets/7a54e227-cad6-46f4-931d-6dafbd565b2f" />

LogMate는 간단한 설정만으로 이용 가능하며, 누구나 손쉽게 실시간으로 로그를 모니터링하며 AI가 이상 징후까지 감지해주는 SaaS형 올인원 (All-in-one) 플랫폼입니다. 
복잡한 로그 관리, 이제 **LogMate** 로 간단하게 시작해 보세요!

## 👨‍💻 Contributors

| 팀장/ 기획 | 디자인 |Agent |Streaming 서버| API 서버 | AI 서버 | 프론트 | 
|:-------:|:-------:|:-------:|:-------:|:-------:|:-------:|:-------:|
| 강찬욱 | 장연우 | 강찬욱 | 강찬욱 | 정주연 | 양승원 | 양승원 |

## 📚 Documentation
- [SRS (Software Requirements Specification)](./docs/SRS_LogMate.pdf)
- [SDS (Software Design Specification)](./docs/SDS_LogMate.pdf)

## ✅ Background

기존 모니터링 솔루션은 고비용/ 고난이도 인프라 설정을 요구합니다. 이는 중소규모 팀이나 초기 스타트업, 학생 프로젝트 팀에게는 큰 부담으로 다가옵니다.

- 단순한 로그 수집에도 과도한 비용이 강제됩니다. 
- 로그 데이터의 AI 기반 분석 및 이상 징후 감지는 주로 대기업 중심의 기술로 제공되기에, 일반 개발자는 접근에 어려움을 느끼는 경우가 많습니다.
- 기존에 존재하는 여러 오픈소스 기반 로그 솔루션들은 설정이 복잡하며, 개별 기능만 제공되어 사용자가 전체 로그 모니터링을 위해 직접 구성 및 연동해야 하는 파편화된 생태계로 존재합니다.



## As-is

- 복잡한 YAML 설정과 수많은 툴 조합 필요
  
- 로그 스트리밍 + AI 탐지를 동시에 제공하는 통합 솔루션 부재

- 초보 개발자/스타트업이 모니터링 환경을 쉽게 구축하기 어려움

## To-be

- 쉽고 간편한 로그 수집
  - 누구나 손쉽게 설치 후 활용 가능한 오픈소스 로그 모니터링 서비스 제공
    
- 올인원 플랫폼
  - 로그 수집부터 저장, 분석, 시각화, AI 기반 탐지까지 통합하여 제공하는 SaaS 플랫폼
    
- 모듈화 & 오픈소스 공개
  - 누구나 확장하고 기여할 수 있는 지속 가능한 커뮤니티 기반 생태계 조성

## ✨ Key Features

### 실시간 로그 스트리밍
- agent가 수집해 온 로그를 streaming server로 전송
- 로그를 Kafka 에 임시 저장한 뒤, WebSocket을 통해 사용자가 실시간 로그 스트리밍이 가능하도록 함
- 대시보드에서 실시간으로 로그 흐름 확인 가능

### 대시보드 관리
- 사용자가 직접 생성, 조회, 수정 가능하도록 함
- 상태 정보 표시 (로그 수집중 / 에이전트 미응답 / 대시보드 준비중)
- 대시보드 별 파싱 룰, 필터 룰 등록 가능
- Agent 설정 Pulling API를 제공함으로써 Agent가 주기적으로 db에서 최신 설정을 가져가도록 함

### AI 기반 로그 이상 탐지
- Isolation Forest 기반 머신러닝 모델 탑재
- 수신된 로그로부터 다양한 속성을 벡터화하며, 정해진 규약에 따라 Isolation forest 모델의 입력으로 변환
- 모델 출력값을 점수화하여, 점수가 높을수록 비정상 로그로 간주
- IoC 키워드 리스트 기반으로 공격, 위협 징후 강화 탐지

### 외부 연동
- Webhhok URL을 등록하여 비정상 로그 탐지 시 자동 알림 전송 가능

## 🔨Project Architecture
<img width="683" height="458" alt="image" src="https://github.com/user-attachments/assets/ee7ccfc4-a5a2-48cd-bf56-a99dd8c0efaa" />

## Repositories
세부 기술은 각 레포지토리를 참고하세요

### Agent
https://github.com/TEAM-LOGMATE/LOGMATE-AGENT

### Streaming
https://github.com/TEAM-LOGMATE/LOGMATE-STREAMING

### API
https://github.com/TEAM-LOGMATE/LOGMATE-API

### FrontEnd
https://github.com/TEAM-LOGMATE/LOGMATE-FRONT

### AI
https://github.com/TEAM-LOGMATE/LOGMATE-AI

## 🖍️ UX Strategy
화면 설계에 공통적으로 적용된 원칙입니다.

원칙 1. 다크 모드를 기본 지원해야 한다.
- 눈의 피로를 줄이고, 개발자 친화적인 작업 환경을 제공합니다.

원칙 2. 직관적인 대시보드를 지원해야 한다.
- YAML 파일과 같은 설정 파일들을 직접 수정하는 대신, 미리 정의된 선택지와 설명을 UI에서 제공함으로써 누구나 쉽게 설정할 수 있습니다.

원칙 3. 간결하고 직관적인 화면을 구성해야 한다.
- 불필요한 버튼과 복잡한 요소를 최소화하며 핵심 기능을 명확히 사용할 수 있도록 합니다.

  
## 🚀 BI
Logmate는 #간편한 #직관적인 #부담없는 키워드를 중심으로 하여 로그 분석이 필요한 누구든지 사용자가 될 수 있도록 기획 및 개발되었습니다.

### 스타트업, 중소기업 팀
- DevOps 인력 부족 환경에서도 손쉽게 로그 모니터링 환경 구축 가능
- 초기 도입 비용 절감 및 운영 효율성 극대화

### 교육 및 연구
- DevOps, 시스템 운영, 모니터링, AI 이상탐지 등을 교육하는 연구, 실습용 플랫폼으로 활용 가능
- 모든 구성 요소가 모듈화되어 있기에 학습과 실습에 용이함
