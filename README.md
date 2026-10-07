# Lighter 지원·약관 사이트

App Store 심사에 필요한 **지원 URL**, **개인정보 처리방침 URL**, **계정 삭제 안내**를 GitHub Pages로 무료 호스팅하는 정적 사이트예요. 빌드 과정 없이 HTML 파일 그대로 올리면 됩니다.

게시 후 주소: `https://kylo2084.github.io/lighter/`

## 파일 구성

| 파일 | 내용 |
|---|---|
| `index.html` | 소개 페이지 (마케팅 URL) |
| `support.html` | 고객지원 — 문의 메일, 자주 묻는 질문 10개, 운영자 정보 (지원 URL) |
| `terms.html` | 서비스 이용약관 |
| `privacy.html` | 개인정보 처리방침 (개인정보 처리방침 URL) |
| `location.html` | 위치기반서비스 이용약관 |
| `delete-account.html` | 계정 삭제 안내 — 앱에서 삭제하는 방법, 이메일 요청, 삭제·보관 정보 |
| `s/index.html` | 위치 공유 링크(`/s/?id=…`)가 이 사이트로 열렸을 때 보여주는 안내 |
| `404.html` | 없는 주소 안내. `/lighter/s/<id>` 형태의 주소는 `s/?id=<id>`로 자동 이동 |
| `assets/style.css` | 공통 스타일 (라이트/다크 자동 전환) |
| `assets/icon.png` 외 | 앱 아이콘, 파비콘(`favicon.ico`, `favicon-32.png`), 홈 화면 아이콘(`apple-touch-icon.png`, 180px) |
| `.nojekyll` | GitHub Pages가 Jekyll 변환 없이 파일을 그대로 내보내도록 하는 빈 파일 |

약관 3종(`terms`·`privacy`·`location`)은 `Lighter_AI_Handoff/legal/01~03` 초안을 문구 그대로 HTML로 옮긴 것이에요. 상단의 "초안 / 변호사 검토 전" 안내는 공개 페이지에서 뺐습니다.

## 공개 전에 꼭 채울 것 (■ 표시)

빈칸은 모두 `■`로 표시되어 있고 화면에서도 노란 배경으로 보여요. 아래 명령으로 남은 빈칸을 찾을 수 있어요.

```bash
grep -rn "■" --include=*.html .
```

| 항목 | 들어 있는 파일 |
|---|---|
| 시행일 (YYYY년 MM월 DD일) | `terms.html`, `privacy.html`(시행일·제15조·버전 표), `location.html` — 각 페이지 상단 배지와 부칙 |
| 통신판매업 신고번호 | `terms.html`(사업자 정보), `support.html`(운영자 정보), 모든 페이지 하단 푸터 |
| 사업장 주소 | `terms.html`, `location.html`(제16조), `support.html`, 모든 페이지 하단 푸터 |
| 위치기반서비스사업 신고번호 | `terms.html`, `location.html`(제16조), `support.html` |
| 고객센터 전화번호 | `location.html`(제16조), `support.html` |
| 개인정보 보호책임자 성명·직위 | `terms.html`, `privacy.html`(제13조), `support.html` |
| 개인정보 열람청구 접수·처리 부서 | `privacy.html`(제13조) |
| 위치정보관리책임자 성명·소속·직위 | `privacy.html`(제7조 7항), `location.html`(제16조), `support.html` |
| 본인확인기관/본인인증 대행사 이름 | `privacy.html`(제5조) |
| 지도·타일 제공 사업자 이름 | `privacy.html`(제5조, 제7조 5항) |
| 고객 문의 처리 도구(사용 시) | `privacy.html`(제5조) — 쓰지 않으면 행을 지우세요 |
| 국외 이전 연락처 (Google, RevenueCat) | `privacy.html`(제6조 표) |

푸터는 모든 HTML 파일 맨 아래 `<footer class="site-footer">` 안에 같은 내용으로 들어 있어요. 값을 바꿀 때는 8개 HTML 파일(`s/index.html`, `404.html` 포함)을 모두 고쳐주세요.

> 약관을 고치면 앱 안의 약관(`src/features/legal/docs.ts`)도 같은 문구로 맞춰야 해요. 지금은 두 곳의 본문이 완전히 같습니다.

## GitHub Pages에 올리기

### 1. 저장소 만들기

1. <https://github.com/new> 에서 **Repository name**에 `lighter`를 입력해요. (이름이 다르면 주소도 달라지고, `404.html` 안의 `/lighter/` 경로도 고쳐야 해요.)
2. **Public**을 선택하고 **Create repository**를 눌러요. (무료 계정의 GitHub Pages는 공개 저장소에서만 동작해요.)

### 2-A. 웹 화면에서 끌어다 놓기

1. 새 저장소 화면에서 **uploading an existing file** 링크(또는 **Add file → Upload files**)를 눌러요.
2. `site` 폴더를 열고 **폴더 안의 내용물 전체**(`index.html`, `support.html` … `assets` 폴더, `s` 폴더)를 선택해서 브라우저 창에 끌어다 놓아요. `site` 폴더 자체가 아니라 그 안의 파일들이 저장소 맨 위에 와야 해요.
3. 숨김 파일 `.nojekyll`은 macOS Finder에서 보이지 않을 수 있어요. Finder에서 `Cmd + Shift + .`을 누르면 보여요. 업로드가 어렵다면 업로드 후 **Add file → Create new file**에서 파일 이름에 `.nojekyll`을 입력하고 내용 없이 저장해도 돼요.
4. 아래 **Commit changes**를 눌러요.

### 2-B. 터미널(git)로 올리기

```bash
cd site                      # 이 README가 있는 폴더
git init
git add -A
git commit -m "Lighter 지원·약관 사이트"
git branch -M main
git remote add origin https://github.com/kylo2084/lighter.git
git push -u origin main
```

이후 수정할 때는 파일을 고치고 `git add -A && git commit -m "수정 내용" && git push` 하면 돼요.

### 3. Pages 켜기

1. 저장소의 **Settings → Pages**로 가요.
2. **Build and deployment → Source**를 **Deploy from a branch**로 두고, **Branch**를 `main`, 폴더를 `/ (root)`로 고른 뒤 **Save**를 눌러요.
3. 1~2분 뒤 같은 화면 위쪽에 `Your site is live at https://kylo2084.github.io/lighter/`가 표시돼요. 수정 사항도 push 후 1~2분 안에 반영돼요.

## App Store Connect에 넣을 주소

| App Store Connect 항목 | 주소 |
|---|---|
| 지원 URL (Support URL, 필수) | `https://kylo2084.github.io/lighter/support.html` |
| 개인정보 처리방침 URL (Privacy Policy URL, 필수) | `https://kylo2084.github.io/lighter/privacy.html` |
| 마케팅 URL (Marketing URL, 선택) | `https://kylo2084.github.io/lighter/` |

함께 쓰면 좋은 주소:

- **이용약관(EULA)** — 자동 갱신 구독 앱은 앱 설명이나 메타데이터에 이용약관 링크가 필요해요: `https://kylo2084.github.io/lighter/terms.html`
- **계정 삭제** — 심사 메모(App Review Information → Notes)에 앱 내 경로(프로필 → 계정 · 지원 → 회원 탈퇴)와 함께 적어두세요: `https://kylo2084.github.io/lighter/delete-account.html`
- **위치기반서비스 이용약관** — `https://kylo2084.github.io/lighter/location.html`

## 위치 공유 링크에 대해

앱 서버(Cloud Functions)는 위치 공유 링크를 `{SHARE_BASE_URL}/s/{shareId}` 형태로 만들어요. 실시간 지도는 서버가 보여줘야 하므로, 이 정적 사이트의 `s/` 페이지는 **링크가 이 사이트로 열렸을 때의 안내용**일 뿐 지도를 그리지 않아요. `SHARE_BASE_URL`을 이 사이트 주소로 지정하면 공유받은 사람은 지도 대신 안내 페이지를 보게 되니, 실제 지도는 서버(예: Firebase Hosting, `lighter.run`)에서 제공해주세요.

## 기타

- 외부 스크립트, 분석 도구, 쿠키가 없어요. 글꼴(Pretendard)만 jsDelivr CDN에서 불러오고, 불러오지 못하면 기기 기본 글꼴로 보여요. `404.html`에만 공유 링크 주소를 옮겨주는 짧은 인라인 스크립트가 있어요.
- 화면은 휴대폰(390px)과 데스크톱(1280px), 라이트·다크 모드에서 확인했어요.
