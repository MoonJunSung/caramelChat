<img src="common/src/main/resources/icon.png" width="96" alt="caramelChat 아이콘"/>

# caramelChat
[English](README.md) | **한국어**

마인크래프트에서 향상된 IME 입력 환경을 제공합니다.

---

## 📕 소개
caramelChat은 [CocoaInput](https://github.com/Axeryok/CocoaInput)의 입력 방식에서 영감을 받은 모던 채팅 모드입니다.

## 💻 호환성
현재 caramelChat은 [CocoaInput-lib](https://github.com/Korea-Minecraft-Forum/CocoaInput-lib)를 사용합니다.
따라서 OS 호환성은 CocoaInput과 동일합니다.

caramelChat v2.0부터는 자체 네이티브 라이브러리를 사용할 계획이며,
호환성도 점차 개선될 예정입니다.

|            OS             |    호환성    |
|:-------------------------:|:---------:|
|    **Windows** (x86_64)   |  🟢 호환됨  |
|    **Windows** (arm64)    | 🔴 호환 안 됨 |
|     **macOS** (Intel)     |  🟢 호환됨  |
| **macOS** (Apple Silicon) |  🟢 호환됨  |
|   **Linux X11** (x86_64)  | 🟡 일부 환경에서 호환 안 됨 |
|   **Linux X11** (arm64)   | 🔴 호환 안 됨 |
| **Linux Wayland** (x86_64) | 🟡 일부 환경에서 호환 안 됨 |
| **Linux Wayland** (arm64) | 🔴 호환 안 됨 |

모드 로더 호환성은 다음과 같습니다.

|      플랫폼       |   지원 여부   |
|:--------------:|:---------:|
| Fabric / Quilt |  🟢 호환됨  |
|     Forge      |  🟢 호환됨  |
|    NeoForge    |  🟢 호환됨  |

## 🛠️ 문제 해결 (macOS 14.0 이상)
macOS Sonoma 이상 버전을 사용 중이라면 다음과 같은 문제가 생길 수 있습니다.
- 아주 빠르게 입력하면 일부 글자가 누락됩니다.
- 시스템 키(예: 입력 소스 전환)를 누르면 클라이언트가 크래시됩니다.

대부분 Sonoma에서 추가된 입력 툴팁(Input Tooltip) 때문입니다. 하지만 Apple은 이 기능을 끄는 API를 제공하지 않습니다.

![macOS Sonoma 입력 표시기](https://github.com/LemonCaramel/caramelChat/assets/45729082/e1d34917-1892-4cb6-aa3f-38fdab58fad9)


아래 방법으로 입력 툴팁을 시스템 전체에서 끌 수 있습니다.

터미널을 열고 다음 명령을 입력하세요.
```Bash
sudo mkdir -p /Library/Preferences/FeatureFlags/Domain
sudo /usr/libexec/PlistBuddy -c "Add 'redesigned_text_cursor:Enabled' bool false" /Library/Preferences/FeatureFlags/Domain/UIKit.plist
```
그다음 맥을 재부팅하면 Sonoma 이전의 입력 환경으로 돌아갑니다.

## 🛠️ 문제 해결 (Linux Wayland)

Wayland 프로토콜을 사용하는 일부 리눅스 배포판에서는 크래시가 발생할 수 있습니다.
시스템에 Xwayland가 있어서 GLFW가 X11 기반으로 실행되려 하기 때문입니다.

다행히 이 문제를 해결해 주는 서드파티 모드가 있습니다.

**WayGL:** [Modrinth](https://modrinth.com/mod/waygl), [Github](https://github.com/wired-tomato/WayGL)

## 🛠️ 문제 해결 (Linux Fcitx5)

Fcitx5는 "On The Spot" 스타일을 사용하지 않으면 동작하지 않을 수 있습니다.

1. 설정 프로그램이 `fcitx5-config-qt`라면 `Fcitx Configuration -> Addons`로 이동해 `X Input Method Frontend`를 찾고, 해당 줄의 톱니바퀴 버튼을 누르세요.
2. `Use On The Spot Style (Needs restarting)` 옵션을 켠 뒤 재부팅하세요.
3. 이제 정상적으로 동작합니다.

## 🚀️ 기여하기
네이티브든 Java든 모든 기여를 환영합니다.

## 📜 라이선스
caramelChat은 자유 오픈소스 라이선스인 GNU LGPLv3를 따릅니다. 자세한 내용은 [라이선스 파일](LICENSE)을 참고하세요.

이 저장소에 풀 리퀘스트를 제출하면, 별도로 밝히지 않는 한 기여 내용도 GNU LGPLv3로 라이선스하는 것으로 간주합니다.
