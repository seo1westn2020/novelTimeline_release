# Ollama 가이드 (한국어 / 한국어 작가용)

> 📘 Ollama는 PC에 직접 설치하는 무료 로컬 AI입니다. 인터넷 없이도 동작하며, 본인 데이터가 외부로 전송되지 않습니다. 단 PC 사양(RAM·GPU)이 일정 이상 필요합니다.

---

## 0. 왜 Ollama인가 — 무료·구독 불필요·offline

다른 AI 프로바이더(OpenAI / Anthropic / Google)와 다른 Ollama만의 장점:

- 💸 **완전 무료** — API 키 발급도, 결제도, 카드 등록도 필요 없습니다. PC 전기료만 듭니다.
- 📦 **구독 0** — 월정액·선결제·잔액 관리 같은 일이 일절 없습니다.
- 🔒 **원고가 PC 밖으로 안 나감** — Google·OpenAI 서버로 전송되지 않습니다. 인터넷이 끊겨도 동작.
- 🌐 **오프라인 가능** — 비행기·기차·산골 작업실 어디서나 사용 가능.
- 🌏 **CORS·계정 차단 걱정 없음** — novel-timeline이 자체적으로 Rust IPC로 호출 처리해 브라우저 차단 이슈가 발생하지 않습니다 (T-051 fix 이후).

**제약**:
- PC 사양(RAM·VRAM)이 일정 이상 필요합니다 (1번 참조).
- 모델 다운로드 1회 시간이 듭니다 (4.7~19 GB).
- 첫 호출 시 모델을 RAM/VRAM에 로드하느라 **5~30초 지연**이 발생합니다. **두 번째 호출부터는 정상 속도** (모델이 메모리에 캐시됨).

> 💡 **실제 검수 결과 (2026-05)**: `qwen2.5:14b`는 GPT-4o와 동일하게 **충돌 2건 검출**을 달성했습니다 (동일 NTZ 샘플). 사양이 받쳐주신다면 **무료로 GPT-4o급 결과**를 얻으실 수 있다는 뜻입니다. 자세한 비교는 [AI_GUIDE.md § 3](./AI_GUIDE.md#3-4-프로바이더-비교-실제-검수-결과-기반) 참조.

---

## 1. PC 사양 확인 (먼저) — 모델 선택 표

본인 PC 사양에 맞는 모델을 고르세요. **사양이 받쳐주시면 `qwen2.5:14b` 사용을 강력 권장**합니다 (GPT-4o급 검출).

| 모델 | 다운로드 크기 | RAM 요구 | **VRAM 권장** | 충돌 검출 (검수) | 추천 대상 |
|---|---|---|---|---|---|
| **qwen2.5:7b** | 4.7 GB | 6 GB+ | 6 GB | 약함 (놓치는 항목 多) | 저사양 / 가볍게 시작 |
| **qwen2.5:14b** ⭐ | 9 GB | 12 GB+ | **10~12 GB** | **GPT-4o급 (2건)** | **사양 OK시 권장** |
| qwen2.5:32b | 19 GB | 24 GB+ | 24 GB+ (RTX 3090/4090) | 최상 | 고사양 워크스테이션 |

> 💡 **한국어 작법 품질은 Qwen 시리즈가 대체로 우수**합니다 (Llama·Gemma·Mistral 대비). 다른 모델 실험은 9번 참조.

추론 시간:
- **GPU 사용 시**: 첫 호출 5~30초(로드) → 이후 수 초~10초
- **CPU만 사용 시**: 첫 호출 30~120초(로드) → 이후 30~60초 (불편하지만 동작)

본인 PC RAM/VRAM 확인:
- Windows RAM: 작업 관리자 → 성능 → 메모리
- Windows VRAM: 작업 관리자 → 성능 → GPU → 전용 GPU 메모리
- macOS: 사과 아이콘 → 이 Mac에 관하여 → 메모리 (Apple Silicon은 RAM=VRAM 공유)

<!-- 📸 스크린샷: Windows 작업 관리자 메모리·GPU 탭 / macOS 이 Mac에 관하여 -->

---

## 2. Ollama 설치

**Windows**:
1. https://ollama.com/download/windows 접속
2. **OllamaSetup.exe** 다운로드 → 더블클릭 설치
3. 설치 후 시스템 트레이에 ollama 아이콘 등장 = 데몬 실행 중

**macOS**:
1. https://ollama.com/download/mac 접속
2. **Ollama-darwin.zip** 다운로드 → 압축 풀기 → `Ollama.app`을 응용 프로그램으로 이동
3. 첫 실행 시 macOS 보안 안내 (확인되지 않은 개발자) — 우클릭 → 열기

**Linux** (참고용):
```bash
curl -fsSL https://ollama.com/install.sh | sh
```

설치 검증 — 명령 프롬프트(Windows: cmd / macOS: 터미널) 열고:
```
ollama --version
```
버전 번호가 출력되면 성공.

<!-- 📸 스크린샷: Ollama 시스템 트레이/메뉴바 아이콘 -->
<!-- 📸 스크린샷: 명령 프롬프트에서 ollama --version 출력 -->

---

## 3. 모델 다운로드

명령 프롬프트(또는 터미널)에서:
```
ollama pull qwen2.5:7b
```
- 다운로드 크기: 약 4.7 GB
- 시간: 인터넷 속도에 따라 10~30분
- 한 번 받으면 다시 받을 필요 없음. 디스크 영구 보관.

다운로드 완료 후 동작 테스트:
```
ollama run qwen2.5:7b "안녕하세요. 자기소개 한 줄로."
```
한국어 답이 나오면 정상.

<!-- 📸 스크린샷: ollama pull 다운로드 진행 표시 -->

---

## 4. Ollama 데몬 실행 확인

**중요**: novel-timeline에서 사용하려면 **Ollama가 백그라운드에서 실행되고 있어야** 합니다.

- Windows: 시스템 트레이에 ollama 아이콘 있으면 OK. 없으면 시작 메뉴 → Ollama 클릭
- macOS: 메뉴바에 ollama 아이콘 있으면 OK. 없으면 응용 프로그램 → Ollama.app 실행
- 데몬 endpoint: `http://localhost:11434` (자동, 변경 불필요)

브라우저로 확인:
- 주소창에 `http://localhost:11434` 입력 → "Ollama is running" 텍스트 보이면 정상

---

## 5. novel-timeline 앱 설정

1. 햄버거 메뉴 ≡ → 설정 → AI 설정
2. 프로바이더: **Ollama** 선택
3. 베이스 URL: 기본값 (`http://localhost:11434`) 유지
4. API 키: **비워둠** (Ollama는 키 불필요)
5. 모델명: `qwen2.5:14b` 권장 (또는 받으신 모델명 그대로 — 1번 표 참조)
6. **연결 테스트** 클릭 → 정상이면 200 OK

> 💡 **CORS 차단 걱정 없음**: novel-timeline은 자체적으로 Rust IPC를 통해 Ollama를 호출하므로, 브라우저 도구에서 흔한 CORS 차단 문제가 발생하지 않습니다. `OLLAMA_ORIGINS` 등 환경변수 설정은 **불필요**합니다. (다른 외부 도구를 함께 쓰실 경우는 부록 10번 참조.)

<!-- 📸 스크린샷: novel-timeline 설정 → AI 프로바이더 Ollama 선택 + 모델명 입력 + 연결 테스트 OK -->

---

## 6. 첫 충돌 검사

샘플 NTZ로 빠른 테스트:
1. release 리포의 [sample-ko.ntz](https://github.com/seo1westn2020/novelTimeline_release/releases/download/v1.0.0/sample-ko.ntz) 다운로드
2. novel-timeline에서 NTZ 가져오기로 열기
3. 사건 카드(예: "동굴 첫 조우") 우상단 🛡️ 버튼 클릭
4. 충돌 검사 결과가 우측 패널에 뜨면 성공. **첫 호출은 모델 로드로 5~30초 지연** → 두 번째부터 정상 속도.

<!-- 📸 스크린샷: 첫 충돌 검사 결과 패널 -->

> 💡 **첫 호출이 답답할 정도로 오래 걸린다고 느끼셔도 정상입니다.** 모델이 RAM/VRAM에 올라가는 시간입니다. 같은 모델을 두 번째 호출하실 때는 이 지연이 사라집니다.

---

## 7. 비용 / 성능

- **비용**: $0 (PC 자원만)
- **속도**: GPU 있으면 빠름. CPU만 사용 시 인내 필요
- **품질**: 7b 모델은 시작용. 결과가 짧거나 누락이 잦으면 14b로 업그레이드
- **장점**: 데이터가 외부로 안 나감. 인터넷 없이 동작.
- **단점**: 큰 프로젝트(인물 20+, 사건 50+)는 7b가 부족할 수 있음 → 14b 또는 OpenAI/Anthropic 사용

---

## 8. 흔한 문제

| 증상 | 원인 / 해결 |
|---|---|
| "Connection refused" 또는 "ECONNREFUSED" | Ollama 데몬 미실행. 시작 메뉴/응용 프로그램에서 Ollama 실행 |
| "Model not found" | 모델 다운로드 안 됨. `ollama pull qwen2.5:14b` (또는 사용 중인 모델명) 재실행 |
| "Out of memory" / 멈춤 | 모델이 PC RAM/VRAM 초과. 더 작은 모델로 변경 (예: 14b → 7b) 또는 RAM 추가 |
| 응답이 짧거나 누락 | 모델 컨텍스트 한계. v1.0.1+ 부터 num_ctx=16384 적용됨 (T-057 fix). 모델을 14b로 업그레이드 또는 작은 프로젝트로 시도 |
| 첫 호출이 매우 느림 (5~30초+) | 정상 동작입니다. 모델을 RAM/VRAM에 로드하는 시간 — **두 번째 호출부터 빠름** |
| GPU가 있는데도 느림 | 모델이 VRAM에 다 못 올라가 일부가 CPU로 떨어졌을 가능성. 아래 `ollama ps` 명령으로 점검 |

### 🔍 진단 명령 — `ollama ps`

현재 로드된 모델이 GPU·CPU에 어떻게 분배되어 있는지 확인합니다.

```
ollama ps
```

출력 예시:
```
NAME            ID              SIZE      PROCESSOR          UNTIL
qwen2.5:14b     abc123...       11 GB     100% GPU           4 minutes from now
```

해석:
- `100% GPU` — 이상적. 모든 레이어가 VRAM에 올라가 가장 빠른 속도로 동작.
- `60% GPU / 40% CPU` — VRAM이 부족해 일부가 CPU로 떨어진 상태. 속도 저하 발생. 더 작은 모델 사용 권장 (예: 14b → 7b).
- `100% CPU` — GPU 사용 안 됨. 매우 느림. GPU 드라이버·CUDA·Metal 설정 확인 또는 더 작은 모델로 전환.

> 💡 충돌 검사 결과가 만족스러우나 속도가 답답하시다면 `ollama ps`로 분배 상태를 먼저 점검하세요. 모델을 굳이 바꾸지 않고 분배 문제를 해결하는 것만으로 속도가 회복되는 경우가 많습니다.

---

## 9. 모델 갈아끼우기 (선택)

**더 작은 (가벼움)**:
```
ollama pull qwen2.5:3b   # 2 GB, RAM 3 GB+, 한국어 약함, 충돌 검출 매우 약함
ollama pull qwen2.5:7b   # 4.7 GB, VRAM 6 GB, 검출 약함이지만 동작
```

**더 큰 (품질)** ⭐ 권장:
```
ollama pull qwen2.5:14b  # 9 GB, VRAM 10~12 GB, GPT-4o급 검출
ollama pull qwen2.5:32b  # 19 GB, VRAM 24 GB+ (RTX 3090/4090급)
```

**다른 모델 탐험**:
```
ollama pull llama3.1:8b
ollama pull gemma2:9b
ollama pull mistral
```
- 모델 다운로드 후 novel-timeline 설정에서 모델명만 바꿔주면 사용 가능
- **한국어 작법·충돌 검사 정밀도는 Qwen 시리즈가 대체로 우수** (실측 기준)

---

## 10. 부록 — 다른 도구에서 Ollama를 쓰실 때 (CORS·`OLLAMA_ORIGINS`)

> 📘 **novel-timeline 사용자는 이 섹션을 읽으실 필요가 없습니다.** novel-timeline은 자체적으로 Rust IPC를 통해 Ollama를 호출하므로 CORS 문제가 발생하지 않습니다. 아래 내용은 Open WebUI·Chrome 확장·기타 브라우저 기반 도구에서 Ollama를 함께 쓰실 때 참고 자료입니다.

브라우저에서 Ollama API(`http://localhost:11434`)를 직접 호출하면 일부 환경에서 CORS 차단이 발생할 수 있습니다. 해결 방법:

**Windows (PowerShell, 영구 적용)**:
```powershell
[System.Environment]::SetEnvironmentVariable('OLLAMA_ORIGINS', '*', 'User')
```
설정 후 Ollama 데몬 재시작 (시스템 트레이 → Quit Ollama → 시작 메뉴에서 다시 실행).

**macOS (~/.zshrc 또는 ~/.bash_profile)**:
```bash
launchctl setenv OLLAMA_ORIGINS "*"
```
또는 영구 적용을 원하시면 `~/Library/LaunchAgents/com.ollama.plist`에 환경변수 추가.

**Linux (systemd)**:
```
sudo systemctl edit ollama
```
편집기에서:
```
[Service]
Environment="OLLAMA_ORIGINS=*"
```
이후 `sudo systemctl restart ollama`.

> ⚠️ `*` 와일드카드는 모든 도메인에서 접근 가능하다는 의미입니다. 보안이 중요하다면 사용하실 도구의 origin만 명시적으로 적으세요 (예: `http://localhost:3000,https://app.example.com`).

---

> 다음: 본인 작품으로 충돌 검사·초고 생성 시도. 결과가 만족스럽지 않으면 [AI_GUIDE.md](./AI_GUIDE.md) 메인 페이지에서 다른 프로바이더 비교.
