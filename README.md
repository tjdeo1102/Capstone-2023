# 전북대학교xLX 캡스톤디자인 2023

---
해당 프로젝트는 전북대학교와 LX의 도움으로 제작된 프로젝트로 하천부근 불법 점용 객체를 탐지하는 소프트웨어입니다.

소프트웨어를 제작하기 위해 YOLOV8, QGIS, pytorch, opencv, shapely가 사용되었습니다.

소프트웨어는 총 2가지 트랙으로 구분되어 진행되며, 각 과정을 수행하기 위한 환경을 만들어야 합니다.

첫번째 트랙에서는 객체를 탐지하는 과정이 진행됩니다.

두번째 트랙에서는 탐지된 객체가 불법인지 판단해주는 과정이 진행됩니다.

---
## 설치
1. 먼저 첫번째 트랙을 위해 VSCode에서 터미널에서 다음의 과정으로 Conda 가상환경을 준비해줍니다. (Conda가 설치되었다고 가정)

```python"
conda create -n [가상환경명] python=3.8

conda activate [가상환경명]
```
   
3. 다음의 필요한 라이브러리들을 설치해줍니다. (파이토치에 관한 설치는 따로 해주셔야 합니다.)

```python"
pip install shapely

pip install ultralytics
```
   
5. QGIS 3.32.3 버전을 설치해야 합니다. [다음](https://download.qgis.org/downloads/)의 링크를 통해 설치해주세요.
   
6. 사전에 드론맵을 준비해주세요(별도로 구해야됨)
   
7. 드론맵에 해당되는 지역의 행정데이터(토지소유정보)를 다음의 [링크](http://openapi.nsdi.go.kr/nsdi/index.do)를 통해 다운받습니다.
---
## 과정
---
### 첫번째 트랙
---
1. 1_YOLO폴더의 main.py을 열어줍니다.

2. input_orgin_tif_folder에는 예측할 이미지들이 있는 폴더로 설정해줍니다.

3. output_folder에는 저장할 경로로 설정해줍니다.

4. 미리 설치해둔 가상환경을 통해 main.py를 실행해줍니다.

5. 설치 후, 저장경로에 예측된 이미지와 객체에 대한 정보가 포함되어 있는 output.csv가 저장됩니다.
---
### 두번째 트랙
---
1. 미리 설치해둔 QGIS를 실행합니다.

2. 상단의 플러그인-플러그인 관리 및 설치-ZIP 파일에서 설치 순으로 들어갑니다.

3. 2_QGIS폴더에 있는 lllegar_checker.zip의 경로를 설정하고 플러그인 설치를 합니다.

4. 다시 상단의 플러그인-lllegalAreaChecker-lllegalAreaChecker 순으로 들어갑니다.

5. 나타난 팝업창에서 다음의 설명에 맞게 경로를 설정합니다.
   
   *Input Image: 예측할 원래 이미지들이 있는 경로입니다.
   
   *Check Opt
   
      +Bounding Box Centroid: 예측된 바운딩 박스의 무게중심을 기준으로 불법 객체를 판단합니다.
   
      +Polygon Box Centroid: 예측된 폴리곤 박스의 무게중심을 기준으로 불법 객체를 판단합니다.
   
   *Input dbf: 행정데이터(토지소유정보)가 있는 폴더 경로입니다.
   
   *Input model: 첫번째 트랙의 결과로 나온 Prediction폴더 경로입니다.
   
   *Output Path: 최종 결과를 저장할 경로입니다.

6. 확인을 눌러 작업을 시작합니다.

7. 최종 결과로 예측된 이미지들과 이미지들의 정보가 저장된 csv가 출력됩니다.
