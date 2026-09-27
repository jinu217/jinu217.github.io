---
title: "Knight Only"
type: project
layout: case-study
lang: ko
slug: knight-only
permalink: /projects/knight-only/
date: 2025-12-01
year: 2025
period: "2025.12–2026.08"
image: "/images/projects/knight-only.png"
thumbnail: "/images/projects/knight-only.png"
cover: "/images/projects/knight-only.png"
cover_alt: "Knight Only의 전투·행동 상태를 보여주는 게임 화면"
thumbnail_alt: "Knight Only 프로젝트 화면"
label: "직접 구현"
role: "4인 팀 · 프로그래머"
technologies: [Unity, C#, New Input System]
code: "https://github.com/jinu217/Knight-Only_Backup"
demo: ""
excerpt: "2D 액션 로그라이크에서 플레이어 행동·전투, 장비, 적·보스 AI와 튜토리얼을 구현했습니다."
resume_line: "Unity·C# / 플레이어 이동·전투, BPM·SP, 장비, 적·보스 AI, 튜토리얼"
---

## 프로젝트와 담당 범위

4인 팀(프로그래머 3명, 디자이너 1명)에서 플레이어 이동과 전투, BPM·SP 상태, 인벤토리·장비, 적·보스 AI, 튜토리얼을 담당했습니다. 아래는 그중 플레이 경험에 직접 영향을 주는 세 가지 구현 사례입니다.

## 행동 상태의 우선순위

대시와 넉백 도중 일반 이동이 속도를 덮어쓰지 않도록 이동 처리 앞에서 상태를 검사했습니다. 대시 중에는 점프 처리도 건너뛰고, 대시가 끝나면 중력 배율과 상태를 복구합니다. 입력과 물리 상태가 서로 다른 경로에서 바뀔 때도 행동의 우선순위가 유지되게 한 선택입니다.

[행동 상태 코드 보기](https://github.com/jinu217/Knight-Only_Backup/blob/34a70f4acfd6de09a10f83f147a3c17d706a0b13/Assets/Scripts/Player/PlayerController.cs#L860)

## 여러 Collider를 가진 대상의 중복 피해 방지

하나의 적이 여러 Collider를 가져도 공격 한 번에 피해가 중복되지 않아야 했습니다. 충돌한 Collider에서 `IDamageable` 대상을 찾고, 그 대상의 ID를 `HashSet`에 기록합니다. 이미 기록된 ID라면 같은 공격 안에서는 피해 처리를 건너뜁니다. 판정의 단위를 Collider가 아니라 피해 대상으로 맞춘 구현입니다.

[공격 판정 코드 보기](https://github.com/jinu217/Knight-Only_Backup/blob/34a70f4acfd6de09a10f83f147a3c17d706a0b13/Assets/Scripts/Player/PlayerController.cs#L1170)

## 장비 변경과 스탯 갱신

장비 변경 시 기본 스탯에서 다시 계산한 값을 플레이어 상태에 반영했습니다. 장비 교체를 여러 번 해도 보너스가 누적되어 값이 틀어지지 않도록 하고, 변경 알림을 UI 갱신과 연결했습니다.

[장비 관리 코드 보기](https://github.com/jinu217/Knight-Only_Backup/blob/34a70f4acfd6de09a10f83f147a3c17d706a0b13/Assets/Scripts/Inventory/EquipmentManager.cs#L139)

### 더 살펴볼 구현

- 적의 탐색·추격·공격 상태와 보스 스킬 실행
- 현재 단계가 맞을 때만 다음으로 넘어가는 튜토리얼 진행
- BPM 단계에 따른 행동 효과와 SP 소비·회복

상세 코드와 화면은 [전체 포트폴리오 PDF]({{ '/files/kim-jinwoo-portfolio.pdf' | relative_url }}) 3–13쪽에 정리했습니다.
