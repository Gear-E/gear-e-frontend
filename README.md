# Gear-E Frontend

Gear-E 프론트엔드 저장소입니다. 팀 공용 AI 작업 규칙과 셀프 리뷰 스킬, GitHub 이슈·PR 템플릿을 관리합니다.

## 공용 작업 환경

| 경로 | 용도 |
| --- | --- |
| [AGENTS.md](AGENTS.md) | 프로젝트 운영 규칙 |
| [CLAUDE.md](CLAUDE.md) | `AGENTS.md`를 참조하는 상대 심볼릭 링크 |
| [.agents/skills/self-review/SKILL.md](.agents/skills/self-review/SKILL.md) | Codex 셀프 리뷰 스킬 |
| [.claude/skills/self-review/SKILL.md](.claude/skills/self-review/SKILL.md) | Claude 셀프 리뷰 스킬 |
| [.github/pull_request_template.md](.github/pull_request_template.md) | PR 템플릿 |
| [.github/ISSUE_TEMPLATE/feature_request.md](.github/ISSUE_TEMPLATE/feature_request.md) | 기능·개선 이슈 템플릿 |
| [.github/ISSUE_TEMPLATE/bug_report.md](.github/ISSUE_TEMPLATE/bug_report.md) | 버그 이슈 템플릿 |

## 개발 흐름

일반 작업은 최신 `develop`에서 목적별 작업 브랜치를 만들고, `develop`을 대상으로 Draft PR을 생성합니다.

```text
Issue → 작업 브랜치 → Draft PR → TDD·검증 → Ready for review
      → 셀프 리뷰 → 수정·재검증 → 사용자 병합 → develop
```

- 작업 브랜치는 `feature/*`, `fix/*`, `docs/*`, `chore/*`를 사용합니다.
- 테스트·정적 검사·빌드·필요한 수동 확인 결과를 PR에 기록합니다.
- 관련 이슈는 PR 본문에 `Closes #번호`로 연결합니다.
- 셀프 리뷰 통과 후 사용자에게 검토와 병합을 요청합니다.
- `develop → main` 승격 PR은 정해진 회의 시간에 생성·검토·병합합니다. 통합 검증, 포함 기능, 위험, 롤백 방법을 확인하고 승인 기록을 남깁니다.

상세 절차는 [프로젝트 운영 규칙](AGENTS.md)을 따릅니다.

## 셀프 리뷰 실행

Codex에서는 다음과 같이 실행합니다.

```text
$self-review
$self-review <PR 번호 또는 URL>
$self-review --base main
```

Claude에서는 다음과 같이 실행합니다.

```text
/self-review
/self-review <PR 번호 또는 URL>
/self-review --base main
```

인자가 없으면 현재 브랜치 PR을 찾고, PR이 없으면 `develop` 기준으로 로컬 변경을 검토합니다. `--base main`은 릴리즈 후보의 로컬 검토에 사용합니다.

리뷰 결과는 먼저 초안으로 공유합니다. GitHub 게시와 리뷰 중 발견한 코드 수정은 각각 명시적인 승인을 받은 뒤 진행합니다.

## 실행 및 검증 명령

현재 로컬 구성에는 앱 소스와 패키지 설정이 없어 개발 서버·테스트·빌드 명령이 정의되어 있지 않습니다. 앱 구성이 추가되면 실제 실행 결과를 기준으로 명령을 문서화합니다.
