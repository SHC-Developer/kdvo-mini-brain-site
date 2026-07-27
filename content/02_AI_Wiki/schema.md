# Wiki Schema — 페이지 유형·규격

> 위키 페이지 작성 시 이 규격을 따른다. AI 사서 전용 참조 문서.

## frontmatter 표준

```yaml
---
type: entity | concept | sop | summary | claim | comparison | automation | contradiction
created: YYYY-MM-DD
updated: YYYY-MM-DD
source_ids: [RAW-YYYYMMDD-001]
tags: []
status: draft | reviewed | stale
---
```

## 페이지 유형별 규격

### entity (`06_엔티티/`)
- **대상**: 시설물, 발주처, 규제기관, 협회 등 고유 개체
- **필수 섹션**: 개요, 속성(표), 관련 [[링크]], 출처(source_ids)

### concept (`07_개념/`)
- **대상**: 손상메커니즘, 조사·시험 방법, 내구성 등 추상 개념
- **필수 섹션**: 정의, 적용범위, 관련 SOP, 출처

### sop (`03_진단SOP/`)
- **대상**: 현장조사, 정밀안전진단, 보고서 작성 등 절차
- **필수 섹션**: 목적, 선행조건, 단계(번호 목록), 산출물, 주의사항

### summary (`11_요약/`)
- **대상**: Raw 소스 1건당 1 요약
- **필수 섹션**: 원본 ID, 핵심 3~5점, 영향받는 [[페이지]] 목록

### claim (`09_주장·근거/`)
- **대상**: 명시적 주장 + 근거
- **필수 섹션**: 주장, 근거, source_id, 신뢰도(高/中/低)

### comparison (`08_비교·대조/`)
- **대상**: 유형·방법·기준 간 비교
- **필수 섹션**: 비교 대상, 기준, 표

### automation (`04_자동화/`)
- **대상**: 자동화 도구, 스크립트, 워크플로
- **필수 섹션**: 문제, 해결, 스크립트/도구, ROI, 상태(idea/dev/done)

### contradiction (`10_모순·미해결/`)
- **대상**: 페이지 간 충돌, 미해결 질문
- **필수 섹션**:
  ```
  Contradiction severity: soft | scope-mismatch | hard
  Status: Unresolved | Resolved
  ```
- **충돌 주장 A/B**, 관련 [[페이지]], 해결 메모

## wikilink 규칙
- 본문에서 다른 페이지를 언급할 때 반드시 `[[노트명]]` 사용
- 파일명(확장자 제외)과 노트명 일치 권장

## index.md 갱신 규칙
- Ingest / Audit 완료 시 해당 카테고리 섹션에 페이지 추가 또는 한 줄 요약 갱신
- 삭제된 페이지는 index에서도 제거

## log.md 항목 형식

```
## [YYYY-MM-DD] ingest | 원본제목
- source_id: RAW-...
- touched: [[페이지1]], [[페이지2]]
- new_pages: [[신규]]
- contradictions: none
```
