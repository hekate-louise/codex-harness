# 업무 도구 디자인 기준

SK 계열 공개 사이트와 CI 공개 자료를 참고해, **사내 업무 도구처럼 담백한 화면**을 빠르게 만들기 위한 기준이다. 과제 README와 업무 담당자의 요구가 이 문서보다 우선한다.

## 0. 먼저 지킬 것
- **로고, 심볼, 회사 이름 표기를 넣지 않는다.** 상표이고, 화면이 회사 공식 서비스처럼 보이면 안 된다. 이 문서는 색과 분위기만 참고한다.
- **화면이 열릴 때 외부 글꼴·CDN을 불러오지 않는다.** 결과물을 쓰는 환경은 오프라인일 수 있다.
- 디자인은 Must가 끝난 뒤, **15분 한도**. 업무 로직은 건드리지 않는다.
- 바꿀 점을 먼저 3~5개로 보여 주고 사용자가 고른 것만 적용한다.

## 1. 색
### 공식 CI 색 (SK하이닉스 CI 페이지 공개 값)
| 이름 | HEX | RGB | 쓰는 곳 |
|---|---|---|---|
| SK Red | `#EA002C` | 234 / 0 / 44 | 가장 중요한 강조 1가지 (주 버튼, 위험·오류·Hold) |
| SK Orange | `#F47725` | 255 / 122 / 0 | 두 번째 강조 (주의, 보조 링크) |
| SK Navy | `#0E306D` | 14 / 48 / 109 | 진한 제목 배경이 필요할 때 |
| SK Blue | `#0072C6` | 0 / 114 / 198 | 정보, 링크, 감소 수치 |
| SK Teal | `#009A93` | 0 / 154 / 147 | 정상·완료 표시 |

공식 페이지의 HEX와 RGB가 일부 다르다 (Orange: RGB로 계산하면 `#FF7A00`). 화면에는 **HEX 값**을 쓴다. Yellow·Green·Purple은 업무 화면에서 쓰지 않는다.

### 실제 사이트에서 쓰는 무채색 (2026-11-03 브라우저로 확인)
| 용도 | 값 | 확인한 곳 |
|---|---|---|
| 제목 글자 | `#212121` (거의 검정) | SK하이닉스 소제목 |
| 본문 글자 | `#666666` | SK하이닉스 본문 |
| 보조 글자 | `#999999` | 공통 |
| 테두리·구분선 | `#E5E5E5` | SK하이닉스 상자 테두리 |
| 옅은 배경 | `#F6F6F6` / `#F2F2F2` | 뉴스룸 |
| 배경 | `#FFFFFF` | 기업 사이트 (뉴스룸은 검정 배경이지만 업무 도구에는 흰 배경) |

### 색 사용 원칙
- **흰 바탕 + 검정·회색 글자가 90% 이상.** 빨강·주황은 점처럼 쓴다. SK 사이트에서도 빨강은 주 버튼과 아이콘 정도에만 나온다.
- 상태 색은 의미를 하나로 고정한다: **빨강 = 조치 필요(Hold, 오류)**, **주황 = 주의**, **청록 = 정상·완료**, **파랑 = 정보**.
- 색만으로 구분하지 않는다. 항상 글자 라벨을 같이 쓴다 ("Hold", "주의").

## 2. 글꼴
| 사이트 | 확인한 글꼴 |
|---|---|
| SK그룹 (sk.com) | Noto Sans KR, 맑은 고딕, Roboto |
| SK하이닉스 (skhynix.com) | Roboto, Noto Sans KR |
| SK하이닉스 뉴스룸 | Pretendard, Poppins (영문 제목) |

공식 그룹 전용 서체는 공개 자료에서 확인되지 않았다. 아래 목록은 **보는 PC에 설치된 첫 번째 글꼴**을 쓴다. 일반 Windows PC에서는 맑은 고딕으로 보인다.

Pretendard로 고정하려면 작업 중에 공개 글꼴(SIL OFL) Regular·Bold woff2 두 개와 라이선스 파일을 `fonts/`에 받아 `@font-face`로 연결하고, 출처를 DECISIONS.md에 적는다. 5분 안에 안 되면 포기한다.
```css
font-family: Pretendard, "Noto Sans KR", "Malgun Gothic", "Apple SD Gothic Neo", system-ui, sans-serif;
```
| 용도 | 크기 / 굵기 | 참고 |
|---|---|---|
| 페이지 제목 | 28~32px / 700, 자간 -0.02em | SK하이닉스 페이지 제목 |
| 구역 제목 | 20~24px / 700 | SK하이닉스 소제목 24px |
| 본문 | 15~16px / 400, 줄 간격 1.5 | 공통 16px |
| 표·보조 | 13~14px | |
| 큰 숫자(요약 지표) | 32~40px / 700 | SK하이닉스 주가 화면 |

숫자는 `font-variant-numeric: tabular-nums;`로 자릿수를 맞춘다.

## 3. 배치
- 내용 최대 폭 **1240px**, 가운데 정렬 (SK하이닉스 본문 폭). 좌우 여백 24px 이상
- 위에서 아래로: **얇은 상단 바(서비스 이름 글자만) → 위치 표시(Home > 메뉴) → 큰 페이지 제목 → 요약 지표 → 표·목록**
- 구역 사이 여백은 넉넉하게 (48~64px). 꾸밈 대신 여백으로 구분
- 모서리는 **0~3px** (SK 사이트는 대부분 0, 버튼 정도만 3px). 그림자는 쓰지 않거나 아주 약하게

## 4. 화면 부품
| 부품 | 모양 |
|---|---|
| 주 버튼 | SK Red 배경, 흰 글자, 모서리 0~3px, 높이 44px. **화면에 하나만** |
| 보조 버튼 | 흰 배경, `#E5E5E5` 테두리, 검정 글자 |
| 표 | 머리줄: 위쪽 2px 진한 선(`#212121`) + 연회색 배경. 행 구분: 1px `#E5E5E5`. 글자 13~14px, 칸 안쪽 여백 위아래 8px로 **촘촘하게**. 숫자는 오른쪽 정렬 |
| 요약 지표 판 | 현업이 요청했거나 판단에 꼭 필요할 때만. 위쪽 진한 선 + 칸 사이 세로 구분선 |
| 상태 라벨 | **조치가 필요한 상태에만** 작은 글자 + 옅은 배경. 정상은 라벨 없이 글자만 |
| 입력칸 | 1px 테두리, 높이 44px, 초점일 때 테두리를 SK Red로 |
| 탭 | 글자 탭, 선택된 탭 아래 2px 선 |
| 오류·경고 문구 | 입력칸 바로 아래 빨강 글자 한 줄, 무엇을 하면 되는지 함께 |

### 로그인 화면
- 흰 배경 가운데 폭 400px 상자, 테두리 `#E5E5E5`
- 위에서부터: 서비스 이름(글자) → 아이디 → 비밀번호 → 주 버튼(로그인) 하나
- 실패 문구는 버튼 위에 한 줄: "아이디 또는 비밀번호가 맞지 않습니다"
- 역할(운영자·사용자)이 있으면 로그인 후 상단 바 오른쪽에 "이름 · 역할 · 로그아웃"

### 운영자 / 사용자 화면
- 같은 틀(상단 바, 제목, 표)을 쓰고 **메뉴만 다르게**
- 운영자 화면 제목 옆에 작은 "운영자" 라벨로 구분

## 5. 하지 말 것 ("AI가 만든 티"가 나는 것들)
- 그라데이션 배경, 유리 효과, 네온 색
- 둥글고 그림자 큰 카드를 빽빽하게 나열
- 이모지 아이콘, 큰 일러스트
- 빨강·주황을 넓은 면적에 칠하기
- 의미 없는 색 여러 개 (상태 색 4가지 외에 추가하지 않기)

색과 글꼴을 지켜도 **구성** 때문에 AI 티가 난다. 아래 구성도 피한다.
- 제목마다 붙는 설명 문장 ("여유 있게 도착하세요", "수정할 항목을 선택하세요"). 쓰는 사람은 업무를 이미 안다
- 회색 안내 띠, 서비스 소개 말투 ("둘러보기", "확인하세요")
- 요구 없이 습관적으로 넣는 숫자 요약 4칸
- 모든 행에 색 라벨, 모든 구역에 같은 크기의 제목과 같은 여백
- 넉넉하기만 한 여백과 큰 글자. 실제 업무 화면은 한 화면에 더 많은 정보를 보여 준다
- `Lorem`처럼 티 나는 예시 값. 예시 데이터는 업무에 맞는 이름을 쓰되, 예시라는 표시는 화면이 아니라 문서에 남긴다 (과제가 요구하면 화면에도 표시)

## 6. CSS 시작값
```css
:root {
  --sk-red: #EA002C;
  --sk-orange: #F47725;
  --sk-blue: #0072C6;
  --sk-teal: #009A93;
  --sk-navy: #0E306D;
  --text: #212121;
  --text-body: #666666;
  --text-sub: #999999;
  --line: #E5E5E5;
  --bg-soft: #F6F6F6;
  --bg: #FFFFFF;
  --radius: 2px;
  --max: 1240px;
  --font: Pretendard, "Noto Sans KR", "Malgun Gothic", "Apple SD Gothic Neo", system-ui, sans-serif;
}
body { margin: 0; background: var(--bg); color: var(--text-body); font: 16px/1.5 var(--font); }
h1, h2, h3 { color: var(--text); letter-spacing: -0.02em; }
.wrap { max-width: var(--max); margin: 0 auto; padding: 0 24px; }
.btn-primary { background: var(--sk-red); color: #fff; border: 0; border-radius: var(--radius); height: 44px; padding: 0 20px; font-weight: 700; }
.btn { background: #fff; color: var(--text); border: 1px solid var(--line); border-radius: var(--radius); height: 44px; padding: 0 20px; }
table { width: 100%; border-collapse: collapse; border-top: 2px solid var(--text); }
th { background: var(--bg-soft); color: var(--text); font-weight: 700; }
th, td { padding: 8px 12px; border-bottom: 1px solid var(--line); font-size: 14px; }
td.num { text-align: right; font-variant-numeric: tabular-nums; }
.tag-hold { color: var(--sk-red); background: rgba(234, 0, 44, .08); }
.tag-warn { color: var(--sk-orange); background: rgba(244, 119, 37, .10); }
.tag-ok { color: var(--sk-teal); background: rgba(0, 154, 147, .08); }
```

## 7. 확인하지 못한 것
- SK그룹 공식 전용 서체 이름과 배포 여부 (공개 자료에서 찾지 못함)
- 공식 CI의 배경·금지 사용 예시 (이미지로만 제공되어 확인 불가)
- SK 계열 앱 화면 (앱은 브라우저로 확인할 수 없어 조사하지 않음)

## 출처
- [SK하이닉스 CI 페이지](https://www.skhynix.com/company/UI-FR-CP0402/): 주조색·보조색 값, 로고 여백 규칙
- [SK CI 페이지](https://www.sk.co.kr/ko/about/ci.jsp): SK Red·Orange 값과 CMYK
- [SK텔레콤 CI/BI](https://www.sktelecom.com/view/introduce/brand.do): 색의 의미
- [SK렌터카 CI 매뉴얼](https://company.skcarrental.com/kr/promotion/ci.html): 화면에는 RGB, 흰 배경 원칙
- 브라우저로 직접 확인 (2026-11-03): [sk.com](https://www.sk.com/), [skhynix.com](https://www.skhynix.com/), [SK하이닉스 주가정보](https://www.skhynix.com/ir/UI-FR-IR02), [SK하이닉스 뉴스룸](https://news.skhynix.co.kr/)
