# 리깅 모델과 적용 안내

2026-11-02 · 학생 번호 16의 기존 리깅 작업에서 선정한 모델입니다.

**모델 파일만 추가한 상태입니다. 현재 실행 게임에는 아직 연결되지 않았습니다.**

## 파일과 동작

- [miner.glb](miner.glb): 3.66 MiB, 23관절, 6동작 — miner_idle, miner_walk, miner_run, flashlight_raise, key_use, bandage_use
- [miner_hands_equipment.glb](miner_hands_equipment.glb): 0.95 MiB, 30관절, 7동작 — miner_idle, flashlight_raise, flashlight_aim, key_use, bandage_use, miner_walk, miner_run
- [horn_monster.glb](horn_monster.glb): 2.66 MiB, 11관절, 4동작 — horn_idle, charge_telegraph, charge_forward, charge_recover
- [fourarm_monster.glb](fourarm_monster.glb): 2.61 MiB, 19관절, 4동작 — fourarm_idle, arm_prepare, arm_extend, arm_retract
- [golem_monster_repaired.glb](golem_monster_repaired.glb): 23.41 MiB, 13관절, 4동작 — golem_idle, capture_warning, golem_capture, golem_walk

## 제작 출처와 확인 범위

Hunyuan 생성 메시를 바탕으로 만든 게임용 GLB입니다. 파일에 따라 Hunyuan 리그를 유지하거나 Blender에서 골격·가중치·동작을 보완했습니다. 모든 리그나 동작을 Hunyuan 자동 생성물로 표시하면 안 됩니다. 항공기·드론은 사람형 스킨 대신 기계 부품 계층 애니메이션을 사용합니다.

골렘은 어깨/상완 가중치 수정본입니다. 일부 눌림과 주름이 남아 있고 실제 게임 충돌/포획 검증이 필요합니다.

GLB 구조, 클립 목록, 내장 의존성과 파일 SHA-256을 확인했습니다. 모델이 정상적으로 게임에서 움직이는지는 이번 업로드에서 검증하지 않았습니다.

## 게임에 적용하는 순서

1. 별도 작업 브랜치에서 기존 게임 변경 내용을 보존합니다.
2. assets.json에 필요한 모델 경로를 등록하고 game.js 또는 source.template.html/src의 로더와 연결합니다.
3. manifest.json의 실제 클립 이름으로 AnimationMixer/clipAction을 연결합니다. 기존 이름과 다르면 이름 대응표가 필요합니다.
4. 모델 크기, 발 위치, 축, 무기/효과 소켓, 충돌, 카메라 및 1인칭 팔 표현을 맞춥니다.
5. 기존 build.ps1로 index.html을 재생성합니다.
6. 시작·이동·공격/점프·피격·재시작을 직접 플레이해 확인합니다.

기존 assets.json과 실행 HTML은 이번 업로드에서 수정하지 않았습니다. 대기·이동 모델만 교체하고 공격/피격 연결을 빠뜨리지 마세요.
