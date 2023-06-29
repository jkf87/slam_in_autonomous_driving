## SLAM in Autonomous Driving book (SAD book)

이 책은 관성 항법, 결합 항법, 레이저 지도 구축, 레이저 포지셔닝, 레이저 관성 주행 거리계 등에 대한 체계적인 소개를 제공합니다. 이 리포지토리는 책에 해당하는 소스 코드 리포지토리이며 공개적으로 사용할 수 있습니다.。

## 주의

- 이 책의 본문은 현재 검토 중입니다. 이 책의 리뷰어가 되고 싶으시면 gao.xiang.thu at gmail.com으로 문의하시기 바랍니다.
- 검토자가 되면 매일 업데이트되는 원고의 PDF에 액세스할 수 있습니다. 또한 2개월 이내에 의견에 대한 피드백을 주셔야 합니다. 다음 주소로 피드백을 보내주세요.  이슈나 이메일 형태로 의견을 보내주세요.
- 이 책의 1차 원고는 2023년 3월 말에 1차 마감되며, 원고를 출판사로 보내 처리할 예정이므로 검토자에게 검토 의견을 계속 업데이트해 주시기 바랍니다. 물론 이후 문제는 출판 인쇄와 함께 수정될 예정이지만, 감사 목록에 이름이 제때 업데이트되지 않을 수도 있습니다.
- 이 책은 최종 검토 단계(2023.6.14)에 있으며 7월에 독자들에게 공개될 예정입니다. 개인적으로 출판사와 함께 몇 가지 활동(할인, 사인회)을 진행한 후 영어 번역본이 어떻게 출시되는지 지켜볼 수 있을 것 같습니다.
- 이 책에 대한 몇 가지 후기를 작성하고 싶으시면 개인적으로 저에게 연락해 주세요. 추천사는 책의 서문 섹션이나 책 뒷표지에 실릴 것입니다.
  
##책의 구성

- 1장, 개요
- 2장, 수학적 기초, 기하학, 운동학, KF 필터 이론, 행렬 거짓말 그룹 복습
- 3장, 오류 상태 칼만 필터, 관성 항법, 위성 항법, 결합 항법
- 4장, 미적분학, 그래프 최적화, 미적분학 기반 조합 탐색
- 5장, 기본 포인트 클라우드 처리, 다양한 최인접 구조, 포인트 클라우드의 선형 피팅
- 6장, 2D 레이저 구축, 스캔 매칭, 가능성 필드, 서브맵, 2D 루프백 감지, 포즈 그래프
- 7장, 3D 레이저 빌딩, ICP, 변형 ICP, NDT, NDT LO, Loam-like LO, LIO 루스 커플링
- 8장, 긴밀하게 결합된 LIO, IESKF, 사전 통합된 긴밀하게 결합된 LIO
- 9장, 오프라인 지도 구축, 프론트엔드, 백엔드, 배치 루프백 감지, 지도 최적화, 슬라이스 내보내기- 10장, 퓨전 포지셔닝, 레이저 포지셔닝, 초기화 검색, 슬라이스 맵 로드, EKF 퓨전

##이 책의 특징

- 이 책은 아마도 유사한 자료 중 가장 간단한 수학적 도출과 코드 구현을 다룬 책일 것입니다.
- 이 책에서는 레이저 SLAM에 사용되는 많은 고전적인 알고리즘과 데이터 구조를 재현합니다.
    - 오류 상태 칼만 필터(ESKF)를 직접 도출 및 구현하고, IMU 및 GNSS에서 데이터를 공급하고, 자체 상태를 도출하는 방법을 확인해야 합니다.
    - 또한 사전 포인트 시스템으로 동일한 기능을 구현한 다음 작동 방식을 비교할 수 있습니다.
    - 다음으로 스캔 매칭, 가능성 필드, 하위 맵, 래스터 점유, 루프백 감지 등 2D 레이저 SLAM의 일반적인 알고리즘을 구현하여 더 큰 맵을 구축합니다. 이 모든 과정을 직접 수행해야 합니다.
    - 레이저 SLAM에서는 대략적인 가장 가까운 이웃을 다루면서 Kd 트리를 한 번 직접 구현한 다음 이 Kd 트리를 사용하여 ICP, 점 표면 ICP를 구현하고 개선할 수 있는 부분을 논의합니다.
    - 그런 다음 고전적인 NDT 알고리즘을 구현하고 정렬 성능을 테스트한 다음 이를 사용하여 레이저 주행 거리계를 구축합니다. 기존의 대부분의 LO보다 훨씬 빠릅니다.
    - 또한 매우 빠른 점 표면 ICP 레이저 주행 거리계를 구현합니다. Loam과 비슷한 방식으로 작동하지만 훨씬 더 간단합니다.
    - 레이저 주행 거리계에도 IMU 시스템을 탑재하고 싶을 것입니다. 느슨하게 결합된 LIO 시스템과 긴밀하게 결합된 LIO 시스템을 모두 구현할 것입니다. 다시 한 번 반복적인 칼만 필터와 사전 통합된 그래프 최적화를 도출해야 합니다.
    - 루프백 감지를 더 완벽하게 실행하려면 위의 시스템을 오프라인으로 실행하도록 변경해야 합니다. 마지막으로 오프라인 지도 구축 시스템으로 만듭니다.
    - 마지막으로, 위의 맵을 잘게 잘라 실시간 포지셔닝에 사용할 수 있습니다.
    - 이 책에 나오는 대부분의 구현은 유사한 알고리즘 라이브러리보다 훨씬 간단합니다. 복잡한 인터페이스를 다루지 않고도 작동 방식을 빠르게 이해할 수 있습니다.
    - 이 책에서는 매우 편리한 동시 프로그래밍을 사용합니다. 이 책의 구현이 기존 알고리즘보다 더 효율적인 경우가 많다는 것을 알게 될 것입니다. 물론 이는 부분적으로 역사적인 이유 때문이기도 합니다.
    - 책의 각 장에는 다음과 같은 동적 데모가 함께 제공됩니다:

![](./doc/lio_demo.gif)
![](./doc/2dmapping_demo.gif)
![](./doc/lo_demo.gif)

이 책의 미니멀한 스타일을 즐기고 알고리즘의 재미를 발견하시길 바랍니다.。

## 数据集

- 데이터 세트 다운로드 링크：
- 바이두 클라우드 링크: https://pan.baidu.com/s/1ELOcF1UTKdfiKBAaXnE8sQ?pwd=feky 출금 코드: feky
- OneDrive 링크：https://1drv.ms/u/s!AgNFVSzSYXMahcEZejoUwCaHRcactQ?e=YsOYy2 

- 다음 데이터 세트가 포함되어 있습니다. 총 용량이 270GB로 크므로 하드 드라이브 용량에 따라 다운로드하시기 바랍니다.
    - UrbanLoco(ULHK, 3D 레이저, 도로 장면)
    - NCLT(3D 레이저, RTK, 캠퍼스 장면)
    - WXB(3D 레이저, 공원 장면)
    - 2D 매핑(2D 레이저, 쇼핑몰 장면)
    - AVIA(DJI 솔리드 스테이트 레이저)
    - UTBM(3D 레이저, 도로 장면)- 기타 기본 제공 데이터
    - 3,4장 텍스트 형식의 IMU, RTK 데이터 사용
    - 7장에서는 EPFL 데이터의 일부를 정렬 포인트 클라우드 소스로 사용합니다.
    -  위의 데이터를 . /dataset/sad/ 디렉터리에 다운로드해야 많은 기본 매개변수가 제대로 작동합니다. 그렇지 않은 경우 이러한 파일 경로를 수동으로 지정할 수도 있습니다. 하드 드라이브의 용량이 부족한 경우 여기에서 다른 하드 드라이브의 디렉터리를 소프트 링크할 수 있습니다.

##컴파일
- 이 책에서 권장하는 빌드 환경은 Ubuntu 20.04입니다. 이전 버전의 Ubuntu는 주로 C++17 표준인 gcc 컴파일러에 맞게 조정해야 합니다. 최신 우분투를 사용하려면 해당 ROS 버전을 직접 설치해야 합니다.
- 이 책의 코드를 컴파일하기 전에 다음 라이브러리를 설치하세요(머신에 설치되어 있지 않은 경우).
    - ROS Noetic: http://wiki.ros.org/noetic/Installation/Ubuntu
    - 나머지 라이브러리를 설치하려면 다음 명령을 사용합니다.
    ```bash
    sudo apt install -y ros-noetic-pcl-ros ros-noetic-velodyne-msgs libopencv-dev libgoogle-glog-dev libeigen3-dev libsuitesparse-dev libpcl-dev libyaml-cpp-dev libbtbb-dev libgmock-dev
    ```
    - Pangolin: thirdparty/pangolin.zip 또는 https://github.com/stevenlovegrove/Pangolin 을 컴파일하여 설치합니다.
    - thirdparty/g2o를 컴파일하거나 직접 컴파일 및 설치 https://github.com/RainerKuemmerle/g2o
    - cmake, make를 통해 이 저장소 아래에 thirdparty/g2o라이브러리를 설치합니다.
- 그런 다음 일반적인 cmake, make 메서드를 사용하여 책의 모든 내용을 컴파일할 수 있습니다. 예를 들면
```bash
mkdir build
cd build
cmake ..
make -j8
```
- 컴파일된 챕터의 실행 파일은 `bin` 디렉터리에 있습니다.

### Ubuntu18.04에 적용

우분투 18.04에서 컴파일하고 실행하려면 gcc-9을 설치하고 해당 버전의 TBB를 사용해야 합니다. 또는 도커 환경에서 사용하세요.

**gcc-9설치**
```bash
sudo add-apt-repository ppa:ubuntu-toolchain-r/test
sudo update-alternatives --remove-all gcc
sudo update-alternatives --remove-all g++

#명령 끝에 있는 1과 10은 우선순위 수준입니다. 자동 선택 모드를 사용하는 경우 시스템은 기본적으로 더 높은 우선순위를 사용합니다.
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-7 1
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-9 10

sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-7 1
sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-9 10
```

**버전확인**
```bash
g++ -v
```

**컴파일 프로그램**
```bash
mkdir build
cd build
cmake .. -DBUILD_WITH_UBUNTU1804=ON
make -j8
```

**도커 환경에서 사용**
```bash
docker build -t sad:v1 .
./docker/docker_run.sh
```
도커 컨테이너 진입 후
```bash
cd ./thirdparty/g2o
mkdir build
cd build
cmake ..
make -j8
cd /sad
mkdir build
cd build
cmake ..
make -j8
```

## 일반적인 문제
1. 그래픽 인터페이스는 2023년 이후 노트북의 특정 모델에서 데스크톱 지연을 유발합니다(GL 하드웨어 호환성).：https://github.com/gaoxiang12/slam_in_autonomous_driving/issues/67 
2. 5장 테스트_nn이 gtest에서 gmock 오류와 함께 컴파일됩니다.：https://github.com/gaoxiang12/slam_in_autonomous_driving/issues/18
3. 컴파일러 버전 문제：https://github.com/gaoxiang12/slam_in_autonomous_driving/issues/4 

## TODO 항목

- 일부 일러스트레이션은 라이선스가 필요합니다.
- 데이터 집합 대조（몇 가지 추가seq）
- 9장 앞부분의 0번째 키프레임에 문제가 있는 것 같습니다.
- LioPreiteg일부 데이터 집합에서 수렴되지 않음

## NOTES

- [확인] ULHK의 IMU는 다른 것과는 다르게 중력이 작용한 것 같습니다.
- [확인] NCLT의 IMU가 라이다 시스템으로 변환되었기 때문에 라이다와 IMU 사이의 회전에 대한 외부 참조가 없으며(원래 라이다는 90도 회전), 이제 라이다는 X 좌측 Y 후방 Z 아래, 원본은 X 전면 Y 오른쪽 Z 아래입니다. 이 책에서 사용된 NCLT 데이터는 포인트 클라우드 시스템을 기반으로 합니다.  IMU의 레버 암은 무시됩니다.
- [확인] NCLT의 rtk 수정은 미터 범위의 평균 오류로 매우 안정적이지 않습니다.
