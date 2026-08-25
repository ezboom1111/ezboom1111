# Lee Jibeom

AI와 LLM을 활용해 **외부 리서치**와 **내부 장기기억**을 연결하는 도구를
설계하고 만드는 데 관심이 있습니다. 외부에서 수집한 근거가 일회성 답변으로
사라지지 않고, 장기기억에 축적되어 다음 조사와 실제 업무에 다시 쓰이는
구조를 탐구합니다.

이 관심사를 프로토타입에만 두지 않고 실제 업무 시스템으로 연결해 왔습니다.
비공개 업체를 위한 통합 운영·매출 시스템, 의료통역·번역 사업 `Aya`,
브라우저 조작 기반 생성형 AI 콘텐츠 파이프라인을 구축했습니다. 상업 프로젝트의
소스 코드와 업무 데이터는 공개하지 않습니다.

개인적으로는 외부 리서치의 추적·검증 인프라와 이를 장기기억으로 연결하는
`Lee Vault`를 함께 개발하고 있습니다.

## Selected systems

| Area | What I built | Status |
| --- | --- | --- |
| Personal research infrastructure | 개인 리서치를 위해 만든 멀티소스 조사 원장 `refcap`과 웹 근거 검증·봉인 서버 Browser-Agent MCP Farm | Public OSS · personal |
| Lee Vault | 외부 근거와 대화에서 나온 결정·정정·결과를 축적하고 다음 AI 작업에 회상시키는 개인 장기기억 시스템 | Private · personal · in progress |
| Private company operations & sales | 동일 비공개 업체의 CRM·ERP·근태·마케팅·지식관리와 3개 POS의 API·수집 데이터를 연결해, 매출 지표→근거→담당 행동으로 이어지는 내부 운영·의사결정 시스템을 구축 | Private company · in operation & ongoing |
| Aya · Interpretation & translation operations | 2025 한양대학교 캠퍼스타운 선정 당시 시작한 사업. 통역·번역 업무의 접수→프리랜서 배치→수행 증거→정산 흐름을 상태 기반으로 관리 | Private startup · ongoing |
| Generative music client delivery | 비공개 업체 외주로 Suno 웹 UI의 반복 작업을 브라우저 조작으로 자동화해 음악 100곡을 생성·전달 | Private client work · delivered |

## Open source · Research infrastructure

| Project | What it does | Verification |
| --- | --- | --- |
| [refcap](https://github.com/ezboom1111/refcap) | 멀티소스 리서치의 출처·미해결 질문·가설·예측을 세션 사이에 이어 주는 Python 증거 원장 | Python 3.9/3.12/3.13 CI, stdlib `unittest` 269개 |
| [Browser-Agent MCP Farm](https://github.com/ezboom1111/browser-agent-mcp-farm) | AI 에이전트가 본 웹 근거를 SHA-256으로 등록하고, 실제 바이트에 없는 인용을 거부하며, Merkle/Ed25519 증거 번들로 전달하는 TypeScript MCP 서버 | Ubuntu/Windows × Node 22/24 CI, 테스트 775개, 패키지·보안 게이트 |

두 공개 프로젝트는 제 개인 리서치에서 먼저 쓰기 위해 만들었습니다. `refcap`은
무엇을 조사했고 무엇이 아직 비어 있는지를 관리하고, Farm은 그중 결론을
지탱하는 핵심 주장만 변조 감지 가능한 증거로 봉인합니다. 검증된 결과는 비공개
장기기억 시스템인 `Lee Vault`의 다음 판단에 활용됩니다. 각 계층은 직접 의존하지
않도록 분리해 독립적으로 교체할 수 있게 설계했습니다.

## Experiments & lessons

- 두 세대의 암호화폐 퀀트 시스템을 개발했습니다. 첫 시스템은 Node.js로
  다중 자산·다중 시간대 기술지표 규칙 엔진을 만들고, Rust 고속 백테스트와
  walk-forward 검증을 거쳐 Python PPO 강화학습·Optuna HPO로 확장했습니다.
  BTC·ETH·SOL·XRP의 가격뿐 아니라 funding, OI, long/short, 청산·거시 데이터를
  수집하고 AWS·GCP에서 학습했습니다. 후속 시스템은 Python `asyncio`·SQLite·
  `ccxt` 기반 비동기 수집, 277차원 feature registry, paper trading, Flask 운영
  대시보드로 다시 설계했습니다. 두 시스템 모두 비용 차감 후 유효한 OOS 알파를
  확인하지 못해 실거래 전에 중단했고, 과적합·데이터 편향·검증 순서 문제를
  사후 분석으로 남겼습니다.
- Vercel에 배포한 마케팅 웹사이트, Leaflet 기반 단일 파일 여행 플래너,
  디자인 시스템을 갖춘 트레이닝 앱 등 여러 웹·UX 프로토타입을 제작했습니다.

## Programs & selections

### Founder / personal

- 2024 · 성균관대학교 캠퍼스타운 선정·입주
- 2025 · `Aya`로 한양대학교 캠퍼스타운 선정·입주
- 2025 · 개인사업 창업자로서 예비창업패키지·신사업창업사관학교 등 사업 서류 선정
- 2026 · 부산대학교 「모두의창업」 1기 선정

### Team contribution

- 2024 · 창업중심대학 선정 프로젝트에 CSO로 참여

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
