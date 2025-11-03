# n8n-workflows

Self-hosted n8n을 활용한 워크플로우 예제 및 템플릿 컬렉션입니다.

## 📋 목차

- [소개](#소개)
- [n8n이란?](#n8n이란)
- [Self-hosted 설정](#self-hosted-설정)
- [워크플로우 카테고리](#워크플로우-카테고리)
- [사용 방법](#사용-방법)

## 소개

이 저장소는 Self-hosted 환경에서 n8n을 사용하여 구현된 다양한 워크플로우 예제들을 모아둔 곳입니다. 모니터링, 자동화, 데이터 처리 등 다양한 사용 사례를 제공합니다.

## n8n이란?

n8n은 오픈소스 워크플로우 자동화 도구로, 다양한 서비스와 API를 연결하여 자동화된 작업 흐름을 만들 수 있습니다. Self-hosted 버전을 사용하면 데이터를 자체 서버에서 완전히 제어할 수 있습니다.

## Self-hosted 설정

### Docker를 사용한 설치

```bash
docker run -it --rm \
  --name n8n \
  -p 5678:5678 \
  -v ~/.n8n:/home/node/.n8n \
  n8nio/n8n
```

### Docker Compose를 사용한 설치

```yaml
version: '3'

services:
  n8n:
    image: n8nio/n8n
    container_name: n8n
    ports:
      - "5678:5678"
    volumes:
      - ~/.n8n:/home/node/.n8n
    environment:
      - N8N_BASIC_AUTH_ACTIVE=true
      - N8N_BASIC_AUTH_USER=admin
      - N8N_BASIC_AUTH_PASSWORD=your_password
```

### 환경 변수

주요 환경 변수 설정 예시:

- `N8N_HOST`: n8n 호스트 주소
- `N8N_PORT`: 포트 번호 (기본값: 5678)
- `N8N_PROTOCOL`: 프로토콜 (http/https)
- `N8N_BASIC_AUTH_ACTIVE`: 기본 인증 활성화
- `N8N_BASIC_AUTH_USER`: 기본 인증 사용자명
- `N8N_BASIC_AUTH_PASSWORD`: 기본 인증 비밀번호

## 워크플로우 카테고리

### 📊 모니터링
- 시스템 리소스 모니터링
- 애플리케이션 로그 추적
- 서비스 상태 확인
- 알림 및 알림 집계

### ⚙️ 자동화
- CI/CD 파이프라인 연동
- 데이터 백업 및 동기화
- 파일 처리 자동화
- 배치 작업 스케줄링

### 🔄 데이터 처리
- 데이터 변환 및 포맷팅
- 데이터베이스 동기화
- API 데이터 수집 및 가공
- 리포트 생성 및 전송

### 📧 알림 및 통신
- 이메일 알림
- Slack/Discord 메시지 전송
- SMS 알림
- 웹훅 처리

### 🔗 서비스 연동
- 클라우드 서비스 연동
- 데이터베이스 연동
- 외부 API 통합
- 웹 서비스 자동화

## 사용 방법

1. **워크플로우 파일 확인**
   - 각 워크플로우는 JSON 형식으로 제공됩니다.
   - 파일명은 워크플로우의 목적을 나타냅니다.

2. **n8n에 가져오기**
   - n8n 웹 인터페이스에 접속합니다.
   - `워크플로우` > `가져오기` 메뉴를 선택합니다.
   - JSON 파일을 업로드하거나 내용을 복사하여 붙여넣습니다.

3. **워크플로우 설정**
   - 각 워크플로우에 필요한 자격증명 및 환경 변수를 설정합니다.
   - 노드별 설정을 확인하고 필요에 따라 수정합니다.

4. **활성화 및 테스트**
   - 워크플로우를 활성화합니다.
   - 테스트 실행을 통해 정상 작동을 확인합니다.

## 요구사항

- n8n (Self-hosted 버전)
- Node.js 18.x 이상 (Docker를 사용하지 않는 경우)
- Docker 및 Docker Compose (권장)

## 보안 고려사항

Self-hosted 환경에서는 다음 사항을 고려하세요:

- 기본 인증 설정 필수
- HTTPS 사용 권장
- 방화벽 규칙 설정
- 정기적인 업데이트
- 민감한 정보 암호화 저장

## 라이선스

이 프로젝트는 MIT 라이선스를 따릅니다.

## 참고 자료

- [n8n 공식 문서](https://docs.n8n.io/)
- [n8n GitHub](https://github.com/n8n-io/n8n)
- [n8n 커뮤니티](https://community.n8n.io/)

## 문의

문제나 제안사항이 있으시면 Issue를 생성해 주세요.
