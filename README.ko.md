<div align="center">

# html-memo

**일상의 메모와 작업 로그를, 명령어 한 번으로 「명조체 × 다크 모드」의 우아한 HTML 파일로. Claude Code 프롬프트에 `/html-memo`라고 입력하기만 하면, 다시 읽고 싶어지는 「문서」가 생성됩니다.**

> Markdown인 채로 방치되기 쉬운 정보를, 품격 있는 문서로 승화시키기 위한 Claude Code 커스텀 스킬입니다. 설치 불필요, `commands` 폴더에 넣기만 하면 작동합니다.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Claude Code](https://img.shields.io/badge/Claude_Code-Skill-D97757)](https://claude.ai/claude-code)
[![Style](https://img.shields.io/badge/Style-Serif_%C3%97_Dark-111418)](#)

[![日本語](https://img.shields.io/badge/Lang-%E6%97%A5%E6%9C%AC%E8%AA%9E-87CEEB.svg)](README.md)
[![English](https://img.shields.io/badge/Lang-English-87CEEB.svg)](README.en.md)
[![한국어](https://img.shields.io/badge/Lang-%ED%95%9C%EA%B5%AD%EC%96%B4-87CEEB.svg)](README.ko.md)
[![简体中文](https://img.shields.io/badge/Lang-%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87-87CEEB.svg)](README.zh.md)
[![繁體中文](https://img.shields.io/badge/Lang-%E7%B9%81%E9%AB%94%E4%B8%AD%E6%96%87-87CEEB.svg)](README.tw.md)

</div>

---

## 출력 예시

`/html-memo`로 생성되는 HTML 파일은 다음과 같은 디자인이 됩니다.

<div align="center">
  <img src="assets/example.en.png" alt="html-memo 출력 예시" width="700">
</div>

---

## 특징

| | |
|---|---|
| **다크 모드 기반** | 순수한 검정보다 부드러운 `#111418`을 채택하여, 장시간 열람해도 눈이 편안합니다 |
| **명조체 폰트** | 텍스트에 품격과 가독성을 더하는 고급스러운 타이포그래피 |
| **한색 계열 강조색** | 진정·집중 효과가 있는 한색 시안 `#5BB3C9`이 중요한 인사이트를 자연스럽게 강조합니다 |
| **설치 불필요** | `commands` 폴더에 파일 하나만 넣으면 작동합니다 |
| **다국어 대응** | 입력한 언어를 자동으로 판별하여 같은 언어로 메모를 출력합니다 |

---

## 빠른 시작

파일을 수동으로 배치할 필요는 없습니다. **Claude Code에 이 저장소의 URL을 전달하고, 스킬을 사용할 수 있도록 요청하기만 하면** 설정이 완료됩니다.

Claude Code를 실행하고, 다음과 같이 지시해 주세요.

```text
이 저장소의 스킬을 사용할 수 있게 해줘:
https://github.com/y177649/html-memo
```

Claude Code가 저장소의 내용을 읽고, `commands/html-memo.md`를 당신의 프로젝트 `commands` 폴더에 배치합니다. 완료되면 `/html-memo` 명령어를 바로 사용할 수 있습니다.

---

## 수동 설치

Claude Code를 사용하지 않고 직접 설정하려면, 다음 절차로 배치할 수 있습니다.

1. 이 저장소의 `commands/html-memo.md`를 다운로드합니다.
2. 당신의 프로젝트 루트 디렉터리에 있는 `commands` 폴더 안에 배치합니다. (폴더가 없으면 생성해 주세요.)

---

## 사용법

Claude Code를 실행하고, 다음과 같이 명령어를 실행해 주세요.

```bash
> /html-memo 오늘의 개발 진행 상황과 앞으로의 과제를 정리해줘
```

`memos/` 디렉터리에 아름다운 HTML 파일이 자동으로 생성됩니다.

---

## 쾌적한 미리보기 환경 구축 (권장)

HTML 파일을 Markdown처럼 에디터 안에서 클릭 한 번으로 미리보기 하기 위해, Microsoft 공식 확장 기능의 도입을 권장합니다.

1. VS Code / Cursor에서 본 프로젝트를 열면, 우측 하단에 `Live Preview` 확장 기능 설치 권장 팝업이 표시되므로 설치해 주세요.
2. HTML 파일을 열면, 에디터 우측 상단에 미리보기 아이콘(돋보기 마크, 또는 「미리보기 표시」 버튼)이 표시됩니다. 이를 클릭하기만 하면, 브라우저를 열지 않고 에디터 안에서 직접 디자인을 확인할 수 있습니다.

---

## 라이선스

[MIT License](LICENSE)에 따라 공개하고 있습니다.
