<p align="center">
  <img src="./assets/logo.png" alt="novel-timeline" width="160" />
</p>

# novel-timeline

> 🌐 **Language**: 한국어 (this file) · [English](./README.en.md)

소설 작가를 위한 **타임라인 기반 스토리 관리 도구**.
복잡한 등장인물·사건·복선·관계를 한눈에 정리하고, 집필 에디터와 AI 연동으로 장편 원고 작업을 지원합니다.

> 이 저장소는 novel-timeline의 **정식 빌드 배포 채널**입니다.
> 소스코드는 별도 비공개 저장소에서 관리됩니다.

---

## 다운로드

최신 빌드는 **[Latest Release](https://github.com/seo1westn2020/novelTimeline_release/releases/latest)** 에서 받으실 수 있습니다. 전체 릴리즈 내역은 [Releases](https://github.com/seo1westn2020/novelTimeline_release/releases) 페이지에서 확인하세요.

| OS | 파일 | 비고 |
|---|---|---|
| **Windows 10 / 11** | [novel-timeline_1.0.0_x64-setup.exe](https://github.com/seo1westn2020/novelTimeline_release/releases/download/v1.0.0/novel-timeline_1.0.0_x64-setup.exe) | NSIS 인스톨러 |
| **macOS 12+ (Apple Silicon)** | [novel-timeline_1.0.0_aarch64.dmg](https://github.com/seo1westn2020/novelTimeline_release/releases/download/v1.0.0/novel-timeline_1.0.0_aarch64.dmg) | 디스크 이미지 (Apple Silicon 전용) |

> 📋 v1.0.0의 새 기능·수정·알려진 제약: [RELEASE_NOTES_v1.0.0.md](./RELEASE_NOTES_v1.0.0.md)

> 📘 자주 묻는 질문(FAQ): [FAQ.md](./FAQ.md)

### 📦 샘플 프로젝트 (NTZ)

처음 실행 시 빈 프로젝트로 시작합니다. 기능 사용법을 짧은 판타지 스토리로 보여주는 4언어 샘플을 제공하니 햄버거 메뉴 ≡ → **NTZ 가져오기**로 열어보세요. 인물 3명·사건 6개·복선·관계도·집필 본문·각주·참고 사진까지 모두 포함되어 있습니다.

| 언어 | 다운로드 |
|---|---|
| 🇰🇷 한국어 | [sample-ko.ntz](https://github.com/seo1westn2020/novelTimeline_release/releases/download/v1.0.0/sample-ko.ntz) |
| 🇺🇸 English | [sample-en.ntz](https://github.com/seo1westn2020/novelTimeline_release/releases/download/v1.0.0/sample-en.ntz) |
| 🇯🇵 日本語 | [sample-ja.ntz](https://github.com/seo1westn2020/novelTimeline_release/releases/download/v1.0.0/sample-ja.ntz) |
| 🇨🇳 中文 | [sample-zh.ntz](https://github.com/seo1westn2020/novelTimeline_release/releases/download/v1.0.0/sample-zh.ntz) |

> 본 빌드는 아직 **코드 서명 인증서가 적용되어 있지 않습니다.** 운영체제가 "출처를 알 수 없는 앱"으로 표시할 수 있으나, 실제 실행에는 문제가 없습니다.

### Windows에서 실행이 막힐 때

`Windows Defender SmartScreen` 경고 화면이 뜨면

1. 작은 글씨의 **"추가 정보"** 를 클릭하면 "실행" 버튼이 나타납니다.
2. **"실행"** 을 클릭하면 정상 설치가 진행됩니다.

### macOS에서 실행이 막힐 때

처음 실행 시 `"손상되어 열 수 없습니다"` 또는 `"확인되지 않은 개발자"` 경고가 뜨면

1. 응용 프로그램 폴더에서 **novel-timeline 아이콘을 우클릭** 후 **"열기"** 를 선택합니다.
   *(Apple Magic Mouse 등 우클릭이 안 되는 마우스를 쓰신다면 **`Control` 키를 누른 채 클릭** 하시면 됩니다.)*
2. 보안 다이얼로그가 다시 뜨면 한 번 더 **"열기"** 를 클릭합니다.
3. 한 번 허용한 뒤로는 일반 더블클릭으로 실행됩니다.

> macOS Sequoia(15) 이상에서 위 우클릭 방법으로도 막힐 경우, **시스템 설정 → 개인정보 보호 및 보안** 화면 하단의 **"확인 없이 열기"** 버튼을 클릭해 주세요.

> 그래도 안 될 경우, 터미널에서 아래 명령으로 quarantine 속성을 제거할 수 있습니다:
> ```bash
> xattr -d com.apple.quarantine "/Applications/novel-timeline.app"
> ```

---

## 주요 기능

- **타임라인** — 시간 축 기반 사건 정리, 동시 사건 그룹핑, 드래그 재정렬
- **관계도** — 인물 관계를 시각화, 페이지별 인물 선택 + 필터(생존자/카테고리)
- **인물 관리** — 성격·말투·세력 소속·상태 타임라인
- **세력 관리** — 인물의 세력 가입/탈퇴 시점 추적, 이중 소속 감지
- **복선 관리** — 심은 시점·회수 시점 연동
- **집필 에디터** — A4 페이지 분리 레이아웃, 각주 시스템, 미리보기/인쇄
- **AI 충돌 검증·초고 생성 (BYOK)** — OpenAI / Anthropic / Google / Ollama 자체 키 사용
- **자동 저장** — 모든 변경은 자동으로 보존, 종료 시에도 데이터 유실 없음
- **새 버전 알림 배지** — 새 릴리즈가 올라오면 헤더에 자동 배지 표시 (하루 1회 갱신)
- **수집자료** — 자료 이미지·텍스트·링크 보관
- **내보내기** — TXT(챕터별·전체) / JSON(전체·선택·관계페이지별)
- **다국어** — 한국어 / 영어 / 일본어 / 중국어
- **테마** — 다크 / 라이트

---

## 가격

| 플랜 | 가격 | 내용 |
|---|---|---|
| **체험 (Free Trial)** | 무료 | 설치 후 **3개월(90일)** 전 기능 사용. 별도 사용 한도 없음 |
| **월 구독 (Monthly)** | $10 / 월 | 전 기능 사용, 매월 자동 갱신 |
| **연 구독 (Annual)** | $80 / 년 | 전 기능 사용, 연 단위 결제 (월 대비 약 33% 할인) |

> 영구 라이선스는 제공하지 않습니다.

> 모든 SKU(월/연 구독)는 결제 후 **14일 이내 무조건 환불**이 가능합니다 ([환불 정책](./legal/refund.md)).

### 체험·구독 만료 후 (읽기 전용 모드)

3개월 체험이 만료되고 유료 구독을 활성화하지 않거나, 구독이 만료·해지된 경우 앱은 **읽기 전용 모드**로 전환됩니다.

| 구분 | 허용 | 차단 |
|---|---|---|
| 프로젝트 조회 | ✅ | |
| JSON · NTZ · TXT 내보내기 | ✅ | |
| 라이선스 키 입력 · 설정 변경 | ✅ | |
| 사건/인물/복선/관계 등 편집 | | ❌ |
| 외부 파일 가져오기 · 새 프로젝트 생성 | | ❌ |

**사용자 데이터 파일은 어떠한 경우에도 훼손되지 않으며**, 내보내기를 통해 언제든 외부 백업이 가능합니다.

결제 및 라이선스 키 발급/검증은 [Lemon Squeezy](https://lemonsqueezy.com) 를 통해 진행됩니다.

---

## 라이선스 키 사용 방법

1. 구매 완료 시 이메일로 **라이선스 키**가 전송됩니다.
2. novel-timeline 실행 → **설정 → 라이선스 키** 입력란에 붙여넣기.
3. 검증이 완료되면 자동으로 유료 기능(한도 해제 등)이 활성화됩니다.

인터넷 연결이 불안정해도 **30일의 오프라인 유예 기간** 동안 정상 사용 가능합니다.

---

## 버그 신고 / 건의

- 이메일: **askNovelTimeline@gmail.com**
- 버그 리포트에는 가능하면 다음 정보를 포함해 주세요:
  - 운영 체제 및 버전 (Windows 11 / macOS 14 등)
  - novel-timeline 버전
  - 재현 절차
  - 스크린샷

---

## 도움을 주신 분들 / Supporters

novel-timeline은 1인 인디 프로젝트입니다. **금전 후원뿐 아니라 번역 교정·기능 제안·버그 제보·아이디어 공유 등 다양한 형태로 도구를 함께 만들어 주신 모든 분**께 감사드립니다.

> _아직 등록된 분이 없습니다. 여러분이 첫 번째가 되어 주세요._

### ☕ 금전 후원 / Monetary support

| | |
|---|---|
| ☕ **Ko-fi** | [ko-fi.com/novelTimeline](https://ko-fi.com/novelTimeline) |
| 💳 **PayPal** | [paypal.me/novelTimeline](https://paypal.me/novelTimeline) |

체험 기간 동안 도구가 도움이 되셨다면 커피 한 잔으로 응원해 주세요.

### 🌍 번역·기능 제안·버그 제보 / Translation, ideas, bug reports

기능 제안·번역 교정·버그 제보 등 비금전적 기여도 환영합니다. 이메일 **askNovelTimeline@gmail.com** 또는 GitHub Issues로 연락해 주세요. 채택된 기여는 본 섹션에 함께 게재됩니다 (동의 시).

### 게재 형식 / Format

| 이름 / Name | 일자 / Date | 기여 내용 / Contribution | 메시지 / Message |
|---|---|---|---|
| _첫 번째 자리 / First slot_ | — | — | — |

---

## 라이선스

본 소프트웨어는 **End User License Agreement(EULA)** 에 따라 배포됩니다.
설치 전 [LICENSE.en](./LICENSE.en) 파일을 확인해 주세요 (한국어 참고 번역: [LICENSE](./LICENSE)).
두 문서 간 불일치가 있을 경우 **영문판이 우선**합니다.

Copyright © 2026 서일선 (novel-timeline). All rights reserved.

**한국 저작권 등록 (한국저작권위원회 CROS)**
- 저작물명: novel-timeline (소설타임라인)
- 등록번호: 제 C-2026-022388 호
- 등록년월: 2026년 5월

---

## 법적 문서 / Legal Documents

novel-timeline을 구매·사용하실 때 적용되는 **이용약관 · 환불 정책 · 개인정보 처리방침**입니다.
영문본이 법적 원본이며, 한국어본은 사용자 편의를 위한 번역입니다.

| 문서 / Document | 한국어 | English |
|---|---|---|
| 이용약관 / Terms of Service | [legal/terms.md](./legal/terms.md) | [legal/terms.en.md](./legal/terms.en.md) |
| 환불 정책 / Refund Policy (14-day, all SKUs) | [legal/refund.md](./legal/refund.md) | [legal/refund.en.md](./legal/refund.en.md) |
| 개인정보 처리방침 / Privacy Policy | [legal/privacy.md](./legal/privacy.md) | [legal/privacy.en.md](./legal/privacy.en.md) |
| 인덱스 / Index | [legal/README.md](./legal/README.md) | — |
