# Portfolio Mirror Trading System

SEC 13F 공시 기반으로 글로벌 투자 거장의
포트폴리오를 자동 수집·분석·미러링하는 시스템

## 미러링 대상
- 워렌 버핏 (버크셔 해서웨이)
- 레이 달리오 (브리지워터 어소시에이츠)

## 시스템 아키텍처
\`\`\`
SEC EDGAR API (분기별 13F 공시)
    ↓
Python 데이터 수집 (sec_13f_fetcher.py)
    ↓
Google Drive 저장
    ↓
n8n 워크플로우
  ├── 포트폴리오 변경사항 감지
  ├── 비중 변화 분석
  └── PostgreSQL 이력 저장
    ↓
Slack 알림 (변경 종목 리포트)
\`\`\`

## 기술 스택
| 분류 | 기술 |
|------|------|
| 데이터 수집 | Python, SEC EDGAR API |
| 워크플로우 | n8n |
| 저장소 | PostgreSQL + pgvector |
| 인프라 | Docker, Oracle Cloud A1.Flex |
| 알림 | Slack API |

## 주요 기능
- SEC 13F 공시 자동 수집 (분기별)
- 포트폴리오 변경사항 자동 감지
  (신규 편입 / 비중 확대 / 비중 축소 / 청산)
- 변경 이력 PostgreSQL 저장
- Slack 실시간 알림

## 실행 결과
[슬랙 알림 스크린샷]

## 로컬 실행
\`\`\`bash
git clone https://github.com/dlrnjsrl89-cmyk/portfolio-mirror-trading
cd portfolio-mirror-trading
pip install -r requirements.txt
python collector/sec_13f_fetcher.py
\`\`\`
