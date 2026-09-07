---
name: jobplanet-ds
description: 잡플래닛 디자인시스템(JDS 1.0) — 컬러 88색·타이포 21스타일·스페이싱 24단계·그리드(1200/12col)·컴포넌트 실측 스펙과 아이콘 334개·이모지 128개 SVG 원본. UI·화면·목업·와이어프레임·프로토타입·랜딩을 만들거나 수정할 때 반드시 먼저 로드한다. 요청에 "잡플래닛"이 없어도 화면을 그리는 작업이면 로드한다. 트리거: 잡플래닛, JDS, 화면 그려줘, 목업, 와이어프레임, 프로토타입, UI 만들어줘, 리뷰 작성/목록, 기업 상세, 채용 공고, 연봉, 커리어, 랜딩페이지.
---

# 잡플래닛 디자인시스템 (JDS 1.0)

출처: Figma `JDS 1.0` (fileKey `c9OwXAPlMJ9YKVDF9ox7O2`) — Color 페이지 `0:1`, Updates 페이지 `2364:27068`에서 추출.

## 먼저 할 것

화면을 그리기 전에 **`reference.html`을 읽고 `:root` 토큰 블록과 `.jds-*` 타이포 클래스를 그대로 복사**해서 쓴다.
값을 다시 타이핑하지 말고 복사한다. Chip Selector도 이 파일의 마크업을 복사해서 조립한다.

## 절대 규칙

1. **색상은 아래 팔레트 밖의 값을 쓰지 않는다.** 임의의 hex 금지.
2. **폰트는 Pretendard.** 폴백: `Pretendard, -apple-system, BlinkMacSystemFont, "Apple SD Gothic Neo", "Malgun Gothic", sans-serif`
   웹 임베드: `https://cdn.jsdelivr.net/gh/orioncactus/pretendard@v1.3.9/dist/web/static/pretendard.css`
3. **한글 줄바꿈은 `word-break: keep-all`** — 단어 중간에서 끊기면 안 됨. (JDS 컴포넌트는 `word-break: break-word` 사용하나, 본문 텍스트는 keep-all이 맞다)
4. 기본 텍스트 색은 **Gray800 `#323438`**, 최고 대비 텍스트/딥 배경은 Gray900 `#242628`.
5. 보더는 **Gray100 `#e5e6e9`**, 디바이더는 **Gray50 `#f3f3f4`**. 둘을 섞어 쓰지 않는다.

## 화면 규칙

유저가 정한 사용 규칙이다. **컴포넌트 스펙보다 우선한다.** 계속 추가된다.

### R1 — 메인 CTA
모바일·웹 화면의 **메인 CTA**(보통 화면 하단에 놓이는 주요 행동 버튼)는 항상 이 변형을 쓴다.

```
button / theme=Primary / state=default / size=Large(52) / Shape=Rounded
```

| 항목 | 값 |
|---|---|
| 높이 | **52px** (min-width 52) |
| padding | `14px 16px` |
| gap | 6px |
| radius | **10px** (Pill 아님) |
| 배경 | `Green500 #00c274` |
| 글자 | White · `Heading 1` **16 / 24 / SemiBold 600** |
| 아이콘 | 20px |

**배치**

| 항목 | 값 |
|---|---|
| 폭 | **화면 폭을 꽉 채운다.** 좌우 여백 `16px` 을 두고 나머지 전부 |
| 하단 고정 | **정해진 기본값 없음.** 화면 성격에 따라 sticky / 콘텐츠 흐름 끝 중에 고른다 |
| 담는 영역 | 별도 padding·배경·상단 보더 **없음** |

폭·여백은 피그마 실측이 아니라 **유저가 정한 규칙**이다.
하단 고정 여부는 규칙으로 못 박지 않았으므로, 판단이 갈리면 유저에게 묻는다.

**개수**

한 화면에 메인 CTA는 하나다. 나머지 행동은 Secondary·Tertiary·Quaternary 로 낮춘다.
Large(52) 를 CTA 아닌 곳에 쓰지 않는다.

```html
<div style="padding:0 16px">
  <button class="jds-cta jds-cta--block">지원하기</button>
</div>
```

## Color

각 색상은 30 / 50 / 100 / 200 / 300 / 400 / 500 / 600 / 700 / 800 / 900 = 11단계.

### Gray (뼈대)
| 단계 | Hex | 용도 |
|---|---|---|
| Gray30 | `#f9f9fb` | 가장 옅은 배경 |
| Gray50 | `#f3f3f4` | **디바이더**, Fill 칩 배경 |
| Gray100 | `#e5e6e9` | **보더**, Tab 디바이더 |
| Gray200 | `#c5c7cc` | |
| Gray300 | `#a4a6ad` | placeholder / disabled 텍스트 |
| Gray400 | `#85878c` | |
| Gray500 | `#686a6d` | 보조 텍스트 |
| Gray600 | `#57595b` | |
| Gray700 | `#4b4c50` | |
| Gray800 | `#323438` | **기본 텍스트 색상** |
| Gray900 | `#242628` | 강조 텍스트, 딥 배경, 선택된 칩 |

### Green (메인 브랜드)
| 단계 | Hex | 용도 |
|---|---|---|
| Green30 | `#f2fbf7` | |
| Green50 | `#e3f8ed` | 연한 배경 |
| Green100 | `#b8ebd0` | |
| Green200 | `#87e0b6` | |
| Green300 | `#57d49b` | |
| Green400 | `#29c886` | |
| Green500 | `#00C274` | **메인 그린 — 브랜드 기준색** |
| Green600 | `#00a866` | 태그 텍스트 (500→600 변경됨) |
| Green700 | `#008552` | |
| Green800 | `#006840` | |
| Green900 | `#024c30` | |

### Purple (프리미엄)
| 단계 | Hex | 용도 |
|---|---|---|
| Purple30 | `#f9f8fc` | |
| Purple50 | `#f2f0f9` | |
| Purple100 | `#d0cbec` | |
| Purple200 | `#aaa1dd` | |
| Purple300 | `#8477cf` | |
| Purple400 | `#6856c3` | |
| Purple500 | `#523cc3` | **프리미엄 메인** |
| Purple600 | `#4736b5` | |
| Purple700 | `#3b2ead` | |
| Purple800 | `#3127a0` | |
| Purple900 | `#2b1b92` | |

### Blue
`#f6fbfe` `#ecf6fe` `#bbdefb` `#90caf9` `#64b5f6` `#42a5f5` `#2196f3` `#1e88e5` `#1976d2` `#1565c0` `#0d47a1`

### Red (에러 / 경고)
`#fff7f7` `#fff0f2` `#ffcdcd` `#f6a2a2` `#f38181` `#ef5350` `#f44336` `#e53935` `#d32f2f` `#c62828` `#b71c1c`

### Orange
`#fffaf5` `#fff3e0` `#ffe0b2` `#ffcc80` `#ffb74d` `#ffa726` `#ff9800` `#fb8c00` `#f57c00` `#ef6c00` `#e65100`

### Yellow
`#FDFCF5` `#FAF9EC` `#F6F3CB` `#F5E993` `#FDE047` `#FACC15` `#F0B500` `#D79304` `#AB6807` `#8D510E` `#402812`

### Teal
`#f1fffd` `#e0fffa` `#b8f0e7` `#87ded0` `#63d3c1` `#40c8b2` `#1cbda3` `#15a78f` `#0e917b` `#077a68` `#006454`

### Base / Gradient
| 이름 | 값 | 용도 |
|---|---|---|
| White | `#FFFFFF` | |
| Dim | `#242628` @ 50% | 모달 딤 배경 |
| Gradient-1 | `#9575cd` → `#5c6bc0` | 프리미엄 |
| Gradient-2 | `#FFD34E` → `#FFA726` | 별점 |
| Gradient-3 | `#00C274` 0% → `#7EC6FF` 70% → `#AC9CFF` 100% | 검색 바 |

## Typography

폰트 **Pretendard**, 자간 0 (Display만 -0.6). 웨이트 4종만 사용: Regular 400 / Medium 500 / SemiBold 600 / Bold 700.

| 스타일 | size | line-height | weight | 자간 |
|---|---|---|---|---|
| Display 1 | 52 | 72 | Bold 700 | -0.6 |
| Display 2 | 40 | 56 | Bold 700 | -0.6 |
| Title 1 | 32 | 44 | Bold 700 | 0 |
| Title 2 | 28 | 40 | Bold 700 | 0 |
| Title 3 | 26 | 36 | Bold 700 | 0 |
| Title 4 | 24 | 34 | Bold 700 | 0 |
| Title 5 | 22 | 30 | Bold 700 | 0 |
| Title 6 | 20 | 28 | Bold 700 | 0 |
| Title 7 | 18 | 26 | Bold 700 | 0 |
| Heading 1 | 16 | 24 | SemiBold 600 | 0 |
| Heading 2 | 15 | 24 | SemiBold 600 | 0 |
| Heading 3 | 14 | 22 | SemiBold 600 | 0 |
| Heading 4 | 13 | 20 | SemiBold 600 | 0 |
| Body 1 | 16 | 24 | Regular 400 | 0 |
| Body 2 | 15 | 24 | Regular 400 | 0 |
| Body 3 | 14 | 22 | Regular 400 | 0 |
| Body 4 | 13 | 20 | Regular 400 | 0 |
| Caption 1 | 12 | 18 | SemiBold 600 | 0 |
| Caption 2 | 12 | 18 | Medium 500 | 0 |
| Caption 3 | 11 | 16 | SemiBold 600 | 0 |
| Caption 4 | 11 | 16 | Medium 500 | 0 |

**체계 읽는 법**
- `Display` / `Title` = Bold 700. 화면 타이틀, 섹션 제목.
- `Heading` = SemiBold 600. Body와 **size·line-height가 완전히 같고 weight만 다름** (16/24, 15/24, 14/22, 13/20). 같은 문단 안에서 강조할 때 Heading↔Body를 갈아끼우면 줄이 밀리지 않는다.
- `Body` = Regular 400. 본문.
- `Caption` = 12·11px. SemiBold(1,3) 와 Medium(2,4) 짝. Regular 캡션은 없다.
- **Title 7(18) 과 Heading 1(16) 사이가 유일한 큰 점프.** 제목 위계는 Title에서, 본문 위계는 Heading/Body에서 잡는다.

자주 쓰는 조합:
- 화면 타이틀 `Title 4`(24) 또는 `Title 6`(20)
- 카드/리스트 아이템 제목 `Heading 1`(16) 또는 `Heading 3`(14)
- 본문 `Body 3`(14) / 조밀한 리스트 `Body 4`(13)
- 메타정보·날짜·보조 라벨 `Caption 2`(12 Medium), 색은 Gray500
- 밸리데이션 에러 문구 `Caption 2` + Red

## Spacing

24단계. **토큰 번호 = px × 25** 로 정확히 대응한다 (`spacing-350` = 14px).
타이포의 `font-size-350 = 14` 와 같은 명명 체계다 — 숫자를 25로 나누면 px가 나온다.

| 토큰 | 값 |
|---|---|
| `spacing-50` | **2px** |
| `spacing-100` | **4px** |
| `spacing-150` | **6px** |
| `spacing-200` | **8px** |
| `spacing-250` | **10px** |
| `spacing-300` | **12px** |
| `spacing-350` | **14px** |
| `spacing-400` | **16px** |
| `spacing-450` | **18px** |
| `spacing-500` | **20px** |
| `spacing-550` | **22px** |
| `spacing-600` | **24px** |
| `spacing-650` | **26px** |
| `spacing-700` | **28px** |
| `spacing-750` | **30px** |
| `spacing-800` | **32px** |
| `spacing-900` | **36px** |
| `spacing-1000` | **40px** |
| `spacing-1200` | **48px** |
| `spacing-1400` | **56px** |
| `spacing-1600` | **64px** |
| `spacing-1800` | **72px** |
| `spacing-2000` | **80px** |
| `spacing-2400` | **96px** |

**스케일이 촘촘해지는 구간이 다르다**
- `2 ~ 32px` : **2px 단위** — 컴포넌트 내부 여백. 이 구간은 홀수 배수(6, 10, 14, 18, 22, 26, 30)도 전부 정식 토큰이다
- `32 ~ 40px` : 4px 단위 (32, 36, 40)
- `40 ~ 80px` : 8px 단위 (48, 56, 64, 72, 80)
- `80 ~ 96px` : 16px 단위

즉 **"8의 배수만 쓴다"는 규칙은 틀렸다.** 작은 간격일수록 2px 단위로 촘촘하게 고를 수 있고,
큰 여백일수록 성기게 뛴다. 실제로 Chip의 세로 padding `7px`처럼 토큰 밖의 값도 존재하므로,
컴포넌트 내부 수치는 반드시 Dev Mode 실측을 따른다.

**쓰는 기준**
- 아이콘–텍스트 간격 `spacing-100`(4px)
- 컴포넌트 내부 좌우 padding `spacing-300`(12) ~ `spacing-400`(16)
- 카드 내부 padding `spacing-400`(16) ~ `spacing-600`(24)
- 리스트 아이템 사이 `spacing-300`(12) ~ `spacing-400`(16)
- 섹션 사이 `spacing-1000`(40) ~ `spacing-1600`(64)
- 아이콘 크기 자체는 `14px`(Small) / `16px`(Medium)

> 참고: JDS에 차세대 시맨틱 토큰 레이어가 만들어지는 중이다
> (`font-family-typeface-basic`, `font-size-350=14`, `line-height-500=20`, `font-weight-600`,
> `letter-spacing-normal`, `Typography/B2 14 semibold`). 현재 화면 작업은 기존
> `Heading/Body/Caption` 이름을 계속 쓰고, 이 토큰이 보이면 같은 값의 새 이름이라고 이해하면 된다.

## Grid

섹션 `889:7665` (Grid system). Desktop · Mobile 두 벌뿐이고 그 사이 브레이크포인트는 정의돼 있지 않다.

### Desktop — 12 컬럼

| 항목 | 값 |
|---|---|
| 기준 화면 폭 | **1920** (좌우 여백 360씩) |
| **Container** | **1200px** — 중앙 정렬 |
| Margin (Container 안쪽 좌우) | **8px** |
| **Contents** | **1184px** = 1200 − 8×2 |
| 컬럼 수 | **12** |
| Column | **84px** |
| Gutter | **16px** |

검산: `84×12 + 16×11 = 1008 + 176 = 1184` — Contents 폭과 정확히 맞는다.

**Container(1200) 와 Contents(1184) 는 다른 값이다.** 배경·구분선처럼 끝까지 가는 요소는 1200,
실제 콘텐츠가 놓이는 자리는 1184다. 이 8px 을 빼먹으면 3열 카드가 잘린다.

### Mobile — 4 컬럼

| 항목 | 값 |
|---|---|
| 기준 화면 폭 | **393** |
| Margin (좌우) | **16px** |
| Contents | **361px** = 393 − 16×2 |
| 컬럼 수 | **4** |
| Column | **78px** (라벨값) |
| Gutter | **16px** |

**주의** — 라벨은 `78px` 이지만 실제 컬럼 폭은 **78.25px** 이다.
`78×4 + 16×3 = 360` 으로 1px 이 비고, `78.25×4 + 16×3 = 361` 이라야 맞는다.
피그마 좌표(16 / 110 / 205 / 299)도 78.25 기준으로 찍혀 있다.
컬럼 폭을 고정값으로 박지 말고 **`flex:1` 이나 `1fr` 로 나누는 게 맞다.**

```css
/* Desktop */
.jds-container{max-width:1200px;margin:0 auto;padding:0 8px}   /* 안쪽이 1184 */
.jds-grid{display:grid;grid-template-columns:repeat(12,1fr);gap:16px}
/* Mobile */
@media (max-width:600px){
  .jds-container{max-width:393px;padding:0 16px}                /* 안쪽이 361 */
  .jds-grid{grid-template-columns:repeat(4,1fr)}
}
```

Gutter 는 데스크톱·모바일 **둘 다 16px** 로 같다. 바뀌는 건 컬럼 수와 좌우 Margin 이다.

## Components

### Chip Selector
컴포넌트셋 `1856:238`. `Type(Fill·Outlined) × Size(Small 32·Medium 36) × Select(On·Off)` = **8조합이 전부다.**
기본값은 `Fill` / `Small(32)` / `Select On`.

`emogi` 와 `arrow` 는 **변형 축이 아니라 불리언 프로퍼티**다 (둘 다 기본 on). 그래서 조합 수는 8이지
32가 아니다. (Large 사이즈는 삭제됨. 제거형 칩은 별도 컴포넌트 `Chip Removable`.)

공통: 텍스트 13px / lineHeight 20px, 아이콘 14px, 이모지 Small 14px·Medium 16px, 텍스트-요소 gap 4px.

| Type | Select | 배경 | 보더 | 텍스트 | radius | padding | height |
|---|---|---|---|---|---|---|---|
| Fill | On | Gray900 `#242628` | 없음 | White, 600 | 999px | 14px / 7px | 32 or 36 |
| Fill | Off | Gray50 `#f3f3f4` | 없음 | Gray900, 400 | 999px | 14px / 8px | 32 or 36 |
| Outlined | On | White | 1px Gray900 `#242628` | Gray900, 600 | 100px | 12px / 8px | 32 or 36 |
| Outlined | Off | White | 1px Gray100 `#e5e6e9` | Gray900, 400 | 100px | 12px / 8px | 32 or 36 |

**주의**
- Fill·On 은 세로 padding 이 **7px**(보더 없음 보정), Off 는 8px. 높이는 둘 다 같다
- **이모지는 `Fill` 에서만 그려진다.** `Outlined` 에는 이모지 슬롯 자체가 없어서 `emogi=true` 로 켜도 안 나온다
- 화살표는 `system-chevron-down` **14px**. 피그마 레이어 이름이 `system-chevron-left` 로 잘못 붙어 있으니
  이름만 보고 왼쪽 화살표를 넣으면 안 된다
- 마크업 구조가 Type 마다 다르다 — `Outlined` 는 안쪽에 flex row 를 한 겹 더 두고 바깥이 `flex-column` 이다.
  `Fill` 은 자식을 바로 나열한다. 결과는 같으니 구현할 땐 한 겹으로 만들어도 된다

### Chip Removable
컴포넌트셋 `2446:12026`. `Size(Small 32·Medium 36) × Theme(Primary·Secondary)` = **4조합**.
기본값은 `Small(32)` / `Secondary`.

Selector 와 달리 **Select 축도, 이모지도 없다.** 항상 `텍스트 + X 아이콘` 한 형태다.

| Theme | 배경 | 보더 | 텍스트 | 아이콘 |
|---|---|---|---|---|
| `Secondary` | White | 1px Gray100 `#e5e6e9` | Gray900 `#242628` | Gray900 |
| `Primary` | Gray900 `#242628` | 없음 | White | White |

| 항목 | 값 |
|---|---|
| height | **32** 또는 **36** |
| padding | `8px 12px` (Theme·Size 무관하게 동일) |
| radius | **100px** |
| gap | 4px |
| 텍스트 | `Body 4` **13 / 20 / Regular 400** — Selector 와 달리 선택 상태에서도 **굵어지지 않는다** |
| 아이콘 | `system-x` **14px** |

**주의**
- **텍스트가 항상 Regular 400 이다.** Chip Selector 의 On 상태(SemiBold 600)와 헷갈리면 안 된다
- 세로 padding 이 Theme 과 무관하게 **8px 고정**이다. Selector 의 Fill·On 7px 보정 같은 예외가 없다
- 여기도 X 아이콘 레이어 이름이 `system-chevron-left` 로 잘못 붙어 있다. 실제 에셋은 `system-x` 다

```html
<span class="jds-chip-rm jds-chip-rm--sm jds-chip-rm--secondary">텍스트<svg …system-x…/></span>
```

### Checkbox
노드 `1898:3260`(단독) / `3260:1846`(텍스트 결합) / 가이드 `2716:4585`.
축: `Type(Primary·Secondary) × State(Default·Selected·Disabled) × Size(Medium 20·Small 16)`.

**Primary — 사각 박스형.** radius 전부 `4px`, box-sizing border-box.

| State | Size | 박스 | 배경 | 보더 | 체크 아이콘 |
|---|---|---|---|---|---|
| Default | Medium(20) | 20×20 | 없음 | 1px Gray200 `#c5c7cc` | 없음 |
| Default | Small(16) | 16×16 | 없음 | 1px Gray200 | 없음 |
| Selected | Medium(20) | 20×20 | Green500 `#00c274` | 없음 | **16px** White |
| Selected | Small(16) | 16×16 | Green500 | 없음 | **12px** White |
| Disabled | Medium(20) | 20×20 | Gray100 `#e5e6e9` | 없음 | **16px** Gray30 `#f9f9fb` |
| Disabled | Small(16) | 16×16 | Gray100 | 없음 | **12px** Gray30 |

Disabled는 회색 박스에 체크가 **남아 있다** (Gray30으로 흐리게). 빈 회색 박스가 아니다.

**Secondary — 박스 없이 체크 아이콘만.** 배경·보더 없음. 아이콘이 곧 컴포넌트 크기.

| State | 크기 | 아이콘 색 |
|---|---|---|
| Selected | 20 또는 16 | Green500 `#00c274` |
| Default | 20 또는 16 | Gray200 `#c5c7cc` |
| Disabled | 20 또는 16 | Gray100 `#e5e6e9` |

**Checkbox_with_text** — `Icon Position: Left / Right` 축이 추가되어 24조합.

- 배치 `display:flex; gap:8px; align-items:flex-start`
- 컨트롤을 래퍼로 감싸 텍스트 **첫 줄의 세로 중앙**에 맞춘다 (여러 줄이어도 첫 줄 기준)

| Size | 래퍼 height | 래퍼 padding | 텍스트 | 색 |
|---|---|---|---|---|
| Medium(20) | 24px | `2px 0` | `Body 1` 16/24 | Gray900 `#242628` |
| Small(16) | 22px | `3px 0` | `Body 3` 14/22 | Gray900 |

래퍼 높이 = 텍스트 line-height와 동일. padding = (래퍼높이 − 박스크기) ÷ 2.
텍스트는 `flex:1; min-width:0`.

**래퍼는 반드시 `box-sizing:border-box` 다.** 피그마의 control height(24 / 22)는
상하 padding 을 **포함한** 값이다. `content-box` 로 두면 `24+2+2 = 28px` 이 되어

- 한 줄일 때: 래퍼(28) 가 라벨 line-height(24) 보다 커져서 **체크박스가 아래로 내려가 중앙이 어긋난다**
- 여러 줄일 때: 위쪽 정렬은 맞지만 박스 위아래 2px 여백이 사라진 것처럼 보인다

검산: Medium `2 + 20 + 2 = 24` = Body 1 line-height, Small `3 + 16 + 3 = 22` = Body 3 line-height.
**래퍼 높이와 라벨 line-height 가 같아야 한 줄에서 자동으로 세로 중앙이 맞는다** —
`align-items:center` 로 맞추는 게 아니라 높이를 같게 만들어서 맞추는 구조다.

**가이드 규칙** (`2716:4585`)
- 구조는 **Control**(체크박스) + **Label**(선택). 단독 사용도 정식이다.
- 체크박스 좌·우로 각각 **8px 여백**을 확보한다.
- 라벨이 길면 **2줄까지 권장, 최대 3줄까지** 노출한다.

### PC Header (GNB)
컴포넌트셋 `158:2190`, 섹션 `4091:6707`. 상태 4종: `default / login / scroll-guest / scroll-login`.

**뼈대**
- 바 높이 **56px** + 하단 1px 라인 `Gray100 #e5e6e9` = 총 57px. 배경 White
- 콘텐츠 **max-width 1200px 중앙 정렬** (1920 기준 좌우 padding 360px)
- 콘텐츠 영역 `display:flex; align-items:center; justify-content:space-between`

**좌측 — 로고 + 메뉴**
- `display:flex; gap:34px; align-items:flex-end; height:100%`
- 로고 **106×25**, `Green500 #00c274` 단색. 감싸는 칸 높이 38px
- 메뉴 아이템: 높이 **38px**, `flex-direction:column; gap:12px`
  - 텍스트 **15px / 24 / SemiBold(600)**, `Gray800 #323438`, 가운데 정렬
  - `active` 는 아래에 **2px 바**, `Green500 #00c274`, 폭 100%
  - 24(텍스트) + 12(gap) + 2(바) = 38 로 딱 맞는다
- 메뉴 6개: 기업 리뷰 / 채용 공고 / 연봉 / 잡플위키 / 커뮤니티 / 멤버십

**우측 — 검색 + 액션**
- `display:flex; gap:24px; align-items:center; padding:10px 0`
- **Search** `188×40`, bg `Gray50 #f3f3f4`, radius `999px`, padding `11px 16px`, 내부 gap 4px
  - placeholder "기업, 공고 검색" **14px / 22 / Regular**, `Gray300 #a4a6ad`
  - 아이콘 14px `#a4a6ad`
- **헤더 버튼** 높이 32 (max-h 32, min-w 32), padding `6px 10px`, radius `8px`, bg White, gap 4px
  - 텍스트 **13px / 20 / SemiBold**, `Gray500 #686a6d`
- 구분선 `1×13`, `Gray100 #e5e6e9`. 버튼 그룹 사이 gap 2px

**로그인 상태 우측**
- 터치 영역: 아이콘 16px + `padding:8px` = **32×32**. 알림(bell) · 글쓰기(edit), 아이콘 색 `#686a6d`
- 터치 영역끼리 gap `spacing-50`(2px), 아이콘군 gap `spacing-200`(8px), 구분선까지 gap `spacing-250`(10px)
- 프로필: `32×32`, bg `Gray30 #f9f9fb`, border 1px `Gray100`, radius **6px**, padding 8px, user 아이콘 14px
- 프로필 옆 chevron-down 14px `#a4a6ad`, gap 4px

**상태별 차이 — 스크롤하면 메뉴가 사라진다**

| state | 메뉴 6개 | 검색창 | 우측 |
|---|---|---|---|
| `default` | 노출 | 188×40 | 로그인 · 회원가입 · 기업 회원 서비스 |
| `login` | 노출 | 188×40 | 알림 · 글쓰기 · 프로필 · 기업 회원 서비스 |
| `scroll-guest` | **숨김** | **620×40** | default 와 동일 |
| `scroll-login` | **숨김** | **620×40** | login 과 동일 |

스크롤 시 좌측에는 로고만 남고, 검색창이 **188 → 620px** 로 확장된다.

**주의**
- 헤더 버튼의 좌우 padding 토큰이 `--unit-8` 인데 실제 값은 **10px** 이다. 이름과 값이 어긋나 있으니 8px로 착각하지 말 것.
- 가이드 노트: "우측 '기업 회원 서비스', '제휴 대학 서비스' 기능은 조건에 맞춰 동일하게 노출".
- 아이콘 터치 영역은 **아이콘 크기 + padding 8px** 로 만든다 (16px 아이콘 → 32×32).

### Mobile Header
**컴포넌트셋이 두 벌이다.** 성격이 달라서 서로 대체하지 않는다.

| 컴포넌트셋 | 노드 | 변형 | 쓰는 곳 |
|---|---|---|---|
| **Main bar** | `21:23114` (`21:23115`) | 1종 | 로고가 보이는 서비스 최상단 |
| **Nav bar** | `21:23096` | **4종** | 그 외 모든 화면 |

공통: 폭 **393**, 높이 **56**, 배경 White, 세로 padding **8px**.
터치 영역은 **아이콘 24 + padding 8 = 40×40**. `8 + 40 + 8 = 56` 으로 높이가 나온다.

> **PC 헤더와 터치 영역 크기가 다르다.** PC 는 아이콘 16 + padding 8 = **32×32**,
> 모바일은 아이콘 24 + padding 8 = **40×40**. 같은 규칙(아이콘+8)이지만 결과값이 다르다.

**Main bar** — `21:23115`

| 항목 | 값 |
|---|---|
| padding | `8px 20px` |
| gap | 16px |
| 로고 | `JP logo` **106×25** |
| 우측 | `Number of icons` **number=2** — `system-bell-line` · `system-menu` |

**Nav bar** — `21:23096`. 축은 `variant` 4종이고, `showBack` · `showIcon` · `title` 은
변형 축이 아니라 **불리언 프로퍼티**(전부 기본 on)다.

| variant | 좌우 padding | 타이틀 | 구성 |
|---|---|---|---|
| `Main` | `pl 16 / pr 10` | **Title 5** 22/30 Bold, 좌측 정렬 | 타이틀 + 아이콘 3개 (`search-line` · `bell-line` · `menu`) |
| `Sub/Icon1` | `px 10` | **Title 7** 18/26 Bold, **가운데** | 뒤로가기 + 타이틀 + `share` |
| `Sub/Icon2` | `px 10` | **Title 7** 18/26 Bold, **가운데** | 뒤로가기 + 타이틀 + `heart-line` · `share` |
| `Sub/Info` | `px 10` | **Title 7** 18/26 Bold, **가운데** | 뒤로가기 + 타이틀 + `help-circle-line` |

타이틀 색은 전부 `Gray900 #242628`, 넘치면 `text-ellipsis` 로 자른다.

**주의**
- **`Sub/Info` 의 우측 아이콘만 20px 다.** 나머지 아이콘은 전부 24px 이고,
  터치 영역은 `40×40` 으로 고정이라 아이콘만 작아진다
- **`Sub/Icon2` 의 뒤로가기 래퍼에 `padding-right: 40px` 이 붙어 있다.** 장식이 아니라
  **균형추**다. 오른쪽 아이콘이 2개(40+40=80)라, 왼쪽도 40+40 을 만들어야 타이틀이 화면 정중앙에 온다.
  이걸 빼면 타이틀이 왼쪽으로 밀린다
- 좌우 padding 이 셋 다 다르다 — Main bar `20`, Nav Main `16 / 10`, Sub `10`. 하나로 통일돼 있지 않다
- `Number of icons` 는 별도 컴포넌트이고 `number` 프로퍼티가 **2**(Main bar) / **3**(Nav Main) 이다
- 아이콘 레이어 이름이 **전부 `system-chevron-left`** 로 잘못 붙어 있다. 실제 에셋은
  bell / search / menu / share / heart / help-circle 이다. Chip 과 같은 함정이다

### Graphic — Icon / Emoji
- **Icon** `5:7147` — `system-` 310개 + `Brand-` 24개 = **334개**. 기본 아트보드 **24×24**
  (2026-09-04 전수 대조. 피그마 심볼 이름과 스킬 파일이 **양방향 차이 0**)
- **같은 이름의 심볼이 2개 있다** — `system-download` 가 `5:4308` 과 `5:4476` 로 따로 등록돼 있다.
  내용은 동일하다. 페이지를 통째로 내보내면 `system-download-1.svg` 가 하나 더 생기는 원인이다
- **인스턴스가 섞여 있다** — `system-bell-line`(`4118:4143`), `Brand-jobplanet-logo`(`16:8766`) 는
  심볼이 아니라 인스턴스가 하나씩 더 놓여 있다. 내보내면 `-1` 파일로 떨어지니 개수를 셀 때 빼야 한다.
  이 중 **로고 인스턴스는 `#323438` 회색 변형**이다 — 경로는 같고 fill 만 다르다.
  회색 워드마크가 필요하면 `Brand-jobplanet-logo.svg` 의 `#00C274` 를 `#323438` 로 바꿔 쓰면 된다
- **Emoji** `5:11482` — `emoji-` **128개**. 기본 아트보드 **32×32**, 다색 일러스트라 색을 바꾸지 않는다
  (2026-09-04 실측. `emoji-jp-reportcenter` `6063:14375` 가 추가되어 127 → 128)
- 둘 다 `size` 프로퍼티가 **12 · 14 · 16 · 18 · 20 · 22 · 24 · 28 · 32** 9단계로 동일하다
- 아이콘 색은 고정이 아니다. 쓰는 자리의 텍스트 색을 따른다 (헤더 기준 액션 `#686a6d`, 보조 `#a4a6ad`)
- `-line` / `-fill` 페어가 있는 아이콘은 짝을 맞춰 쓴다. 기본 `-line`, 활성·선택 `-fill`
- **삭제 예정** — 숨겨진 가이드 프레임(`3581:4216`, `3581:4217`, 둘 다 `hidden`)이 덮고 있는 아이콘만 해당한다.
  덮인 좌표를 실측해서 정확히 추린 목록이다 (2026-09-04):

  | 표시 | 대상 |
  |---|---|
  | 삭제할 것 | `system-check` · `system-check-20` · `system-checkbox-checked-line` · `system-checkbox-checked-fill` · `system-checkbox-unchecked` · `system-checkbox-multi-checked` · **`Brand-twitter`** |
  | 나중에 삭제할 것 | `system-radio-checked` · `system-radio-unchecked` |

  Checkbox·Radio 컴포넌트가 체크 표시를 자체적으로 그리므로 쓸 일이 없다.
  **`system-check-circle` `system-check-square` `system-radio`(방송 아이콘) 는 대상이 아니다** —
  가이드 사각형 밖에 있다. 이름이 비슷하다고 싸잡아 버리면 안 된다
- **네이밍 예외**: `emoji_headhunter` 만 언더스코어, `emoji-talkNaver` 만 카멜케이스.
  오타가 그대로 이름인 것 — `emoji-paperfoler` `emoji-checkture` `emoji-accout`
- **번호 붙이는 방식이 제각각**이다. `emoji-place2` · `emoji-heart02` · `emoji-resume-2` 세 가지가 공존한다
- **`emoji-jp-` 계열 6개** — `jp-community` `jp-explore` `jp-resume` `jp-apply` `jp-awards` `jp-reportcenter`.
  잡플래닛 서비스 진입점용이다. 잡코리아 로고는 `emoji-jk-logo` 로 접두사가 다르다
- **사용 보류는 2개다.** 페이지 맨 아래 "사용 보류" 라벨(`4712:470`) 밑에
  `emoji-like`(`4712:453`) 와 **`new` 뱃지**(`361:288`, 27.3×14.74) 가 놓여 있다.
  `emoji-like` 는 컴포넌트(`4712:334`) 로는 그리드에 그대로 남아 있으니, 목록에 보인다고 써도 되는 게 아니다

**실제 SVG 파일이 이 스킬 안에 있다.** 그림을 지어내지 말고 파일을 읽어서 인라인한다.

```
assets/icons/system-*.svg   310개  ← fill="currentColor" 로 변환해둠
assets/icons/Brand-*.svg     24개  ← 브랜드 색 그대로 유지
assets/emoji/emoji-*.svg    128개  ← 다색 일러스트, 색 변경 금지
```

쓰는 법:
1. `icons.md` 또는 `assets/icons/` 목록에서 이름을 고른다
2. 해당 `.svg` 파일을 읽어 마크업을 그대로 붙여넣는다
3. `width`/`height` 를 원하는 사이즈(12~32)로 바꾼다. viewBox 는 전부 `0 0 24 24` 이므로 건드리지 않는다
4. 색은 부모의 `color` 로 정해진다 (`currentColor`). 이모지는 색을 바꾸지 않는다

`emoji-gunbo` 하나만 SVG가 아니라 래스터 이미지다.

> 목록에 없는 이름을 지어내지 않는다. 필요한 아이콘이 없으면 없다고 말한다.

### Button
컴포넌트셋 `330:67443` (페이지 `406:14844`).
축: `theme(5) × state(4) × size(4) × Shape(2)` — 실제 존재하는 조합 **96개**.

**Shape 는 사실상 Quaternary 전용이다.** `Rounded` 80개(5 theme × 4 state × 4 size) +
`Pill` 16개(**Quaternary 만** × 4 state × 4 size). Primary·Secondary·Tertiary·Error 에는 Pill 이 없다.

**사이즈** — 글자는 전부 SemiBold 600.

| size | height / min-width | padding (세로/가로) | gap | radius | 글자 | 아이콘 |
|---|---|---|---|---|---|---|
| `x-small(32)` | 32 | 6 / 10 | 4 | **8** | `Heading 4` 13/20 | 14px |
| `Small(40)` | 40 | 9 / 12 | 4 | 10 | `Heading 3` 14/22 | 16px |
| `Medium(48)` | 48 | 12 / 14 | 6 | 10 | `Heading 1` 16/24 | 20px |
| `Large(52)` | 52 | 14 / 16 | 6 | 10 | `Heading 1` 16/24 | 20px |

`min-width` 가 높이와 같다 — 라벨이 짧아도 정사각형보다 작아지지 않는다.
x-small 만 radius 8 이고 나머지는 10 이다.

**Pill 은 radius = 높이 ÷ 2** — 32→16, 40→20, 48→24, 52→26. padding·gap 은 Rounded 와 같다
(단 `Small(40)` 만 세로 padding 이 Rounded 9 / Pill 10 으로 1px 다르다. 높이가 고정이라 결과는 같다).

**theme × state** (Medium(48) 기준, 색은 모든 사이즈 공통)

| theme | default | D-hover | disabled |
|---|---|---|---|
| `Primary` | bg `Green500 #00c274` · 글자 White | bg `Green600 #00a866` | bg `Gray200 #c5c7cc` · 글자 White |
| `Secondary` | bg `Gray50 #f3f3f4` · 글자 `Gray600 #57595b` | bg `Gray100 #e5e6e9` | bg `Gray100` · 글자 `Gray300 #a4a6ad` |
| `Tertiary` | bg White + 1px `Gray100` · 글자 `Green500` | bg `Gray30 #f9f9fb` · 글자 `Green600` | bg White + 보더 · 글자 `Gray200` |
| `Quaternary` | bg White + 1px `Gray100` · 글자 `Gray600` | bg `Gray30` · 글자 `Gray600` | bg White + 보더 · 글자 `Gray200` |
| `Error` | bg `Red500 #f44336` · 글자 White | bg `Red600 #e53935` | bg `Gray200` · 글자 White |

**disabled 처리가 theme 마다 다르다.** Primary·Error 는 배경을 Gray200 으로 덮고,
Secondary 는 Gray100, Tertiary·Quaternary 는 **배경·보더를 그대로 두고 글자만 Gray200** 으로 흐린다.

**loading** — 라벨이 사라지고 **정사각형**이 된다 (h = min-width = size).
배경은 default 와 같고 가운데에 `system-loader` 아이콘만 남는다. 아이콘 크기는 사이즈별 아이콘 크기와 동일.

**토큰 주의**
- `unit-8` 토큰 값이 **10** 이다 (이름과 불일치). 헤더 버튼에서도 같은 문제가 있었다
- `radius-sm` `radius-md` `radius-lg` 가 **전부 10** 으로 같은 값이다. 이름으로 구분해 쓰면 안 된다
- 세로 padding 이 `9` `12` `14` 처럼 Spacing 스케일에 없는 값도 쓴다. 버튼 내부 수치는 스케일이 아니라 이 표를 따른다

### ButtonText (텍스트 버튼)
컴포넌트셋 `1016:2962`. 축: `color(3) × size(3) × weight(2)` = **18조합**.
`variant` 은 `normal` 하나뿐이고, `leftIcon` · `rightIcon` 두 개의 on/off 프로퍼티가 따로 있다 (둘 다 기본 on).

배경·보더·padding·밑줄이 **전부 없다.** 글자와 아이콘만 있는 `inline-flex` 다.

**color — 글자색이 아니라 "놓이는 배경"을 가리킨다**

| color | 글자색 | 쓰는 곳 |
|---|---|---|
| `dark-bg` | `Gray300 #a4a6ad` | **어두운 배경 위** |
| `light-bg` | `Gray400 #85878c` | **밝은 배경 위** (일반 화면) |
| `Primary` | `Green500 #00c274` | 강조 |

이름을 반대로 읽기 쉽다. 흰 화면에 놓는 기본값은 `light-bg` 다.

**size**

| size | 글자 | 아이콘 | gap |
|---|---|---|---|
| `x-small(13)` | 13 / 20 | 14px | 4px |
| `small(14)` | 14 / 22 | 16px | 4px |
| `medium(16)` | 16 / 24 | 20px | **6px** |

**weight**
- `regular` = Pretendard Regular **400** (`Body 4/3/1`)
- `bold` = Pretendard **SemiBold 600** (`Heading 4/3/1`) — 이름은 bold 지만 **700 이 아니다**

`Primary` 는 Green **500** 을 쓴다. 태그가 500→600 으로 바뀐 규칙의 예외라고 업데이트 로그에 명시돼 있다
("Green-fill 과 Text Button 을 제외한 모든 태그 유형의 Text 색상 500 → 600").

### Divider
컴포넌트셋 `469:8873`. 축: `Type(Thin·Thick) × Color(Gray50·Gray100)` = **4조합**.
기본값은 `Thin` / `Gray50`.

| Type | 높이 | Color=Gray50 | Color=Gray100 |
|---|---|---|---|
| `Thin` | **1px** | `#f3f3f4` | `#e5e6e9` |
| `Thick` | **8px** | `#f3f3f4` | `#e5e6e9` |

**보더가 아니라 배경색으로 칠한 블록이다.** `border-top` 이 아니라 높이를 가진 `div` 에
`background` 를 넣는다. 폭은 부모를 꽉 채운다 (피그마의 361px 는 표본 폭일 뿐 규격이 아니다).

```html
<div class="jds-divider"></div>              <!-- Thin  / Gray50  -->
<div class="jds-divider jds-divider--g100"></div>
<div class="jds-divider jds-divider--thick"></div>
```

**주의**
- **세로 디바이더 변형은 없다.** 헤더의 `1×13` 구분선처럼 세로선이 필요하면 컴포넌트가 아니라 직접 그린 것이다
- Thick(8px) 은 섹션을 크게 끊을 때 쓰는 덩어리다. 얇은 선을 두껍게 한 게 아니라 별도 타입이다
- 색 고르는 기준은 Color 섹션 규칙을 따른다 — **디바이더 Gray50 / 보더 Gray100**, 섞어 쓰지 않는다.
  단 **Tab 디바이더만 예외로 Gray100** 이다 (2026-06-08 변경)

### Tab
컴포넌트셋 `895:925`. 축은 `Tab 개수(2~7) × Select(1~n)` 이고,
개수마다 선택 가능한 위치가 달라서 조합은 `2+3+4+5+6+7 = ` **27개**다.

**구조는 2층이다.**

```
flex-column
├─ 탭 줄        flex · gap 8px
│   └─ 탭 아이템  padding 14px 8px · Heading 1 16/24 SemiBold
└─ Divider      Thin · Gray100 · 폭 100%
```

| 상태 | 텍스트 색 | 인디케이터 |
|---|---|---|
| 선택 | **Gray800 `#323438`** | 아래 **2px** `Gray800` |
| 미선택 | **Gray200 `#c5c7cc`** | 없음 |

| 항목 | 값 |
|---|---|
| 탭 아이템 padding | `14px 8px` |
| 탭 사이 gap | **8px** |
| 탭 줄 높이 | **52px** (`14 + 24 + 14`) |
| Divider | **1px** `Gray100 #e5e6e9` (Divider 컴포넌트 `Thin`/`Gray100` 재사용) |
| 전체 높이 | **53px** (`52 + 1`) |

**폭은 `66n − 8`** 로 떨어진다 (n = 탭 개수). 2→124, 3→190, 4→256, 5→322, 6→388, 7→454.
`58n + 8(n−1)` 과 같은 값이다 — 즉 **탭 아이템은 고정 폭이 아니라 글자 폭에 맞춰 늘어난다.**
58px 은 "텍스트" 3글자일 때의 결과일 뿐이고, 탭을 같은 폭으로 균등 분할하지 않는다.

**주의**
- **인디케이터가 Green 이 아니라 `Gray800` 이다.** PC 헤더 GNB 의 active 바는 `Green500` 인데
  Tab 컴포넌트는 회색이다. 둘을 같은 것으로 보면 안 된다
- **미선택 텍스트가 `Gray200`** 이다. placeholder·disabled 에 쓰는 `Gray300` 이 아니라 그보다 더 옅다
- 선택 텍스트도 `Gray900` 이 아니라 **`Gray800`** 이다
- **2px 인디케이터는 아이템 "안쪽"에 그린다.** 피그마에서 inside stroke 라 아이템 높이가 52 로 유지된다.
  `border-bottom:2px` 로 만들면 높이가 54 가 되어 미선택 탭과 1~2px 어긋나고 전체가 밀린다.
  `position:absolute` 로 바닥에 깔거나 `::after` 로 그린다
- 콘텐츠가 디바이스 너비를 넘어도 **우측 그라데이션을 노출하지 않는다** (Updates 로그 결정)

```html
<div class="jds-tab">
  <div class="jds-tab__row">
    <button class="jds-tab__item is-on">텍스트</button>
    <button class="jds-tab__item">텍스트</button>
  </div>
  <div class="jds-divider jds-divider--g100"></div>
</div>
```

### 그 외 컴포넌트 — 스펙 미추출
`Icon Button`, `ButtonPagenationArrow`,
`Bottomsheet_btn`, `Modal`, `Modal.Footer`, `Emoji`, `텍스트 필드`, `태그`, `Radio`

이것들은 **실측값이 없다.** 화면에 필요하면 추측해서 그리되, 결과물에 "이 컴포넌트는 JDS 실측이 아니라
추정입니다"라고 명시하고, 아래 파생 규칙을 따른다:
- 보더 1px `Gray100`, 배경 White
- 텍스트 13px(`Heading 4`/`Body 4`) 또는 14px(`Heading 3`/`Body 3`)
- 세로 padding 8px 기준, 높이 32 / 36 / 40 / 48 중에서 선택
- 아이콘 14px 또는 16px, 텍스트와의 gap 4px

## 운영 규칙 (Updates 로그에서 확인된 최신 결정)

- **버튼 Shape**: `Rounded`(모서리 radius) / `Pill`(양 끝 완전 둥글게) 두 속성 존재.
- **Chip**: `Chip Selector`(default/selected/disabled) 와 `Chip Removable`(selected, X로 제거) 로 분리. Selector의 Large 사이즈 삭제됨.
- **텍스트 필드**: X 아이콘과 텍스트 간 마진 `4px`. 밸리데이션 텍스트는 `Caption 2` 적용.
- **Divider**: 컬러 타입에 Gray100 추가. **Tab 디바이더는 Gray50 → Gray100으로 변경됨.**
- **태그**: Green-fill 과 Text Button 을 제외한 모든 태그 유형의 텍스트 색상은 `500 → 600`.
- **Tab**: 콘텐츠가 디바이스 너비를 초과해도 우측 그라데이션을 **노출하지 않는다**.
- **Emoji**: 구 `Graphic` → `Emoji`로 통합. 기존 이모지 색상 블루 → 그린으로 변경.
  Graphic 페이지는 `Icon` 카드와 `emoji` 카드 두 개로 나뉘어 있고, 각 카드 우측의 size 리스트에서
  크기를 골라 쓰라고 안내문에 적혀 있다.

## 화면을 그릴 때

1. 위 팔레트/타이포 밖의 값을 쓰지 않는다.
2. 컴포넌트는 위 스펙 그대로. 없는 컴포넌트는 가장 가까운 스펙의 규칙(radius, padding 리듬, 보더 Gray100)을 따라 만든다.
3. 실제 서비스 문구를 쓴다. "텍스트", "제목" 같은 placeholder 금지.
4. 아이콘은 14px / 16px 기준.

---

## 이 스킬을 업데이트하는 법

새 컴포넌트를 추가하거나 기존 값을 고칠 때 **반드시 이 절차를 따른다.**
추측으로 채우면 이 스킬을 만든 이유가 사라진다.

**1. 노드 링크를 받는다**
피그마에서 컴포넌트셋을 선택하고 `Copy link to selection` 한 URL. 링크 없이 시작하지 않는다.

**2. Dev Mode 값을 읽는다** (스크린샷으로 눈대중하지 않는다)

| 도구 | 얻는 것 |
|---|---|
| `get_design_context` | Dev Mode Inspect — 실제 CSS 값 + 토큰 이름 |
| `get_variable_defs` | 변수 패널 — hex, 폰트 정의 |
| `get_metadata` | 레이어 트리 + 변형 축 + x/y/w/h |

응답이 커서 파일로 저장되면 (`... exceeds maximum allowed tokens`), 그 파일을 python/jq 로 파싱한다.
컴포넌트셋 전체를 한 번에 받아 파싱하는 쪽이 변형마다 호출하는 것보다 훨씬 싸다.

**3. 이름을 원본과 대조한다**
아이콘·이모지·변형 이름을 목록으로 만들었으면 **원본에서 뽑은 이름과 diff 해서 검증한다.**
과거에 `emoji-headhunter`, `emoji-papers-folder` 처럼 있을 법한 이름을 지어낸 적이 있다.

**4. 세 곳을 같이 고친다**
- `SKILL.md` — 스펙 표. 값과 함께 **왜 그런지**(예: Pill radius = 높이÷2) 를 적는다
- `reference.html` — 복붙용 CSS 클래스
- 검수 보드 — https://claude.ai/code/artifact/49f4529f-4ef6-42d5-9f39-5955fa9892c9
  (같은 파일 경로로 재발행하면 URL 유지. `url` 파라미터로도 갱신 가능)

**5. 이상한 값은 그대로 적고 경고를 붙인다**
고쳐서 적지 않는다. 지금까지 발견된 것:
`unit-8 = 10` · `radius-sm/md/lg 전부 10` · `weight=bold 가 SemiBold 600` ·
`emoji_headhunter` 만 언더스코어 · `emoji-talkNaver` 만 카멜케이스 ·
`emoji-paperfoler` `emoji-checkture` `emoji-accout` 오타가 이름 ·
`emoji-jp-reportcenter` 는 SVG 내부 `<g id>` 가 `emoji-clipboard` 로 잘못 붙어 있었다(내려받아 교정함) ·
`system-download` 심볼이 2개 · 삭제 예정 가이드가 `hidden` 이라 화면에선 안 보인다 ·
Chip 두 종 모두 아이콘 레이어 이름이 `system-chevron-left` 인데 실제 에셋은 chevron-down / x 다 ·
버튼 세로 padding `9` 는 Spacing 스케일에 없는 값

**6. 화면 규칙(R#) 은 유저만 정한다**
`## 화면 규칙` 항목은 유저가 말한 것만 적는다. 내가 판단해서 추가하지 않는다.
정해지지 않은 건 "정해진 기본값 없음" 으로 남기고 물어본다.

**주의** — 이미 열려 있는 다른 세션은 파일을 미리 읽어둔 상태라 이번 변경이 반영되지 않는다.
그 세션에서는 스킬을 다시 로드해야 한다.
