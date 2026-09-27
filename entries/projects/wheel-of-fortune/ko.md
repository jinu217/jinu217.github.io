---
title: "Wheel of Fortune"
type: project
layout: case-study
lang: ko
slug: wheel-of-fortune
permalink: /projects/wheel-of-fortune/
date: 2026-08-01
year: 2026
period: "2026.08 게임잼"
image: "/images/projects/wheel-of-fortune.png"
thumbnail: "/images/projects/wheel-of-fortune.png"
cover: "/images/projects/wheel-of-fortune.png"
cover_alt: "맵 노드와 룰렛을 보여주는 게임 화면"
thumbnail_alt: "Wheel of Fortune 프로젝트 화면"
label: "직접 구현"
role: "4인 팀 · 프로그래머"
technologies: [Unity, C#]
code: "https://github.com/jinu217/Wheel-of-Fortune"
demo: ""
excerpt: "로그라이크 턴제 게임의 이벤트 맵, 룰렛 추첨, 씬 전환 후 진행 상태 복원을 구현했습니다."
resume_line: "Unity·C# / 이벤트 맵·노드 연결·룰렛·회차 상태 복원"
---

## 프로젝트와 담당 범위

4인 게임잼 팀에서 이벤트 맵, 노드 연결, 룰렛, 전투 후 맵 복귀와 회차 상태를 구현했습니다.

## 연결 가능한 이벤트 맵

각 노드에 좌표, 이벤트 종류, 다음 노드 목록을 두었습니다. 상점·여관의 연속 연결을 제한하고 전투·랜덤 이벤트의 연속 횟수도 확인해 후보를 정합니다. 이전 층에서 이어질 수 있는 경로를 고려한 뒤 가중치로 이벤트를 선택하고 간선을 구성합니다.

노드의 다음 경로는 `List` 인접 리스트로 저장했습니다. 실제 연결만 기록하므로 공간은 노드와 간선 수에 비례합니다. 중복 연결 검사는 `List.Contains`를 사용하므로 해당 노드의 연결 수만큼 순회합니다. 현재 맵 규모에서는 단순한 구조를 택했고, 연결 검사 빈도나 밀도가 커질 경우 `HashSet`을 검토할 수 있습니다.

[연결 조건 코드 보기](https://github.com/jinu217/Wheel-of-Fortune/blob/0a62f3d881bc23f9f0aa3f758ad79aad462abb2e/Assets/Scripts/Map/InGameEventNode.cs#L93)

## 룰렛 추첨과 연출의 분리

10칸의 효과 구성을 데이터로 관리하고, 칸 수의 합을 검사합니다. 회전을 시작할 때 결과 칸을 먼저 선택하고 목표 각도를 계산한 뒤, 연출이 끝나면 결과 이벤트와 완료 콜백을 전달합니다. 결과만 얻는 경로와 효과까지 적용하는 경로를 분리했습니다.

[룰렛 코드 보기](https://github.com/jinu217/Wheel-of-Fortune/blob/0a62f3d881bc23f9f0aa3f758ad79aad462abb2e/Assets/Scripts/Roulette/RouletteController.cs#L334)

## 씬 전환 후 진행 상태 복원

세션에는 완료한 이벤트 좌표와 플레이어 상태를 보관합니다. 맵으로 돌아오면 완료 노드를 다시 표시하고 다음 선택 가능한 노드를 엽니다. 새 회차에서는 기록과 맵 시드를 초기화합니다. 씬을 넘는 데이터와 화면에서 다시 적용할 상태를 구분해 처리했습니다.

[진행 상태 코드 보기](https://github.com/jinu217/Wheel-of-Fortune/blob/0a62f3d881bc23f9f0aa3f758ad79aad462abb2e/Assets/Scripts/Map/InGameProgressionManager.cs#L59)

구조와 코드 발췌는 [전체 포트폴리오 PDF]({{ '/files/kim-jinwoo-portfolio.pdf' | relative_url }}) 33–37쪽에서 볼 수 있습니다.
