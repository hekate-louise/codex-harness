# Codex 작업 하네스

Codex CLI로 제한 시간 안에 업무 문제를 정의하고 결과물을 만들 때 쓰는 작업 원칙, 기록 템플릿, 스킬 모음.

## 구성
| 경로 | 역할 |
|---|---|
| `AGENTS.md` | Codex가 매번 읽는 작업 원칙: 계획 → 승인 → 구현, 직접 실행해 검증, 독립 확인, 기록, git 커밋 |
| `templates/REQUIREMENTS.md` | 문제 정의, 사용자 환경, 입력·출력, 우선순위, 인터뷰 기록 틀 |
| `templates/DECISIONS.md` | 결정 / 이유 / 버린 대안 / 한계 / 검증 기록 틀 |
| `skills/` | Codex 스킬. 설치하면 작업 폴더의 `.agents/skills/`로 복사된다 |
| `install.sh` | 작업 폴더에 설치. 이미 있는 파일은 덮어쓰지 않는다 |

## 설치
```bash
git clone https://github.com/<계정>/<저장소> /tmp/h
bash /tmp/h/install.sh .
```
설치한 뒤 Codex를 다시 시작한다. Codex 샌드박스는 `.agents` 폴더에 쓰지 못할 수 있으므로 설치는 셸에서 직접 실행한다.

## 스킬
`$이름`으로 부른다. 직접 부를 때만 동작하도록 설정한 스킬은 Codex의 자동 목록에 나오지 않을 수 있다.

| 스킬 | 호출 | 하는 일 |
|---|---|---|
| `env` | 직접 | 개발 환경 점검. 사용자 환경 질문 목록 |
| `kickoff` | 직접 | 과제 README 분석, 업무 담당자 질문 목록, REQUIREMENTS 초안 |
| `interview` | 직접 | `check`: 보내기 전 질문 점검 / `record`: 받은 답을 REQUIREMENTS에 기록 |
| `plan` | 직접 | 구현 계획. 완료 기준 명령은 미리 실행. 승인 후 PLAN.md에 저장 |
| `decide` | 직접 | DECISIONS.md에 결정 기록 |
| `verify` | 직접 | 실행·테스트, 구현과 독립된 확인, 테스트가 틀린 코드를 잡는지 확인, 수동 체크리스트 |
| `wrap` | 직접 | 제출 전 최종 점검과 결과 공유 메시지 |
| `explain` | 직접 | 구조·규칙·검증·한계 정리. 예상 질문은 질문만 내고 답은 사용자가 쓴다 |
| `handoff` | 직접 | 대화를 `docs/handoff-NN.md`로 정리해 다음 세션에 넘김 |
| `grilling` | 자동 | 계획·결정의 허점을 질문으로 점검 |
| `diagnosing-bugs` | 자동 | 막힌 버그를 재현 루프 → 가설 → 검증 순서로 진단 |
| `frontend-design` | 자동 | 화면 디자인 방향 |

## 출처와 라이선스
- `handoff`(수정본), `grilling`, `diagnosing-bugs`: [mattpocock/skills](https://github.com/mattpocock/skills), MIT. 각 폴더에 원본 LICENSE 포함. `handoff`는 저장 위치와 기록 규칙을 이 하네스에 맞게 고쳤다.
- `frontend-design`: [anthropics/skills](https://github.com/anthropics/skills), Apache 2.0. 폴더에 원본 LICENSE.txt 포함.
- 그 밖의 파일은 이 저장소에서 작성했다.
