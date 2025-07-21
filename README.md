# mycobot_moveit_config
## 確認環境
2025年7月21日時点

環境：Ubuntu22.04

ROS 2 version : Humble

ロボットモデル： mycobot（`https://docs.elephantrobotics.com/docs/gitbook-en/2-serialproduct/2.1-280/2.1.4.1%20Introduction%20of%20product%20parameters.html`）

## 動作手順
### 1 必要なパッケージのインストール

```bash
sudo apt update
sudo apt install -y \
  ros-humble-moveit \
  ros-humble-gazebo-ros-pkgs \
  ros-humble-ros2-control \
  ros-humble-ros2-controllers \
  ros-humble-ros-gz \
  ros-humble-xacro
```

### 2 必要なパッケージのインストール

```bash
sudo apt update
sudo apt install -y \
  ros-humble-moveit \
  ros-humble-gazebo-ros-pkgs \
  ros-humble-ros2-control \
  ros-humble-ros2-controllers \
  ros-humble-ros-gz \
  ros-humble-xacro
```
### 2 ファイルのダウンロード 
任意の`ros2`ワークスペースの`src`ディレクトリに移動し、`mycobot_moveit_config`をダウンロードする。

URDFファイルを下記コマンドで`/opt/ros/humble/share/moveit_setup_assistant`へコピーしておく。管理者権限ではないとコピーできない場所なのでsudoを使うこと。
```bash
cd mycobot_moveit_config
sudo cp mycobot.urdf /opt/ros/humble/share/moveit_setup_assistant
```

### 3 ビルドと実行
#### 3.1 ビルド
ワークスペースのルートディレクトリに戻り、ビルドします。
```bash
cd ../..
source /opt/ros/humble/setup.bash
colcon build --packages-select mycobot_moveit_config
```
#### 3.2 実行
```bash
source install/setup.bash
```
#### 3.3 RVizの起動
```bash
ros2 launch mycobot_moveit_config demo.launch.py
```

### 4 動作確認

1.  RVizの`MotionPlanning`パネルを開きます。
2.  `Planning`タブの`Query`セクションで、`Planning Group`が`mycobot`になっていることを確認します。
3.  3Dビュー内で、エンドエフェクタ（水色の球体）の先にあるインタラクティブマーカーをドラッグして、目標の姿勢（Goal State）を設定します。
4.  `Plan and Execute`ボタンをクリックします。
