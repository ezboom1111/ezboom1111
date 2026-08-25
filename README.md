# Lee Jibeom

AI와 LLM을 활용해 **외부 리서치**와 **내부 장기기억**을 연결하는 도구를
설계하고 만드는 데 관심이 있습니다. 외부에서 수집한 근거가 일회성 답변으로
사라지지 않고, 장기기억에 축적되어 다음 조사와 실제 업무에 다시 쓰이는
구조를 탐구합니다.

이 관심사를 프로토타입에만 두지 않고 실제 업무 시스템으로 연결해 왔습니다.
회사 운영을 위한 CRM·ERP 플랫폼과 매출 데이터 제품, 프리랜서 비대면 업무
배치 서비스, 브라우저 조작 기반 생성형 AI 콘텐츠 파이프라인을 구축했습니다.
상업 프로젝트의 소스 코드와 업무 데이터는 공개하지 않습니다.

공개 저장소에서는 그중 외부 리서치의 추적 가능성과 검증 가능성을 다룹니다.
내부 장기기억 시스템은 현재 비공개로 개발하고 있습니다.

## Selected systems

| Area | What I built | Status |
| --- | --- | --- |
| AI research infrastructure | 멀티소스 조사 원장 `refcap`과 웹 근거 검증·봉인 서버 Browser-Agent MCP Farm | Public OSS |
| Agent long-term memory | 대화에서 근거·결정·정정·결과를 축적하고 다음 작업에 회상시키는 개인 장기기억 시스템 | Private · in progress |
| Business operations | CRM·ERP·근태·마케팅·지식관리·매출 흐름을 연결한 사내 운영 플랫폼 | Private · internal beta |
| Sales intelligence | 서로 다른 3개 POS 데이터를 통합해 지표·근거·담당 행동을 연결한 운영 대시보드 | Private · in operation |
| Remote workforce operations | 프리랜서 업무 접수→배치→수행 증거→정산 흐름을 상태 기반으로 관리하는 운영 콘솔 | Private · closed product |
| Generative music delivery | Suno 웹 UI의 반복 작업을 브라우저 조작으로 자동화해 음악 100곡을 생성·전달 | Private · delivered |

## Open source · Research infrastructure

| Project | What it does | Verification |
| --- | --- | --- |
| [refcap](https://github.com/ezboom1111/refcap) | 멀티소스 리서치의 출처·미해결 질문·가설·예측을 세션 사이에 이어 주는 Python 증거 원장 | Python 3.9/3.12/3.13 CI, stdlib `unittest` 269개 |
| [Browser-Agent MCP Farm](https://github.com/ezboom1111/browser-agent-mcp-farm) | AI 에이전트가 본 웹 근거를 SHA-256으로 등록하고, 실제 바이트에 없는 인용을 거부하며, Merkle/Ed25519 증거 번들로 전달하는 TypeScript MCP 서버 | Ubuntu/Windows × Node 22/24 CI, 테스트 775개, 패키지·보안 게이트 |

`refcap`은 무엇을 조사했고 무엇이 아직 비어 있는지를 관리합니다. Farm은 그중
결론을 지탱하는 핵심 주장만 변조 감지 가능한 증거로 봉인합니다. 두 프로젝트는
직접 의존하지 않도록 분리해 수집·판단 계층과 검증 계층을 독립적으로 교체할
수 있게 설계했습니다.

## Experiments & lessons

- Node.js 규칙 엔진에서 Rust 백테스트 엔진과 Python PPO·Optuna 파이프라인까지
  두 세대의 암호화폐 퀀트 시스템을 만들었습니다. 비용 차감 후 유효한 알파를
  확인하지 못해 실거래 전에 중단했고, 실패 원인과 검증 순서의 문제를 기록했습니다.
- Vercel에 배포한 마케팅 웹사이트, Leaflet 기반 단일 파일 여행 플래너,
  디자인 시스템을 갖춘 트레이닝 앱 등 여러 웹·UX 프로토타입을 제작했습니다.

## Programs & selections

### Founder / personal

- 2024 · 성균관대학교 캠퍼스타운 선정·입주
- 2025 · 한양대학교 캠퍼스타운 선정·입주
- 2026 · 부산대학교 「모두의창업」 1기 선정

### Team contribution

- 2024 · 창업중심대학 선정 프로젝트에 CSO로 참여
- 2025 · 예비창업패키지·신사업창업사관학교 등 사업 서류 선정에 CSO·팀원으로 기여

## Core stack

- Primary: Python, TypeScript, JavaScript, SQL
- Web & data: Next.js, React, Vite, Express, Streamlit, Supabase/Postgres, SQLite
- AI & automation: LLM agents, RAG/retrieval, MCP, Playwright/browser automation
- Engineering: GitHub Actions, CI, testing, security and evidence gates
- Additional project experience: Rust, reinforcement learning, Optuna

## How I build

- 먼저 실패 조건과 성공 기준을 적고, 테스트와 CI로 재현합니다.
- 외부 페이지와 모델 출력은 지시가 아니라 검증할 데이터로 취급합니다.
- 로그인·CAPTCHA·결제 우회처럼 넘지 않을 경계는 문서뿐 아니라 코드에 둡니다.
- 과장된 기능 설명을 발견하면 숨기지 않고 문서와 구현을 함께 정정합니다.

현재 관심사는 RAG와 에이전트 orchestration을 “데모가 돌아가는가”보다
“근거·실패·인수인계를 다른 사람이 다시 검증할 수 있는가”의 관점에서
설계하는 것입니다.
