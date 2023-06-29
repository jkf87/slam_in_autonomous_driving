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
    - 책의 각 장에는 다음과 같은 역동적인 프레젠테이션이 함께 제공됩니다:

![](./doc/lio_demo.gif)
![](./doc/2dmapping_demo.gif)
![](./doc/lo_demo.gif)

이 책의 미니멀한 스타일을 즐기고 알고리즘의 재미를 발견하시길 바랍니다.。

## 数据集

- 数据集下载链接：
- 百度云链接: https://pan.baidu.com/s/1ELOcF1UTKdfiKBAaXnE8sQ?pwd=feky 提取码: feky
- OneDrive链接：https://1drv.ms/u/s!AgNFVSzSYXMahcEZejoUwCaHRcactQ?e=YsOYy2 

- 包含以下数据集。总量较大(270GB)，请视自己硬盘容量下载。
    - UrbanLoco (ULHK，3D激光，道路场景)
    - NCLT (3D激光，RTK，校园场景)
    - WXB (3D激光，园区场景)
    - 2dmapping (2D激光，商场场景)
    - AVIA (大疆固态激光)
    - UTBM (3D激光，道路场景)
- 其他的内置数据
    - 第3,4章使用文本格式的IMU，RTK数据
    - 第7章使用了一部分EPFL的数据作为配准点云来源
- 您应该将上述数据下载至./dataset/sad/目录下，这样许多默认参数可以正常工作。如果不那么做，您也可以手动指定这些文件路径。如果您硬盘容量不足，可以将其他硬盘的目录软链至此处。

## 编译

- 本书推荐的编译环境是Ubuntu 20.04。更老的Ubuntu版本需要适配gcc编译器，主要是C++17标准。更新的Ubuntu则需要您自己安装对应的ROS版本。
- 在编译本书代码之前，请先安装以下库（如果您机器上没有安装的话）
    - ROS Noetic: http://wiki.ros.org/noetic/Installation/Ubuntu
    - 使用以下指令安装其余的库
    ```bash
    sudo apt install -y ros-noetic-pcl-ros ros-noetic-velodyne-msgs libopencv-dev libgoogle-glog-dev libeigen3-dev libsuitesparse-dev libpcl-dev libyaml-cpp-dev libbtbb-dev libgmock-dev
    ```
    - Pangolin: 编译安装thirdparty/pangolin.zip，或者 https://github.com/stevenlovegrove/Pangolin
    - 编译thirdparty/g2o，或者自行编译安装 https://github.com/RainerKuemmerle/g2o 
    - 通过cmake, make安装本repo下的`thirdparty/g2o`库
- 之后，使用通常的cmake, make方式就可以编译本书所有内容了。例如
```bash
mkdir build
cd build
cmake ..
make -j8
```
- 编译后各章的可执行文件位于`bin`目录下

### 适配Ubuntu18.04

为了在Ubuntu18.04上编译运行，需要安装gcc-9，并且使用对应版本的TBB。或者在docker环境下使用。

**安装gcc-9**
```bash
sudo add-apt-repository ppa:ubuntu-toolchain-r/test
sudo update-alternatives --remove-all gcc
sudo update-alternatives --remove-all g++

#命令最后的1和10是优先级，如果使用auto选择模式，系统将默认使用优先级高的
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-7 1
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-9 10

sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-7 1
sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-9 10
```

**检查版本**
```bash
g++ -v
```

**编译程序**
```bash
mkdir build
cd build
cmake .. -DBUILD_WITH_UBUNTU1804=ON
make -j8
```

**在docker环境下使用**
```bash
docker build -t sad:v1 .
./docker/docker_run.sh
```
进入docker容器后
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

## 常见问题
1. 图形界面在2023年以后特定型号的笔记本端导致桌面卡死（GL硬件兼容性）：https://github.com/gaoxiang12/slam_in_autonomous_driving/issues/67 
2. 第5章test_nn编译时，gtest报gmock错误：https://github.com/gaoxiang12/slam_in_autonomous_driving/issues/18
3. 编译器版本问题：https://github.com/gaoxiang12/slam_in_autonomous_driving/issues/4 

## TODO项

- 一部分插图需要授权
- 整理数据集（增加几个seq）
- 第9章前端第0个关键帧貌似有问题
- LioPreiteg在某些数据集上不收敛

## NOTES

- [已确认] ULHK的IMU似乎和别家的不一样，已经去了gravity
- [已确认] NCLT的IMU在转包的时候转成了Lidar系，于是Lidar与IMU之间没有旋转的外参（本来Lidar是转了90度的），现在Lidar是X左Y后Z下，原车是X前Y右Z下。本书使用的NCLT数据均基于点云系,
  IMU的杆臂被忽略。
- [已确认] NCLT的rtk fix并不是非常稳定，平均误差在米级
