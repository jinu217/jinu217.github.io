# 김진우 | 게임 클라이언트 포트폴리오

게임 클라이언트 프로그래머 김진우의 범용 이력서형 개인 홈페이지입니다. 첫 화면은 이력서 요약, `/work/`는 전체 프로젝트 목록, `/projects/.../`는 구현 사례를 보여줍니다. 회사별 자기소개서는 이 사이트에 고정하지 않고 별도로 작성합니다.

## 내용 수정

- 이름, GitHub 주소, 사이트 주소: `_config.yml`
- 첫 화면의 이력서 요약과 대표 프로젝트 순서: `_includes/page-home.html`
- 프로젝트별 상세 내용과 코드 링크: `entries/projects/<프로젝트>/ko.md`
- 소개 페이지와 메뉴 문구: `_data/locales/ko.yml`
- 디자인: `css/jinwoo.css`
- 플레이 화면 이미지: `images/projects/`
- 원본 상세 자료: `files/kim-jinwoo-portfolio.pdf`

프로젝트 화면 이미지는 제공된 포트폴리오 PDF에서 잘라 왔습니다. 넥슨 이력서에 기재된 학력·교육·이메일과 출시·시연·배포 성과도 반영했습니다. 사용자가 알려준 생년월일(2000.02.17)을 첫 화면에 추가했습니다. 직무 관련 교육 두 과정은 첫 화면에, 나머지는 소개 페이지에 요약했습니다. 주소·전화번호는 공개 사이트에 넣지 않았습니다. 플레이 영상은 제공된 자료에 없어 추가하지 않았습니다. 공개할 영상이 생기면 각 프로젝트의 `demo` 값에 링크를 넣으면 됩니다.

## GitHub Pages 배포

1. `jinu217.github.io`라는 이름의 GitHub 저장소를 만듭니다. 다른 이름을 쓰려면 `_config.yml`의 `url`, `baseurl`, `repository`를 그 주소에 맞게 수정합니다.
2. 이 폴더의 파일을 저장소 `main` 브랜치에 올립니다.
3. 저장소 **Settings → Pages → Build and deployment → Source**에서 **GitHub Actions**를 선택합니다.
4. `.github/workflows/pages.yml`이 Jekyll 사이트를 빌드하고 배포합니다.

로컬 Jekyll 환경이 있으면 `bundle install` 후 `bundle exec jekyll serve`로 확인할 수 있습니다. 현재 작업 환경에는 Ruby가 없어 로컬 Jekyll 빌드는 실행하지 못했습니다.

## 출처

사이트 구조는 [Andrei-Stefan20/developer-portfolio-template](https://github.com/Andrei-Stefan20/developer-portfolio-template)의 MIT 템플릿을 바탕으로 수정했습니다. 템플릿 저작권 고지는 `LICENSE`에 유지했습니다.
