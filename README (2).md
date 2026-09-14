# LGD Production & Quality Report Dashboard

**날짜:** 09월 14일

## 사용 라이브러리

- **Python**
- **Flask 3.1.2** — 웹 서버 및 REST API 구성
- **Werkzeug** — Flask 웹 서버 실행
- **Three.js 0.170.0** — 생산·검사 설비 3D 시각화
- **OrbitControls** — 3D 화면 회전 및 확대/축소 제어
- **Cloudflared** — Google Colab에서 실행한 로컬 Flask 서버를 외부에서 접속하기 위한 Cloudflare Tunnel 구성
- **IPython.display** — Google Colab에서 외부 접속 링크 출력
- Python Standard Library
  - `asyncio`
  - `json`
  - `os`
  - `pathlib`
  - `socket`
  - `subprocess`
  - `threading`
  - `urllib`
  - `datetime`

## 설명

LG디스플레이 직무 이해 및 생산·품질 업무 학습을 목적으로 제작한 **교육용 생산·품질 보고서 대시보드**입니다.

Google Colab 환경에서 Flask 기반 웹 서버를 실행하고, Cloudflare Tunnel을 통해 생성된 외부 URL을 이용하여 브라우저에서 대시보드에 접속할 수 있도록 구성했습니다.

대시보드에서는 날짜와 생산 라인을 선택하여 가상의 생산 데이터를 조회할 수 있으며 다음 정보를 확인할 수 있습니다.

- 생산 목표 및 실제 생산량
- 생산 달성률
- 검사 수량 및 불량 수량
- 불량률
- LOT별 생산·검사 기록
- 날짜별 불량률
- 생산설비 이벤트 및 이상 이력

조회된 데이터를 기반으로 **생산·품질 업무 보고서 초안**을 자동 생성할 수 있습니다. 생성한 보고서는 사용자가 직접 내용을 검토 및 수정하고 검토 완료 상태와 함께 저장할 수 있습니다.

저장된 보고서는 다음 형식으로 내려받을 수 있습니다.

- `TXT` : 생산·품질 업무 보고서
- `JSON` : 보고서 작성에 사용한 근거 데이터

또한 **Three.js 기반 3D 패널 검사·이송 설비**를 구현하여 생산 라인의 상태를 시각적으로 확인할 수 있도록 구성했습니다.

3D 화면에서는 다음 기능을 제공합니다.

- 마우스 드래그를 통한 설비 회전
- 마우스 휠을 통한 확대/축소
- 디스플레이 패널 이송 애니메이션
- 검사 장비 및 컨베이어 표현
- 생산 라인 상태에 따른 타워 램프 표시
- 라인별 온도 상태 표시

본 프로젝트의 데이터와 설비 상태는 실제 생산 데이터가 아닌 **교육용 가상 데이터**이며, 별도의 LLM API를 사용하지 않고 정해진 데이터와 로직을 기반으로 보고서를 생성합니다.

## 주요 기능

```text
사용자
  ↓
날짜 / 생산라인 선택
  ↓
Flask REST API
  ↓
생산·품질 데이터 조회
  ↓
생산량 / 달성률 / 불량률 계산
  ↓
LOT 및 설비 이벤트 확인
  ↓
보고서 초안 생성
  ↓
사용자 검토 및 수정
  ↓
TXT / JSON 저장
```

서버는 Google Colab 내부의 사용 가능한 포트를 자동으로 탐색하여 실행되며, 실행된 로컬 Flask 서버는 **Cloudflared Quick Tunnel**을 통해 외부에서 접속할 수 있는 URL로 연결됩니다.

## 참고 문헌

1. **Flask Documentation**  
   https://flask.palletsprojects.com/

2. **Werkzeug Documentation**  
   https://werkzeug.palletsprojects.com/

3. **Three.js Documentation**  
   https://threejs.org/docs/

4. **Three.js OrbitControls**  
   https://threejs.org/docs/#examples/en/controls/OrbitControls

5. **Cloudflare Tunnel Documentation**  
   https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/

6. **Cloudflared GitHub Repository**  
   https://github.com/cloudflare/cloudflared

7. **Google Colab**  
   https://colab.research.google.com/

8. **Python Documentation**  
   https://docs.python.org/3/