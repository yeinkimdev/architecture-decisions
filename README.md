# Architecture Decisions

> 백엔드 시스템을 설계·운영하면서 내린 의사결정의 기록입니다.
> 결정의 결과뿐 아니라 **검토했던 대안과 선택하지 않은 이유**까지 남겨,
> 같은 문제를 만난 다른 분들과 미래의 저에게 도움이 되길 바랍니다.

## 왜 이 저장소를 만들었나

- 시간이 지나면 **"왜 그렇게 결정했는지"** 가 가장 먼저 잊힙니다.
- 코드는 결과만 보여주지만, ADR은 **그 결과에 도달한 사고 과정**을 남깁니다.
- "지금이라면 다르게 결정했을까?"를 정직하게 회고하기 위한 도구입니다.

## 인덱스

| ID | 제목 | Status | Date | Tags |
|---|---|---|---|---|
| [ADR-0001](./adr/0001-사내-공통-스타터-라이브러리-도입.md) | 사내 공통 기능을 Spring Boot Starter 형태의 멀티 모듈 라이브러리로 제공 | Accepted | 2024-XX | `#platform` `#standardization` |
| [ADR-0002](./adr/0002-마이크로서비스-도메인-경계-분리.md) | 단일 Spring 모놀리식을 9개 마이크로서비스로 분리 | Accepted | 2024-XX | `#msa` `#ddd` |
| [ADR-0003](./adr/0003-gateway-jwt-통합-처리.md) | Gateway에서 JWT 인증/인가를 통합 처리 | Superseded by ADR-0005 | 2024-XX | `#security` `#gateway` |
| [ADR-0004](./adr/0004-인증-인가-필터-분리.md) | 인증 필터와 인가 필터를 분리 | Accepted | 2024-XX | `#security` `#gateway` |
| [ADR-0005](./adr/0005-인증을-별도-idp-서비스로-분리.md) | SSO 요구를 위해 인증을 별도 IdP 서비스로 분리 | Accepted | 2025-XX | `#security` `#identity` `#sso` |
| [ADR-0006](./adr/0006-kustomize-argocd-app-of-apps.md) | Kustomize + ArgoCD App-of-Apps GitOps 채택 | Accepted | 2025-XX | `#devops` `#gitops` `#k8s` |
| [ADR-0007](./adr/0007-마스터-코드-캐시-워밍업.md) | 마스터 코드 캐시 워밍업을 별도 빈으로 분리 | Accepted | 2026-05 | `#performance` `#spring` `#cache` |

## 결정 궤적 (시각화)

> 어떤 결정이 어떤 결정으로 이어졌는지

\`\`\`mermaid
graph TD
  ADR3[ADR-0003: Gateway 통합 인증]
  ADR4[ADR-0004: 인증·인가 필터 분리]
  ADR5[ADR-0005: IdP 분리]
  ADR3 -.refined by.-> ADR4
  ADR3 -.superseded by.-> ADR5
  ADR4 -.builds on.-> ADR5
\`\`\`

## 사용한 템플릿
[template.md](./template.md) — MADR-lite 기반

## 표기 규칙
- **Status**: `Proposed` / `Accepted` / `Superseded by ADR-NNNN` / `Deprecated`
- **수정 이력**: 결정이 바뀌면 옛 ADR을 지우지 않고 `Status`만 변경, 새 ADR을 추가합니다.
- 모든 사례는 **회사 식별 정보를 제외한 추상화된 형태**로 정리합니다.
