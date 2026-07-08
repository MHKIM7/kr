# 연구실 홈페이지 편집 가이드 (학생용)

이 문서는 GIScience & Spatial Bigdata Lab 영문 홈페이지를 직접 편집하는
방법을 설명합니다. **GitHub, 마크다운, BibTeX를 몰라도 됩니다.** 폼만
채우면 됩니다.

- 영문 홈페이지: <https://knu-giscience.github.io/>
- 한국어 홈페이지(기존 Weebly, 별도 운영): <https://knugis.weebly.com/>
  영문 사이트 우상단 "한국어" 버튼이 Weebly로 이어집니다.

> 이 문서는 **영문 사이트 편집**만 다룹니다. 한국어 콘텐츠는 Weebly에서
> 관리합니다.

---

## 1. 처음 한 번만 하는 준비

### (1) GitHub 계정 만들기

1. <https://github.com/> 접속 → **Sign up**
2. 학교 또는 개인 이메일로 가입
3. 사용자명을 정한다 (예: `knugis-yourname`)

### (2) 교수님께 GitHub 사용자명 알려주기

본인 GitHub 사용자명을 슬랙 또는 이메일로 알려주면 편집 권한이 부여됩니다.
GitHub에 초대 메일이 오면 **"Accept invitation"** 버튼을 꼭 눌러주세요.

### (3) Pages CMS 접속

1. <https://app.pagescms.org/> 접속
2. **Sign in with GitHub** 클릭
3. "Authorize Pages CMS" 허용
4. 좌측 목록에서 `knu-giscience/knu-giscience.github.io` 선택

이게 끝. 다음부터는 1번 클릭이면 편집 가능. **북마크 추천.**

---

## 2. Members 정보 수정

졸업, 입학, 직책 변경 등이 있을 때.

1. Pages CMS → **"Members"**
2. 5개 그룹 중 수정할 그룹 펼치기:
   - Principal Investigator (교수님)
   - PhD Students / MS Students / Undergraduate Students / Alumni
3. 본인 항목 수정 또는 새 항목 추가
4. **저장**

### 사진 추가/교체

- 정사각형 jpg, 500×500px 정도 권장
- 파일명: `myunghwan_kim.jpg` 처럼 영문·언더스코어
- 폼의 **Photo**에서 업로드 → `assets/img/members/`에 자동 저장

### 졸업하면

해당 그룹에서 본인 항목 삭제 → **Alumni**에 새로 추가 → note에 현재
소속 입력.

---

## 4. Projects 추가

새 연구과제가 시작되거나 완료되면.

1. Pages CMS → **"Projects"** → **"+ Add Entry"**
2. 폼 입력:
   - **Title**: 영문 프로젝트명
   - **Description**: 한 줄 요약 (영어)
   - **Cover image**: 표지 사진 (선택)
   - **Importance**: 진행 중은 1~4, 완료는 5 이상
   - **Category**: `ongoing` 또는 `completed`
   - **Period**: `2026.05 – 2026.10` 형식
   - **Sponsor**: 발주처 (영문, 예: KRIHS / KOTI / NRF)
   - **Body**: 자세한 영문 설명
3. 저장

프로젝트가 완료되면 항목을 열고 **Category**를 `ongoing` → `completed`
로 바꾸기만 하면 됩니다.

---

## 5. Publications 추가 (논문 게재)

논문은 **BibTeX** 형식으로 4개 파일에 분류해서 관리합니다:

| 파일 | 용도 |
|---|---|
| `01_journal.bib` | I. Journal Articles |
| `02_book_chapter.bib` | II. Book Chapters |
| `03_conference.bib` | III. Conference Proceedings |
| `04_report.bib` | IV. Research Reports |

### 가장 쉬운 방법: Google Scholar에서 BibTeX 복사

1. <https://scholar.google.com/> 에서 자기 논문 검색
2. 논문 아래 **"인용"** 클릭 → **BibTeX** 클릭 → 텍스트 복사
3. Pages CMS → 해당 카테고리 ("Publications · I. Journal Articles" 등)
4. 본문 위쪽 (가장 최신 항목 옆)에 붙여넣기
5. 저장

### 한국어 논문 (Korean journals)도 같은 파일에

`01_journal.bib`에 한국어 논문도 함께 들어갑니다. 형식:

```bibtex
@article{lee2026sample,
  title    = {{국문 논문 제목 그대로}},
  author   = {{이재현, 홍길동}},
  journal  = {대한교통학회지},
  volume   = {44},
  number   = {1},
  pages    = {1--15},
  year     = {2026}
}
```

**중요**: 한국어 저자명은 `{{이재현, 홍길동, 김철수}}`처럼 **하나의 묶음**
으로 작성합니다. 영어식 ` and ` 구분자를 쓰면 화면에 "and"가 그대로
나옵니다. 한국어 제목과 저널명도 그대로 한글로.

### 대표 논문 표시

BibTeX 항목 끝에 `selected = {true},` 한 줄을 추가하면 영문 홈페이지의
"selected publications"에 표시됩니다.

---

## 6. About / Contact 페이지 수정

- 좌측 **"Home (About)"** 또는 **"Contact"**
- Body 직접 편집 → 저장

---

## 7. 자주 묻는 질문

### Q. 잘못 저장했어요. 되돌릴 수 있나요?

네. 모든 변경은 git commit으로 기록됩니다. 교수님께 알려주시면 1분 안에
되돌릴 수 있습니다.

### Q. 저장했는데 사이트에 안 보여요.

저장 후 사이트 반영까지 **1~3분** 걸립니다. 그래도 안 보이면:

1. <https://github.com/knu-giscience/knu-giscience.github.io/actions> 접속
2. 최신 빌드(맨 위)가 ✅ 초록색이면 성공, ❌ 빨간색이면 빌드 실패
3. 빨간색이면 교수님께 알려주세요

### Q. 사진은 어디에 저장되나요?

자동으로 `assets/img/members/` 또는 `assets/img/projects/`에 들어갑니다.
직접 폴더를 손대지 않아도 됩니다.

### Q. 모바일에서도 편집 가능한가요?

네. Pages CMS는 모바일·태블릿에서도 동작합니다.

### Q. GitHub 코드는 직접 안 봐도 되나요?

네. **Pages CMS만 쓰면 됩니다.**

---

## 8. 도움이 필요할 때

- 교수님 (이재현)
- 슬랙: 연구실 채널 #homepage
- Pages CMS 매뉴얼: <https://pagescms.org/docs/>
- 마크다운 가이드: <https://www.markdownguide.org/cheat-sheet/>

---

처음엔 어색해도 멤버 항목 두세 개 추가해보면 금방 익숙해집니다.
