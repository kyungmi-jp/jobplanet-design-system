# 잡플래닛 디자인시스템 (JDS 1.0)

피그마 `JDS 1.0` 파일의 **Dev Mode 실측값**을 코드와 문서로 옮겨둔 곳이다.
눈대중이 아니라 실제 수치를 옮기는 것이 목적이라, 추측으로 채운 값은 문서에 **"추정"** 이라고 표시한다.

- 피그마 파일: `JDS 1.0` — fileKey `c9OwXAPlMJ9YKVDF9ox7O2`
- 검수 벤치(브라우저 실측 ↔ Dev Mode 대조): [`docs/index.html`](docs/index.html)

## 무엇이 들어 있나

| 경로 | 내용 |
|---|---|
| `tokens/jds.css` | 복붙해서 바로 쓰는 CSS — 토큰(`:root`) + 타이포 클래스 + 컴포넌트 클래스 |
| `docs/spec.md` | 실측 스펙 전문. 컴포넌트별 수치와 **함정**까지 |
| `docs/index.html` | 검수 벤치. 이 CSS로 실제 렌더하고 브라우저가 잰 값을 Dev Mode 값과 대조한다 |
| `docs/reference.html` | 토큰·타이포·컴포넌트를 한 페이지로 훑어보는 문서 |
| `docs/icons.md` | 아이콘 이름 목록 |
| `assets/icons/` | 아이콘 **334개** (`system-` 310 + `Brand-` 24) SVG 원본 |
| `assets/emoji/` | 이모지 **128개** SVG 원본 |

## 쓰는 법

### 웹에서

```html
<!-- Pretendard 먼저 -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/orioncactus/pretendard@v1.3.9/dist/web/static/pretendard.css">
<link rel="stylesheet" href="tokens/jds.css">

<button class="jds-btn jds-btn--primary jds-btn--md">지원하기</button>
<span class="jds-chip jds-chip--fill jds-chip--sm is-on">최신순</span>
```

### 아이콘

`assets/icons/` 의 SVG를 **파일에서 읽어 그대로 인라인**한다. 목록에 없는 이름을 지어내지 않는다.

- `system-*.svg` 는 `fill="currentColor"` 로 변환돼 있어 부모의 `color` 를 따라간다
- `Brand-*.svg` 는 브랜드 색을 그대로 둔다
- `assets/emoji/*.svg` 는 다색 일러스트라 **색을 바꾸지 않는다**

## 지켜야 할 것

1. **팔레트 밖의 색을 쓰지 않는다.** 임의의 hex 금지
2. **폰트는 Pretendard.** 웨이트는 400 / 500 / 600 / 700 네 종류만
3. **한글 본문은 `word-break: keep-all`** — 단어 중간에서 끊기면 안 된다
4. 기본 텍스트 `Gray800 #323438`, 보더 `Gray100 #e5e6e9`, 디바이더 `Gray50 #f3f3f4`.
   **보더와 디바이더를 섞어 쓰지 않는다**
5. 스펙에 없는 값이 필요하면 지어내지 말고 **피그마 노드를 열어 실측**한다

## 자주 걸리는 함정

`docs/spec.md` 에 전부 적혀 있지만, 특히 많이 틀리는 것들이다.

- **Container 1200 ≠ Contents 1184** — 좌우 마진 8px 을 빼먹으면 3열 카드가 잘린다
- **Checkbox 라벨 래퍼는 `box-sizing: border-box`** — `content-box` 면 24+2+2=28 이 되어 세로 중앙이 어긋난다
- **Tab 인디케이터는 Green 이 아니라 `Gray800`** — 초록 밑줄은 PC 헤더 GNB 쪽이다
- **Chip Selector 는 8조합이 전부다** — `emogi` · `arrow` 는 변형 축이 아니라 불리언 프로퍼티
- **모바일 터치영역 40×40, PC 는 32×32** — "아이콘 + padding 8" 규칙은 같은데 결과가 다르다
- **아이콘 레이어 이름을 믿지 말 것** — 피그마에서 여러 아이콘의 레이어명이 `system-chevron-left` 로
  잘못 붙어 있다. 실제 에셋은 chevron-down / x / share / heart 등이다
- **`radius-sm` `radius-md` `radius-lg` 가 전부 10** 으로 같은 값이다. 이름으로 구분해 쓰면 안 된다
- **토큰 `unit-8` 의 실제 값은 10** 이다

## 고칠 때

값을 바꾸려면 **반드시 피그마 노드를 열어 Dev Mode 값을 확인하고** 고친다. 스크린샷 눈대중 금지.

1. 피그마에서 컴포넌트셋을 선택 → `Copy link to selection`
2. Dev Mode 값 확인
3. `tokens/jds.css` · `docs/spec.md` · `docs/index.html` **세 곳을 같이** 고친다
4. `CHANGELOG.md` 에 무엇이 어떻게 바뀌었는지 남긴다
5. PR 로 올린다

이상한 값을 발견하면 **고쳐서 적지 말고 그대로 적은 뒤 경고를 붙인다.** 피그마가 원본이다.

## 아직 안 채운 것

`Shadow` · `Modal` · `Bottomsheet` · `텍스트 필드` · `태그` · `Radio` · `Icon Button` ·
`ButtonPagenationArrow` 는 스펙 미추출 상태다. 노드 링크가 생기면 채운다.
