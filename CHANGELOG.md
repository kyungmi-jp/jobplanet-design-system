# CHANGELOG

피그마 `JDS 1.0` 의 변경을 언제, 무엇을, 어떻게 반영했는지 남긴다.
날짜는 **실측한 날**이다. 피그마가 바뀐 날과 다를 수 있다.

---

## 2026-09-07 — 최초 커밋

그동안 쌓아둔 실측 결과를 레포로 옮겼다. 아래는 이번에 담긴 내용이다.

### Foundation

- **Color** 88색 · **Typography** 21스타일 · **Spacing** 24단계
- **Grid** 섹션 `889:7665` 신규 실측
  - Desktop: 기준 1920 / Container **1200** / Margin **8** / Contents **1184** / 12컬럼 × 84 / Gutter 16
  - Mobile: 기준 393 / Margin **16** / Contents **361** / 4컬럼 / Gutter 16
  - 검산 `84×12 + 16×11 = 1184`
  - ⚠️ 모바일 컬럼 라벨은 `78px` 인데 `78×4 + 16×3 = 360` 으로 1px 이 빈다.
    실제는 **78.25px** 이므로 컬럼 폭을 고정하지 말고 `1fr` 로 나눠야 한다
  - ⚠️ 브레이크포인트는 피그마에 정의돼 있지 않다. CSS 의 `600px` 은 **임의로 정한 값**이다
- **Divider** 컴포넌트셋 `469:8873` 신규 실측 — `Type(Thin 1px · Thick 8px) × Color(Gray50 · Gray100)` 4조합
  - 보더가 아니라 **높이를 가진 배경 블록**이다. 그래서 Thick 8px 이 성립한다

### Graphic

- **Icon 334개** (`system-` 310 + `Brand-` 24) — 피그마 심볼 이름과 로컬 에셋 **양방향 차이 0** 확인
- **Emoji 127 → 128** — `emoji-jp-reportcenter` (`6063:14375`) 추가
  - 이 파일은 내부 `<g id>` 가 `emoji-clipboard` 로 잘못 붙어 있어 내려받으며 교정했다
- **삭제 예정 목록 정정** — 기존 기록이 `system-check*` 같은 와일드카드라 멀쩡한 아이콘까지 포함됐다.
  숨겨진 가이드 프레임(`3581:4216`, `3581:4217`) 좌표를 실측해 다시 추렸다
  - 삭제할 것: `check` · `check-20` · `checkbox-checked-line` · `checkbox-checked-fill` ·
    `checkbox-unchecked` · `checkbox-multi-checked` · **`Brand-twitter`**(새로 발견)
  - 나중에 삭제할 것: `radio-checked` · `radio-unchecked`
  - **대상 아님**: `check-circle` · `check-square` · `radio`(방송 아이콘)
- **사용 보류가 2개**였다 — `emoji-like` 외에 `new` 뱃지(`361:288`)도 함께 놓여 있다.
  단 `emoji-like` 는 컴포넌트로는 그리드에 살아 있으니 보인다고 써도 되는 게 아니다
- 네이밍 예외 추가 발견 — `emoji-talkNaver` 만 카멜케이스,
  번호 규칙이 `place2` · `heart02` · `resume-2` 세 가지로 제각각

### Components

- **Chip Selector** `1856:238` — **기존 기록이 틀렸다.** "32조합 중 8개만 받았다"고 돼 있었으나
  **8조합이 전부**다. `emogi` · `arrow` 는 변형 축이 아니라 불리언 프로퍼티라 곱해지지 않는다
  - 이모지는 **`Fill` 에서만** 그려진다. `Outlined` 에는 슬롯 자체가 없다
- **Chip Removable** `2446:12026` 신규 — `Size(32·36) × Theme(Primary·Secondary)` 4조합
  - 텍스트가 **항상 Regular 400** 이다 (Selector 의 On 은 SemiBold 600)
- **Checkbox 정렬 버그 수정** — 라벨 래퍼가 `content-box` 라 `24+2+2 = 28px` 이 되어
  한 줄일 때 세로 중앙이 어긋났다. **`border-box`** 로 고쳤다
  - 피그마의 control height(24 / 22)는 상하 padding 을 **포함한** 값이다
  - 이 컴포넌트는 `align-items:center` 로 중앙을 맞추는 게 아니라,
    **래퍼 높이를 라벨 line-height 와 같게 만들어서** 한 줄=중앙 / 여러 줄=상단이 동시에 성립한다
- **Mobile Header** 신규 — 컴포넌트셋이 **두 벌**이다
  - `Main bar` `21:23114` 1종 (로고형) / `Nav bar` `21:23096` 4종
  - 공통 393 × 56, 터치영역 **40×40**(PC 는 32×32)
  - `Sub/Info` 의 우측 아이콘만 **20px**
  - `Sub/Icon2` 의 `padding-right:40px` 은 장식이 아니라 **타이틀을 정중앙에 두는 균형추**다
- **Tab** `895:925` 신규 — `개수(2~7) × Select(1~n)` = **27조합**
  - 탭 줄 52 + Divider 1 = **53**, 폭은 **`66n − 8`**
  - 인디케이터가 **Green 이 아니라 Gray800**, 미선택 텍스트는 **Gray200**
  - 2px 인디케이터는 **아이템 안쪽**에 그린다. `border-bottom` 으로 만들면 높이가 54 가 된다

### 그 외

- 피그마 쪽에서 Divider 컴포넌트셋 이름 오타(`Divier` → `Divider`)가 수정됨을 확인
- 여러 컴포넌트에서 **아이콘 레이어 이름이 `system-chevron-left` 로 잘못 붙어 있는** 패턴 확인
  (Chip, Mobile Header 등). 실제 에셋은 chevron-down / x / share / heart / help-circle 이다

---

## 남은 것

`Shadow` · `Modal` · `Bottomsheet` · `텍스트 필드` · `태그` · `Radio` · `Icon Button` ·
`ButtonPagenationArrow` — 노드 링크가 생기면 실측해서 채운다.
