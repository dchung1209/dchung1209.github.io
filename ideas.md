# Do Chung 포트폴리오 & 블로그 — 디자인 아이디어

## 사용자 요구사항 요약
- 이름: Do Chung (정도영)
- 직업: ML Engineer / Data Scientist / Robotics Engineer
- 3학년 재학 중 엔지니어
- 밝은 톤, 그레이/따뜻한 크림 톤
- 블로그 기능: 티스토리/옵시디언 Vault 느낌
- 기술 스택 섹션 (Python, C++, C, PyTorch 등)

---

<response>
<probability>0.07</probability>
<text>

## Idea A — "Academic Notebook" (학술 노트북)

**Design Movement:** Swiss Typography + Academic Paper Aesthetic

**Core Principles:**
1. 종이 질감의 크림-화이트 배경으로 오프라인 노트북 느낌
2. 좌측 사이드바 고정 네비게이션 (Obsidian vault 구조)
3. 타이포그래피 중심 레이아웃 — 콘텐츠가 주인공
4. 기술 문서 스타일의 코드블록과 섹션 구분

**Color Philosophy:**
- Background: `#FAF8F5` (따뜻한 크림 오프화이트)
- Surface: `#F2EFE9` (페이퍼 그레이)
- Accent: `#C0392B` (학술 레드 — 중요 표시)
- Text: `#2C2C2C` (진한 차콜)
- Muted: `#8A8A8A`

**Layout Paradigm:**
- 좌측 고정 사이드바 (240px) + 우측 콘텐츠 영역
- 블로그 글 목록은 파일 트리처럼 카테고리별 접기/펼치기
- 홈은 "README.md" 스타일로 자기소개

**Signature Elements:**
1. 좌측 사이드바에 파일 트리 구조 네비게이션
2. 코드블록 스타일 기술 스택 배지
3. 마크다운 렌더링 시 학술 논문 스타일 타이포그래피

**Interaction Philosophy:**
- 클릭 시 부드러운 슬라이드 전환
- 사이드바 항목 hover 시 배경색 변화
- 코드 블록 복사 버튼

**Animation:**
- 페이지 전환: fade-in 0.2s ease
- 사이드바 아이템: hover 시 left border accent 나타남
- 스크롤 시 헤더 그림자 강화

**Typography System:**
- Heading: `Playfair Display` (세리프, 학술적)
- Body: `Source Serif 4` (가독성 좋은 세리프)
- Code: `JetBrains Mono`
- 크기 계층: 2.5rem / 1.75rem / 1.25rem / 1rem / 0.875rem

</text>
</response>

<response>
<probability>0.08</probability>
<text>

## Idea B — "Engineer's Logbook" (엔지니어 로그북) ← **선택됨**

**Design Movement:** Industrial Minimalism + Warm Editorial

**Core Principles:**
1. 따뜻한 그레이 (#F5F3EF) 배경 — 눈에 편안한 독서 환경
2. 비대칭 레이아웃 — 좌측 넓은 콘텐츠 + 우측 좁은 메타 정보
3. 엔지니어링 감성의 모노스페이스 강조 + 세리프 본문
4. 카드 기반 블로그 목록 (티스토리 느낌)

**Color Philosophy:**
- Background: `#F5F3EF` (따뜻한 그레이-크림)
- Surface: `#EDEAE3` (카드 배경)
- Primary Accent: `#3D5A80` (딥 스틸 블루 — 엔지니어링)
- Secondary: `#E07A5F` (테라코타 — 포인트)
- Text: `#1A1A2E` (딥 네이비 차콜)
- Muted: `#7A7A8A`

**Layout Paradigm:**
- 상단 수평 네비게이션 (얇고 깔끔)
- 홈: 좌측 60% Hero + 우측 40% 빠른 링크/최근 글
- 블로그: 2열 카드 그리드 + 좌측 카테고리 필터
- 글 상세: 넓은 본문 + 우측 TOC

**Signature Elements:**
1. 터미널 스타일 Hero 텍스트 타이핑 애니메이션
2. 기술 스택 육각형 배지 (로봇공학 느낌)
3. 블로그 카드에 코드 스니펫 미리보기

**Interaction Philosophy:**
- 버튼/카드 hover 시 미세한 위로 이동 (translateY -2px)
- 기술 배지 hover 시 툴팁으로 설명
- 블로그 카드 hover 시 accent 색상 border

**Animation:**
- Hero 타이핑 효과: 커서 깜빡임
- 섹션 진입: slide-up 0.4s ease-out
- 카드: stagger 0.1s delay per card

**Typography System:**
- Display: `Syne` (기하학적, 현대적)
- Body: `Lora` (따뜻한 세리프, 독서에 최적)
- Code/Mono: `JetBrains Mono`
- 크기: 3rem / 2rem / 1.5rem / 1rem / 0.875rem

</text>
</response>

<response>
<probability>0.06</probability>
<text>

## Idea C — "Research Terminal" (리서치 터미널)

**Design Movement:** Neo-Brutalism + Academic

**Core Principles:**
1. 강한 보더와 그림자로 요소 구분
2. 그리드 기반 비대칭 레이아웃
3. 타이포그래피 크기 대비로 계층 표현
4. 기능 중심의 미니멀리즘

**Color Philosophy:**
- Background: `#FFFDF7` (아이보리)
- Accent: `#000000` (순수 블랙 보더)
- Highlight: `#FFD166` (네오브루탈 옐로우)
- Text: `#111111`

**Layout Paradigm:**
- 전체 화면 그리드 (12열)
- 섹션마다 다른 컬럼 스팬
- 헤더: 좌측 로고 + 우측 네비

**Signature Elements:**
1. 두꺼운 블랙 보더 카드
2. 오프셋 그림자 (box-shadow: 4px 4px 0 black)
3. 형광 하이라이트 강조

**Interaction Philosophy:**
- 클릭 시 오프셋 그림자 줄어드는 효과 (눌리는 느낌)
- 강한 hover 색상 반전

**Animation:**
- 빠른 전환, 0.15s
- 슬라이드 인 from left

**Typography System:**
- Display: `Space Grotesk` (기하학적 산세리프)
- Body: `IBM Plex Serif`
- Code: `IBM Plex Mono`

</text>
</response>

---

## 최종 선택: **Idea B — "Engineer's Logbook"**

따뜻한 그레이-크림 배경, 딥 스틸 블루 + 테라코타 포인트 컬러, Syne + Lora 타이포그래피 조합으로 엔지니어링 감성과 독서 친화적 블로그를 동시에 구현합니다.
