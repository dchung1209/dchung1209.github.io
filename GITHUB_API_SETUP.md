# GitHub API 연동 설정 가이드

## 개요

Do Chung 포트폴리오 사이트는 GitHub API를 통해 실시간으로 레포지토리 데이터를 불러와 홈페이지의 "Featured Projects" 섹션에 표시합니다.

## 작동 원리

1. **자동 필터링**: `dochung` 계정의 모든 공개 레포 중에서 특정 토픽을 가진 것만 선택
2. **정렬**: 스타 수 (내림차순) → 최근 업데이트 (내림차순)
3. **표시**: 상위 3개 레포를 홈페이지에 카드 형태로 표시

## 포트폴리오 토픽 목록

다음 토픽 중 **최소 1개 이상**을 레포에 추가하면 자동으로 표시됩니다:

- `machine-learning` — 머신러닝 프로젝트
- `ml` — ML 관련 (약자)
- `robotics` — 로보틱스 프로젝트
- `data-science` — 데이터 사이언스
- `pytorch` — PyTorch 사용
- `ros2` — ROS2 사용
- `deep-learning` — 딥러닝
- `portfolio` — 포트폴리오용

## GitHub에서 토픽 추가하는 방법

### 1단계: 레포지토리 설정 열기
- GitHub에서 레포지토리 페이지 이동
- 상단 **Settings** 탭 클릭

### 2단계: Topics 섹션 찾기
- Settings 페이지에서 **About** 섹션 (우측 상단)
- "Edit" 버튼 클릭

### 3단계: 토픽 추가
- **Topics** 입력 필드에 위의 토픽 중 하나 이상 입력
- 예: `machine-learning`, `pytorch`, `robotics`
- **Save changes** 클릭

### 4단계: 포트폴리오 사이트 새로고침
- 포트폴리오 사이트를 새로고침하면 자동으로 업데이트됩니다
- (캐시 때문에 몇 초 지연될 수 있음)

## 예시

### 좋은 예
```
Topics: machine-learning, pytorch, deep-learning
```
→ 포트폴리오에 표시됨 ✅

### 나쁜 예
```
Topics: awesome, cool, my-project
```
→ 포트폴리오에 표시 안 됨 ❌

## API 상세 정보

### 엔드포인트
```
GET https://api.github.com/users/dochung/repos?type=public&sort=updated&per_page=100
```

### 필터링 로직
```typescript
// client/src/lib/github.ts에서 정의
const PORTFOLIO_TOPICS = [
  'machine-learning', 'ml', 'robotics', 'data-science',
  'pytorch', 'ros2', 'deep-learning', 'portfolio'
];

// 토픽 중 하나라도 포함하면 표시
repos.filter(repo =>
  repo.topics.some(topic =>
    PORTFOLIO_TOPICS.includes(topic.toLowerCase())
  )
);
```

### 표시되는 정보
- 레포 이름
- 설명
- 프로그래밍 언어 (색상 코드)
- 스타 수 ⭐
- 포크 수 🔀
- 마지막 업데이트 시간
- 토픽 태그 (최대 3개)

## 문제 해결

### Q: 새로 추가한 레포가 표시되지 않습니다
**A:** 다음을 확인하세요:
1. 레포가 **공개(Public)**로 설정되어 있는가?
2. 포트폴리오 토픽 중 **최소 1개**가 추가되어 있는가?
3. 포트폴리오 사이트를 **새로고침**했는가?
4. 5분 정도 기다려본다 (API 캐시 때문)

### Q: 특정 레포를 숨기고 싶습니다
**A:** 두 가지 방법:
1. 레포를 **Private**으로 변경 (공개하고 싶지 않은 경우)
2. 모든 포트폴리오 토픽 제거 (공개는 유지하되 포트폴리오에서만 숨김)

### Q: 토픽을 수정했는데 반영이 안 됩니다
**A:** 
1. 포트폴리오 사이트 **강력 새로고침** (Ctrl+Shift+R 또는 Cmd+Shift+R)
2. 브라우저 캐시 삭제
3. 개발자 도구 → Network 탭에서 API 요청 확인

## 커스터마이징

토픽 목록을 변경하려면:

```typescript
// client/src/lib/github.ts, 약 15줄
const PORTFOLIO_TOPICS = [
  'your-topic-1',
  'your-topic-2',
  // ... 원하는 토픽 추가
];
```

수정 후 사이트를 다시 빌드하면 적용됩니다.

## 보안 고려사항

- **인증 불필요**: 공개 API 사용으로 GitHub 토큰 필요 없음
- **Rate Limiting**: 시간당 60개 요청 제한 (충분함)
- **개인정보**: 공개 레포 정보만 표시

## 참고 자료

- [GitHub API 문서](https://docs.github.com/en/rest)
- [Topics 추가 가이드](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/classifying-your-repository-with-topics)
