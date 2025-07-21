# mycobot
## 動作手順
URDFファイルを下記コマンドで`/opt/ros/humble/share/moveit_setup_assistant`へコピーしておく。管理者権限ではないとコピーできない場所なのでsudoを使うこと。

        cd mycobot_moveit_config
        sudo cp mycobot.urdf /opt/ros/humble/share/moveit_setup_assistant

        cd ../..
        source /opt/ros/humble/setup.bash
        colcon build --packages-select mycobot_moveit_config
        source install/setup.bash
        ros2 launch mycobot_moveit_config demo.launch.py
