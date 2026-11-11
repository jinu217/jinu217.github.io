---
title: "Knight Only"
type: project
layout: case-study
lang: ko
slug: knight-only
permalink: /projects/knight-only/
date: 2025-12-01
year: 2025
period: "2025.12–진행 중"
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
excerpt: "2D 액션 로그라이크 졸업작품에서 플레이어 행동·전투, BPM·SP, 적·보스 AI, 씬 전환과 튜토리얼을 구현하고 있습니다."
resume_line: "Unity·C# / 플레이어 이동·전투, BPM·SP, 적·보스 AI(Stage 1~5), 씬 전환, 튜토리얼"
---

## 프로젝트와 담당 범위

4인 팀(프로그래머 3명, 디자이너 1명)의 졸업작품입니다. 2025년 12월에 기획을 시작해 2026년 4월 말부터 개발했고, 지금도 진행 중입니다. 플레이어 이동과 전투, BPM·SP 시스템, 적·보스 AI(Stage 1~5), 인벤토리·장비, NPC 상점, 씬 전환, 튜토리얼을 맡았습니다.

팀 저장소 커밋 423개 중 113개가 제 커밋입니다. 줄 단위 기록으로는 PlayerController의 약 79%, EnemyController의 약 76%를 작성했고, 튜토리얼과 씬 전환 관리자는 전부 작성했습니다(2026-11-09 기준). 아래 코드 링크의 공개 저장소는 백업본이라 최신 코드와 줄 위치가 다를 수 있습니다.

## 대시·넉백 중 어색해지던 움직임

대시나 넉백 중에 일반 이동 코드가 속도를 덮어써 움직임이 의도한 궤적에서 벗어났습니다. 직접 플레이하다 발견했고, 입력과 상태가 바뀌는 순간의 코드를 따라가 원인을 찾았습니다. 일반 이동 처리가 현재 행동 상태를 확인하지 않고 매 프레임 속도를 다시 설정하고 있었습니다.

행동 상태의 우선순위를 정해 대시·넉백·이동 지연 중에는 일반 이동을 건너뛰게 했습니다. 대시가 끝나면 보관해 둔 중력 배율과 상태를 되돌립니다.

[행동 상태 코드 보기](https://github.com/jinu217/Knight-Only_Backup/blob/34a70f4acfd6de09a10f83f147a3c17d706a0b13/Assets/Scripts/Player/PlayerController.cs#L860)

## 공격 한 번에 여러 번 들어가던 피해

적과 보스에 Collider가 여러 개 붙어 있어 공격 한 번에 같은 대상이 여러 번 피해를 받았습니다. Collider마다 상위 `IDamageable`을 찾아 실제 피해 대상의 ID를 `HashSet`에 넣고, 이미 들어 있으면 건너뜁니다. 판정의 단위를 Collider가 아니라 피해 대상으로 맞춘 구현입니다.

[공격 판정 코드 보기](https://github.com/jinu217/Knight-Only_Backup/blob/34a70f4acfd6de09a10f83f147a3c17d706a0b13/Assets/Scripts/Player/PlayerController.cs#L1170)

## BPM 배율이 겹쳐 쌓이던 구조

BPM은 공격과 대시로 오르는 전투 상태값입니다. 구간에 따라 공격력·공격속도·이동속도·대시·SP 수급에 배율이 붙는데, BPM이 바뀔 때마다 기본 스탯을 직접 고치면 배율이 겹치거나 원래 값으로 정확히 돌아오지 않았습니다.

기본값은 그대로 두고, 행동이 일어나는 시점에 현재 구간의 배율을 곱해 최종 값을 계산하도록 구조를 바꿨습니다. 탈진, 자연 감소, 명상, SP 수급도 같은 구조로 연결했습니다. PlayerStatus는 팀원이 처음 만든 클래스에 제가 BPM·SP·명상을 더했습니다.

## 적·보스 AI

![Stage 2 메인 보스 등장 장면]({{ '/images/projects/knight-only-boss2.jpg' | relative_url }})

탐지 범위·시야·공격 거리·공격 간격과 피격 반응은 공통 적 컨트롤러가 처리하고, 적마다 공격 방식만 다르게 구현합니다. 보스는 스킬 목록을 앞에서부터 검사해 조건을 만족하는 첫 스킬을 고르고, 실행 중에는 새 스킬을 고르지 않습니다.

Stage 2 메인 보스에는 필드를 깔고 그 안에서 버티는 전용 패턴을 만들었습니다. 발동 조건, 필드 효과, 필드 밖에 오래 있을 때의 복귀 규칙을 한 컴포넌트에 모으고, 강제 복귀가 다른 행동보다 우선하도록 순서를 정리했습니다.

## 씬 전환 관리자

여러 스크립트에 흩어져 있던 씬 이동을 비동기 전환 관리자 하나로 모았습니다. 로딩 패널을 띄우고, 전환 전에 저장한 뒤 `LoadSceneAsync`로 다음 씬을 불러옵니다. 다음 씬의 진입 위치는 Spawn ID로 정합니다. 저장은 팀원이 나눈 영구·회차 데이터 구조를 함께 확장해 사용했습니다.

## 그 밖에 맡은 시스템

![NPC 장비 상점 화면]({{ '/images/projects/knight-only-shop.jpg' | relative_url }})

- NPC 상점: 장비·대장간·버프 상점의 공통 동작을 한 기반 클래스에서 처리합니다.
- 장비 재계산: 장비를 바꾸면 기본 스탯에서 다시 계산해 효과가 거듭 쌓이지 않습니다. 기본 구조는 팀원과 함께 만들었고 재계산 함수는 제가 다시 작성했습니다. [장비 관리 코드 보기](https://github.com/jinu217/Knight-Only_Backup/blob/34a70f4acfd6de09a10f83f147a3c17d706a0b13/Assets/Scripts/Inventory/EquipmentManager.cs#L139)
- 하향 점프: 시작 발판과의 충돌만 잠시 끄고, 몸체가 발판 아래로 충분히 내려가면 다시 켭니다.
- 튜토리얼: 16단계로 나누고, 현재 단계가 예상 단계와 같을 때만 다음으로 넘어갑니다.

상세 코드와 화면은 [포트폴리오 PDF]({{ '/files/kim-jinwoo-portfolio.pdf' | relative_url }}) 4–12쪽에 정리했습니다.
