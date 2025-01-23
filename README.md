# 실시간 침입자 감지 시스템 (Real-time Intruder Detection System)

## 소개

이 프로젝트는 웹 기반으로 실시간 비디오 스트림에서 사람의 포즈를 감지하고 분석하여 이상 행동을 감지하는 시스템입니다. TensorFlow.js 라이브러리를 사용하여 브라우저에서 실시간으로 포즈 감지 및 분석을 수행하며, Gemini 1.5 API를 연동하여 이상 행동 판단을 위한 동적 임계값 조정을 지원합니다.

## 주요 기능

- **실시간 포즈 감지:** 웹캠 또는 비디오 파일로부터 실시간으로 사람의 포즈를 감지합니다.
- **이상 행동 감지:** 관절 각도의 변화를 분석하여 이상 행동을 감지하고, 사용자에게 경고를 표시합니다.
- **동적 임계값 조절:** Gemini 1.5 API를 사용하여 이상 행동 판단을 위한 최적의 임계값을 동적으로 설정합니다.
- **비디오 녹화:** 감지된 비디오 스트림을 녹화하고 다운로드할 수 있습니다.
- **실시간 캔버스 캡처:** 이상 행동 감지 시 캔버스 이미지를 캡처하여 저장합니다.
- **슬라이더 조절:** 사용자가 수동으로 각도 변화 임계값을 조절할 수 있습니다.
- **다양한 관절 분석:** 팔, 다리, 몸통, 목 등 다양한 관절의 각도 변화를 분석합니다.
- **웹 기반 인터페이스:** 브라우저에서 실행되는 사용자 친화적인 인터페이스를 제공합니다.

## 기술 스택

- **TensorFlow.js:** 브라우저에서 머신러닝 모델을 실행하기 위한 JavaScript 라이브러리
- **@tensorflow-models/pose-detection:** TensorFlow.js를 사용한 포즈 감지 모델
- **Gemini 1.5 API:** Google의 생성형 AI 모델 API (API 키 필요)
- **HTML, CSS, JavaScript:** 웹 페이지 구조, 스타일, 동작 구현

## 실행 방법

1.  **필수 조건:**
    *   Node.js 및 npm (또는 yarn) 설치
    *   Gemini 1.5 API 키 발급
2.  **프로젝트 설정:**
    *   프로젝트 폴더를 생성하고, 해당 폴더에 아래의 코드를 `index.html` 파일로 저장합니다.
    *   `geminiApiKey` 변수에 실제 API 키를 입력합니다.
3.  **실행:**
    *   웹 브라우저에서 `index.html` 파일을 엽니다.
    *   "Start Webcam" 버튼을 클릭하여 웹캠을 시작하거나, 파일 선택기를 사용하여 비디오 파일을 선택합니다.
    *   "Analyze Angles" 버튼을 클릭하여 Gemini API로 각도를 분석하고 동적으로 임계값을 설정합니다.
    *   슬라이더를 움직여 임계값을 수동으로 조절할 수 있습니다.
    *   "Start Recording" 버튼을 클릭하여 비디오 녹화를 시작하고, 다시 클릭하여 녹화를 종료합니다.

## 주요 코드 설명

- **`loadModels()`:** TensorFlow.js를 사용하여 포즈 감지 모델을 로드합니다.
- **`calculateAngle(a, b, c)`:** 세 점의 좌표를 사용하여 각도를 계산합니다.
- **`detectAndAnalyze(currentVideo)`:** 실시간으로 비디오 스트림을 분석하고 포즈를 감지합니다.
- **`detectMovement(keypoints)`:** 포즈 키포인트의 움직임을 감지합니다.
- **`detectSuspiciousBehavior(keypoints)`:** 관절 각도의 변화를 분석하여 이상 행동을 감지합니다.
- **`analyzeAngles()`:** Gemini API를 사용하여 각도를 분석하고 동적으로 임계값을 조절합니다.
- **`callGeminiApi(prompt)`:** Gemini API를 호출하여 텍스트를 생성합니다.
- **`setDynamicThresholds(analysis)`:** Gemini API 응답을 기반으로 임계값을 동적으로 조절합니다.
- **`startWebcam()`:** 웹캠을 시작합니다.
- **`handleFile(event)`:** 비디오 파일을 선택합니다.
- **`startRecording()`:** 비디오 녹화를 시작합니다.
- **`handleDataAvailable(event)`:** 녹화된 비디오 데이터를 처리합니다.
- **`downloadVideo()`:** 녹화된 비디오를 다운로드합니다.
- **`captureCanvas(type)`:** 캔버스 이미지를 캡처합니다.
- **`setMessage(text, color)`:** 사용자에게 메시지를 표시합니다.

## 추가 고려 사항

- **API 응답 처리:** API 응답이 JSON 형식이 아닌 경우 추가 파싱 로직 구현
- **임계값 조절 알고리즘:** Gemini API 응답을 기반으로 임계값을 조절하는 알고리즘 개선
- **사용자 피드백:** 이상 행동 감지 결과를 더 명확하게 표시하는 방법 고려
- **성능 최적화:** Gemini API 호출 및 모델 분석 성능 최적화
- **UI/UX 개선:** 사용성 개선을 위한 인터페이스 및 경험 개선
- **보안:** 웹페이지에서 API 키 노출에 대한 보안 강화

## 라이선스

MIT License

Copyright (c) 2024 hwkims

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

## 연락처

[https://github.com/hwkims](https://github.com/hwkims)
