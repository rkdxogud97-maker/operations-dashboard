# Production management operations dashboard

_Started 2026-06-30 01:28 UTC_

---

## User

# Claude Design 프롬프트 — 생산관리 운영 대시보드 UI

> 이 프롬프트와 함께 **(1) 사내 포털 캡처 이미지**, **(2) PRD v0.2/v0.3 문서**를 첨부해서 주면 가장 정확합니다. 프롬프트 자체에 핵심은 모두 담았습니다.

---

## 무엇을 디자인하나

석유화학 회사의 **생산관리·기술 담당자 1인이 매일 보는 개인 업무 운영 대시보드**의 UI를 디자인해줘. 다양한 주기의 업무(1회성·매주·매월·연 1회·중장기)와 자산화/변경관리 같은 장기 과제를 한 화면에서 관리하고, 마감·마일스톤 임박을 놓치지 않게 알려주는 도구야. 기능 정의는 첨부 PRD를 따르고, 아래 두 가지를 반드시 반영해줘.

---

## 1. 사용 환경 (레이아웃 최우선 조건)

- 사용자는 **랩탑(약 1440px)과 32인치 모니터(약 2560px)** 로만 본다. **데스크톱 와이드 화면 우선**으로 설계해줘. 모바일 우선이 아니다.
- 넓은 가로 공간을 **적극적으로 활용**해줘. 중앙에 좁은 한 컬럼으로 몰지 말고, **다중 컬럼 그리드**로 한눈에 많은 정보를 펼친다.
- 콘텐츠 최대 폭은 **약 1680px 내외로 가운데 정렬**, 32인치에서는 좌우 여백과 컬럼 폭이 시원하게 늘어나도록(또는 컬럼 수가 늘어나도록) 반응형을 잡아줘.
- **정보 밀도는 높되 답답하지 않게.** 한 화면에서 오늘 할 일·이번 주·이번 달·임박 마일스톤을 동시에 보면서도 카드 사이 여백으로 숨 쉴 공간을 확보한다.

---

## 2. 디자인 원칙 (첨부 캡처 = 사내 포털 톤에 맞춤)

전체 인상은 첨부한 사내 인트라넷 포털과 **같은 계열의 차분한 엔터프라이즈 라이트 모드**여야 한다. 사용자가 매일 보는 사내 시스템과 이질감 없이 자연스럽게 이어지는 것이 목표다. **단, 포털의 로고·브랜드명(Cleverse 등)은 베끼지 말 것.** 시각 언어와 톤만 일치시키고, 우리 도구만의 미니멀한 자체 마크를 쓴다.

**색 (캡처 기준, 근사값 — 이미지 톤에 맞춰 조정 가능)**
- 페이지 배경: 아주 옅은 쿨 그레이 `#F4F5F7`
- 카드/표면: 화이트 `#FFFFFF`, 매우 옅은 그림자
- 상단 헤더 바: 거의 검정 `#101012` + 흰 텍스트 (포털 상단 바와 동일한 인상)
- 기본 텍스트: 짙은 잉크 `#1C212B` / 보조 텍스트: 그레이 `#8A929E`
- **포인트 컬러: 코랄~오렌지** `#FF6B4A`(주 포인트) — 로고/도넛 게이지/포인트 pill/캐러셀 점에 쓰인 그 톤
- **경보/신규 배지: 강한 레드** `#FB3B3B` ("N", "New" 같은 알림 표시)
- 분할선/스크롤바: 얇고 옅은 그레이

**타이포그래피**
- 한글은 **Pretendard 계열**(또는 Noto Sans KR)의 깔끔한 산세리프. 영문 섹션 제목(예: "Email", "Approval", "WORK")처럼 **영문 단어는 굵게(Bold)** 포인트로 쓰는 포털의 습관을 살린다.
- 핵심 숫자(진척률·D-day·건수)는 **크고 굵게** — 도넛 가운데 "58%"처럼 한눈에 읽히는 대형 수치 표현.

**카드 & 컴포넌트 패턴 (포털에서 그대로 가져올 것)**
- 카드: **큰 라운드(약 16px)** + **아주 부드러운 그림자**, 넉넉한 안쪽 여백(약 20~24px).
- 섹션 헤더: 좌측 굵은 제목 + 우측 **라운드 사각형 "+" 버튼**(옅은 그레이 배경).
- 탭 토글: 활성 탭은 **굵은 잉크색**, 비활성은 그레이(포털의 "사업장공지 / 전사공지 / 그룹공지" 스타일).
- 측면 세로 탭: 활성 항목 옆 **검은 세로 인디케이터 바**(포털의 WORK/INFO처럼) — 보드/중장기 전환에 응용 가능.
- 데이터 시각화: **도넛/링 게이지 + 가운데 대형 수치**(진척률·완료율에 사용), 코랄 그라데이션 아크.
- 리스트 행: (썸네일/아이콘) + **굵은 한 줄 제목(말줄임)** + 그레이 보조정보 + 우측 정렬 날짜 + 신규 시 빨간 "N" 배지, 얇은 커스텀 스크롤바.
- 상태 pill, 옅은 그레이 라인의 빈 상태(empty state) 일러스트.

---

## 3. 화면별 요구 (PRD 기능 → 위 디자인 언어로)

**① 상단 헤더 바 (검정)**
포털과 같은 검은 풀폭 바. 좌측에 도구명(예: "운영 대시보드")과 미니 마크, 우측에 **알림 종 아이콘(미확인 건수 빨간 배지)**, "+ 업무 추가" 버튼, 그리고 포털의 출근/퇴근 pill을 응용한 **오늘 날짜·요약 pill**(예: "오늘 마감 2 · 임박 마일스톤 3").

**② 메인 보드 — 4구역 (와이드 핵심 화면)**
"오늘·지난 마감 / 이번 주 / 이번 달 / 곧 도래" 네 구역. 와이드 화면이므로 **4개 컬럼을 가로로 펼치거나**, "오늘"을 넓게 강조하고 나머지 3개를 컬럼으로 두는 구성. 각 업무 카드: 업무명, 유형 칩(1회성/매주/매월/N일/연1회/중장기), 중요도 표시, **우측 대형 D-day(D-7, D-DAY, 지남 시 D+N 강조)**, 1회성·중장기는 진척 바, 완료/수정/삭제. 마감 임박순 정렬, 지난 마감은 레드 강조.

**③ 알림 센터 (헤더 종 → 드롭다운 패널)**
"지난 마감 / 오늘 마감 / 임박 마일스톤" 세 묶음 리스트(좌측 컬러 점 + 제목 + 보조정보 + 우측 D-day). 하단에 데스크톱 알림 on/off 상태 표시와 "마일스톤 알림 시점 D-[N]일" 설정. 포털의 알림/리스트 톤을 그대로.

**④ 중장기 관리 (별도 탭/화면)**
자산화사업·변경관리(MOC)·기타 과제 카드. 카드마다: 과제명, 분류 칩, 상태(진행/대기/보류/완료), **진척률(도넛 또는 굵은 바 + 대형 %)**, 목표일, 그리고 **마일스톤 타임라인**(단계명 + 목표일 + D-day, 완료 체크, 임박/지연 색 구분). 와이드 화면에서는 2컬럼 카드 그리드.

**⑤ 캡처 등록 플로우 (모달)**
보고서 화면 캡처 업로드 → 해석(로딩) → **등록 미리보기 표**(날짜/업무명/기한/완료/메모/상태 컬럼, 행별 제외·수정, 낮은 신뢰도 강조) → "N건 등록" 확정.

---

## 4. 기능 요약 (디자인이 알아야 할 만큼만 — 상세는 PRD)

업무는 반복 유형별로 다음 도래일이 자동 계산되어 4구역에 배치된다. 일일/주간 보고 **캡처를 업로드하면 자동으로 업무가 추출·등록**되고(취소선=완료, 열 위치=날짜), 중복은 갱신 처리된다. 중장기 과제는 마일스톤·진척률로 관리하며, 마일스톤이 D-N에 들면 알림 센터로 떠오른다. 데이터는 개인용으로 로컬 저장된다.

---

## 5. 카피 & 보이스
- **UI 전부 한국어**, 간결하고 능동태. 라벨은 사용자가 인지하는 말로(예: "완료", "업무 추가"). 같은 동작은 흐름 내내 같은 단어로.
- 빈 상태는 무엇을 하면 되는지 안내하는 한 줄 + 행동 버튼.

## 6. 품질 기준
- 라이트 모드, 키보드 포커스 가시화, 명도 대비 충분, 모션 최소·은은하게.
- 1440px와 2560px 두 폭에서 모두 균형 잡히게(특히 32인치에서 빈 공간이 휑하지 않도록 컬럼/여백 확장).

## 7. 산출물
일관된 디자인 시스템(색·타입·컴포넌트) 위에서 **(a) 메인 보드(4구역) 와이드 화면, (b) 중장기 관리 화면, (c) 알림 센터 패널, (d) 캡처 등록 미리보기 모달**을 디자인해줘. 가능하면 1440px와 2560px 두 폭의 보드 화면을 함께 보여주면 좋겠어.

## Assistant

This is a remarkably complete brief — colors, type, layout, screens, copy, and quality bar are all specified. Before I build, a few decisions will shape the output. (Note: no capture images or PRD actually came through as attachments — but you said the prompt carries the essentials, so I'll work from it.)

_[tool: questions_v2]_

## User

Questions answered:
- deliverable_mode: 동작 프로토타입 + 핵심 화면 디자인 변형(옵션) 병행
- interactivity_depth: 풀 인터랙션 — 업무 추가/완료/삭제, 알림 드롭다운, 캡처 모달 단계 진행까지 실제 동작 + 로컬 저장
- data_realism: 실제 업무처럼 구체적 (예: '촉매 교체 주기 점검', 'MOC-2024-017 변경관리', '월간 생산실적 보고')
- korean_font: Pretendard (캡처 톤에 가장 근접)
- primary_width: 반응형 하나로 만들고 두 폭에서 각각 캡처해 비교
- variation_focus: 중장기 관리의 마일스톤 타임라인 표현, 업무 카드 / D-day 표현 방식, 메인 보드 4구역의 레이아웃 (4컬럼 vs 오늘 강조형 등)

## Assistant

This is a meaty, well-specified build. Let me set up my plan and get the design system + prototype going.

_[tool: update_todos]_

_[tool: dc_write]_

Let me remove the unused `createElement` and check the render.

_[tool: dc_js_str_replace]_

_[tool: show_html]_

_[tool: show_html]_

Renders cleanly. The header wrapping is just the narrow preview pane — at 1440/2560 the zones get room. Let me confirm the other views and check for errors.

_[tool: eval_js]_

_[tool: get_webview_logs]_

No errors. Clean. Handing to the verifier for thorough checks across views and widths.

_[tool: update_todos]_

동작하는 풀 프로토타입을 만들었습니다 — **운영 대시보드.dc.html**.

**담긴 것**
- 검정 헤더 바(요약 pill · 알림 종+빨간 배지 · 업무 추가) + 오늘 보드 / 중장기 관리 탭
- 메인 보드 4구역(오늘·지난 / 이번 주 / 이번 달 / 곧 도래), 마감 임박순 정렬, 지난 마감은 레드 강조, 유형 칩·중요도·대형 D-day·진척 바
- 중장기 관리: 도넛 진척률 + 마일스톤 타임라인(완료/임박/지연/예정 색 구분)
- 알림 센터 드롭다운(지난/오늘/임박 + 데스크톱 알림 토글 + D-N일 설정)
- 캡처 등록 모달: 업로드 → 해석 로딩 → 미리보기 표(완료 취소선·낮은 신뢰도·중복 갱신) → N건 등록
- 완료/수정/삭제·추가 전부 실제 동작 + localStorage 저장. Pretendard, 캡처 톤 라이트 모드, 반응형(1440~2560).

**디자인 변형**은 우측 Tweaks 패널에서 즉시 전환됩니다 — 보드 레이아웃(4컬럼 / 오늘강조), D-day 표현(대형숫자 / pill배지), 타임라인(수직 / 수평).

다음으로 원하시면: 세 변형을 한 페이지에 나란히 비교하는 옵션 시트를 따로 만들거나, 캡처 모달에 실제 이미지 업로드 미리보기를 붙일 수 있습니다.

_[tool: ready_for_verification]_

프로토타입이 깨끗하게 로드됐고 검증을 백그라운드로 넘겼습니다. 미리보기에서 바로 만져보세요 — 업무 추가/완료, 알림 종, "캡처로 등록", 중장기 탭, 그리고 Tweaks 패널의 세 변형까지 모두 동작합니다.

## User

ㅇㅇㅇ

## Assistant



## User

만약 업무가 많아져서 한 페이지에 다 담기지 않으면 스크롤을 통해 아래로 내려 확인할 수 있는거지?

## Assistant

네, 맞습니다. 업무가 많아지면 각 구역(컬럼)의 카드가 아래로 계속 쌓이고, **페이지 전체가 세로 스크롤**되어 아래로 내려 확인할 수 있습니다. 가로 스크롤은 생기지 않습니다.

지금은 페이지 통째로 스크롤되는 방식이라, 한 구역만 길어지면 그 구역만 길게 늘어납니다. 원하시면 다음 중 하나로 바꿀 수 있어요:

- **구역별 독립 스크롤** — 각 컬럼에 최대 높이를 주고 컬럼 안에서만 스크롤(헤더 4개는 항상 상단 고정). 구역 간 높이가 들쭉날쭉해지지 않습니다.
- **건수 많을 때 접기** — 구역당 예: 6건까지 보이고 "+N건 더 보기"로 펼치기.

지금의 전체 페이지 스크롤을 유지할지, 위 둘 중 하나로 바꿀지 알려주시면 반영하겠습니다.

## User

구역별 독립 스크롤과 건수 많을 때 접기 둘 다 적용해주면 좋을 것 같아.

## Assistant



## User

구역별 독립 스크롤로 바꿔줘.

## Assistant

둘 다 적용하겠습니다 — 구역별 독립 스크롤 + 건수 많을 때 접기("+N건 더 보기").

_[tool: read_file]_

_[tool: read_file]_

Now the edits — body scroll wrapper, sliced list, and the more/collapse button:

_[tool: dc_html_str_replace]_

_[tool: dc_html_str_replace]_

_[tool: dc_html_str_replace]_

Now the logic — add per-zone expand state and the visible/more fields:

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

Both applied. Default sample data has under 5 per zone so the "더 보기" button only appears once a zone exceeds the limit (10 in the wide 오늘강조 layout, 5 otherwise). Let me confirm it still renders cleanly.

_[tool: show_html]_

구역별 독립 스크롤이 적용됐습니다 — 각 컬럼이 헤더는 고정한 채 자체 스크롤바를 가지며, 한 구역이 길어져도 화면 높이 안에서만 스크롤됩니다. 더불어 한 구역이 5건(오늘강조 와이드 구역은 10건)을 넘으면 "**+N건 더 보기 / 접기**" 버튼으로 접거나 펼칠 수 있습니다.

_[tool: ready_for_verification]_

끝났습니다. 미리보기에서 각 구역을 따로 스크롤해보시고, 업무를 여러 건 추가하면 "더 보기/접기" 버튼도 확인하실 수 있습니다.

## User

캡처로 등록하는 방법 외에, 초안처럼 보고 자료 내용을 복사 붙여넣기 하는 방안을 고민해보자.

새 업무 추가 버튼을 눌렀을 때 별도의 탭을 하나 추가해서 '텍스트 붙여넣기'로 만들어줘.

그리고, 1~12월을 선택할 수 있는 버튼을 만들어 주면 내가 특정 월을 선택한 후 해당 월의 일일보고 내용을 쭉 드래그해서 붙여넣을거야.

내용이 중복되는 업무는 알아서 걸러주면 좋을 것 같고.

## Assistant

보고 자료를 붙여넣어 한 번에 등록하는 방식, 좋습니다. "새 업무 추가" 모달에 **직접 입력 / 텍스트 붙여넣기** 탭을 만들고, 붙여넣기 탭에 1~12월 선택 버튼 + 큰 입력창 + 중복 자동 필터링 미리보기를 붙이겠습니다. 현재 모달 구조부터 확인할게요.

_[tool: grep]_

_[tool: read_file]_

Now I'll rewrite the add modal with tabs. Replacing the whole inner modal:

_[tool: str_replace_edit]_

Now the logic — state, openAdd reset, the parser, and handlers:

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

Now the renderVals fields for the modal tabs and paste step:

_[tool: dc_js_str_replace]_

_[tool: dc_js_str_replace]_

Let me test the full flow — open the modal, switch to paste tab, paste sample text, parse, and check the preview:

_[tool: eval_js]_

_[tool: eval_js]_

_[tool: save_screenshot]_

_[tool: save_screenshot]_

_[tool: get_webview_logs]_

_[tool: eval_js]_

_[tool: eval_js]_

_[tool: eval_js]_

The preview is stale — let me force a fresh load and re-test the modal.

_[tool: show_html]_

_[tool: save_screenshot]_

Screenshots aren't capturing the fixed-overlay modal reliably. Let me verify via DOM after the fresh load.

_[tool: eval_js]_

Tabs, textarea, and 12 month buttons all render. Now let me test the parse + dedupe flow end-to-end.

_[tool: eval_js]_

Parse + dedupe work (8 lines → 6 rows, "6건 등록"), but there's a name-cleaning bug: the date prefix `06/02` leaves a stray `/` and clips `일일`. Let me fix the cleaning order — strip the full date token before anything else.

_[tool: dc_js_str_replace]_

Now let me re-run the parse to confirm clean names and that duplicates against existing tasks are auto-caught.

_[tool: eval_js]_

The hot-reload didn't refresh the running parser instance — still old behavior. Let me reload the page fresh, then re-test.

_[tool: show_html]_

_[tool: eval_js]_

Now it works correctly: names are clean, the repeated "질소 퍼지" line deduped (8 lines → 6), "일일 운전일지 검토 및 인계" matched an existing task → **중복(갱신) auto-excluded**, "특이사항" header filtered, and the no-date line flagged "확인" → "**5건 등록**".

Let me reset to a clean board view for handoff.

_[tool: show_html]_

"업무 추가" 모달에 **텍스트 붙여넣기** 탭을 추가했습니다. 동작은 DOM 단으로 전부 검증했습니다(고정 오버레이 모달이라 정적 캡처에는 안 잡히지만 실제로는 정상 렌더·동작).

**텍스트 붙여넣기 탭 흐름**
- 상단에 **1~12월 버튼** — 월을 고르면 코랄로 강조됩니다.
- 큰 입력창에 해당 월의 일일 보고를 드래그해 붙여넣고 "해석하기".
- 줄 단위로 업무를 인식 — 앞쪽 날짜(MM/DD·N일)는 자동 추출해 "날짜" 열로, "완료"·취소선·체크는 완료로 처리, "특이사항"·"오전" 같은 머리글은 자동 제외.
- **중복은 알아서 필터**: 같은 줄이 반복되면 한 건으로, 기존 등록 업무와 겹치면 "중복(갱신)" 배지를 달고 기본 체크 해제(자동 제외) — 나머지만 "N건 등록"으로 반영됩니다.
- 날짜를 못 읽은 줄은 "확인" 배지로 표시해 검토를 유도합니다.

직접 입력 탭은 기존 폼 그대로이고, 수정 시에는 탭 없이 단일 폼으로 열립니다.

테스트용 스크린샷만 정리하고 마무리하겠습니다.

_[tool: delete_file]_

_[tool: ready_for_verification]_

완료했습니다. "업무 추가" → **텍스트 붙여넣기** 탭에서 월을 고르고 일일 보고를 붙여넣어 보세요 — 날짜·완료 자동 인식, 중복 자동 제외, "N건 등록"까지 동작합니다. 캡처 등록 방식도 그대로 함께 있습니다.

