# GitHub Pages 배포 가이드

이 가이드는 Do Chung 포트폴리오 사이트를 GitHub Pages에 배포하는 방법을 설명합니다.

## 📋 사전 준비

- GitHub 계정 (없으면 [github.com](https://github.com)에서 생성)
- Git 설치 ([git-scm.com](https://git-scm.com))
- 이 프로젝트의 코드

## 🚀 배포 방법

### 1단계: GitHub에서 레포지토리 생성

**옵션 A: 개인 도메인 (username.github.io)**

1. GitHub에 로그인
2. 우측 상단 `+` → **New repository** 클릭
3. 레포지토리 이름: **`dochung.github.io`** (본인 username으로 변경)
   - 예: `john.github.io`, `alice.github.io`
4. **Public** 선택
5. **Create repository** 클릭

**옵션 B: 프로젝트 레포지토리 (username.github.io/repo-name)**

1. GitHub에 로그인
2. 우측 상상 `+` → **New repository** 클릭
3. 레포지토리 이름: **`do-chung-portfolio`** (원하는 이름)
4. **Public** 선택
5. **Create repository** 클릭
6. `vite.config.ts`에서 다음 수정:
   ```typescript
   const GITHUB_PAGES_BASE = process.env.GITHUB_PAGES_BASE || "/do-chung-portfolio/";
   ```

### 2단계: 로컬에서 Git 설정

터미널을 열고 프로젝트 디렉토리에서 다음 명령어 실행:

```bash
# 프로젝트 디렉토리로 이동
cd /home/ubuntu/do-chung-portfolio

# Git 초기화 (이미 되어있을 수 있음)
git init

# GitHub 레포지토리 추가
git remote add origin https://github.com/YOUR_USERNAME/dochung.github.io.git
# 또는 (프로젝트 레포의 경우)
git remote add origin https://github.com/YOUR_USERNAME/do-chung-portfolio.git

# 기본 브랜치를 main으로 설정
git branch -M main
```

### 3단계: 코드를 GitHub에 푸시

```bash
# 모든 파일 스테이징
git add .

# 커밋
git commit -m "Initial commit: Do Chung portfolio with i18n and GitHub API"

# GitHub에 푸시
git push -u origin main
```

### 4단계: GitHub Actions 자동 배포 설정

GitHub Actions 워크플로우가 이미 설정되어 있습니다 (`.github/workflows/deploy.yml`).

1. GitHub 레포지토리 페이지로 이동
2. **Settings** 탭 클릭
3. 좌측 메뉴에서 **Pages** 클릭
4. **Source** 섹션에서:
   - **Deploy from a branch** → **GitHub Actions** 선택
5. 저장

### 5단계: 배포 확인

1. GitHub 레포지토리의 **Actions** 탭 클릭
2. "Deploy to GitHub Pages" 워크플로우 실행 확인
3. 초록색 체크마크 ✅ 표시 = 배포 성공

### 6단계: 사이트 접속

배포 완료 후 다음 URL에서 사이트 확인:

**옵션 A (개인 도메인):**
```
https://dochung.github.io
```

**옵션 B (프로젝트 레포):**
```
https://YOUR_USERNAME.github.io/do-chung-portfolio
```

---

## 🔄 이후 업데이트 방법

코드를 수정한 후 배포하려면:

```bash
# 변경사항 스테이징
git add .

# 커밋
git commit -m "Update: [변경 내용 설명]"

# GitHub에 푸시
git push origin main
```

GitHub Actions가 자동으로 빌드 & 배포를 진행합니다. (약 1-2분 소요)

---

## 🆘 문제 해결

### Q: "Deploy to GitHub Pages" 워크플로우가 보이지 않습니다

**A:** `.github/workflows/deploy.yml` 파일이 `main` 브랜치에 있는지 확인하세요.

```bash
git status
git add .github/workflows/deploy.yml
git commit -m "Add GitHub Actions workflow"
git push origin main
```

### Q: 배포 후 사이트가 빈 페이지입니다

**A:** 다음을 확인하세요:

1. **GitHub Pages 설정 확인**
   - Settings → Pages → Source가 "GitHub Actions"로 설정되어 있는가?

2. **base 경로 확인**
   - 프로젝트 레포를 사용하는 경우, `vite.config.ts`의 `GITHUB_PAGES_BASE`가 올바른가?
   ```typescript
   const GITHUB_PAGES_BASE = "/do-chung-portfolio/";
   ```

3. **빌드 로그 확인**
   - Actions 탭에서 워크플로우 실행 로그 확인
   - 빨간색 ❌ 표시 = 빌드 실패

### Q: 스타일이 적용되지 않습니다

**A:** CSS 경로 문제일 수 있습니다. `vite.config.ts`의 `base` 설정을 확인하세요.

```typescript
export default defineConfig({
  base: GITHUB_PAGES_BASE, // "/" 또는 "/repo-name/"
  // ...
});
```

### Q: 라우팅이 작동하지 않습니다 (404 에러)

**A:** GitHub Pages는 SPA 라우팅을 지원하지 않습니다. 이 프로젝트는 이미 `404.html` 리다이렉트로 해결했습니다.

확인 방법:
- `client/public/404.html` 파일이 존재하는가?
- GitHub Pages 설정에서 "Enforce HTTPS" 활성화

---

## 📚 참고 자료

- [GitHub Pages 공식 문서](https://docs.github.com/en/pages)
- [GitHub Actions 공식 문서](https://docs.github.com/en/actions)
- [Vite 배포 가이드](https://vitejs.dev/guide/static-deploy.html#github-pages)

---

## 💡 팁

### 커스텀 도메인 연결 (선택사항)

GitHub Pages에 커스텀 도메인을 연결하려면:

1. 도메인 레지스트라에서 DNS 설정
2. GitHub 레포지토리 Settings → Pages → Custom domain
3. 도메인 입력 후 저장

### 자동 배포 확인

매번 푸시할 때마다 자동으로 배포되는지 확인:

```bash
# 작은 변경 후 푸시
echo "# Updated" >> README.md
git add README.md
git commit -m "Test deployment"
git push origin main

# GitHub Actions 탭에서 배포 진행 상황 확인
```

---

## 🎯 완료 체크리스트

- [ ] GitHub 레포지토리 생성
- [ ] 로컬 Git 설정 완료
- [ ] 코드 GitHub에 푸시
- [ ] GitHub Pages 설정 (Source: GitHub Actions)
- [ ] 첫 배포 성공 확인
- [ ] 사이트 접속 및 정상 작동 확인
- [ ] 블로그 글 작성 및 배포 테스트

모든 단계를 완료하면 `https://YOUR_USERNAME.github.io`에서 포트폴리오를 볼 수 있습니다! 🎉
