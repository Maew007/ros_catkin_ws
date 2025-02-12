# ros_catkin_ws
สร้างไว้สำหรับการเก็บข้อมูลที่ใช้ในการเชื่อมต่อกับ ชุดจำลองการทำงาน ROS NOETIC  เพื่อเชื่อมกับ MovIT
เริ่มต้นการใช้งาน ROS Noetic

ขั้นที่ 1. ตรวจสอบสถานะก่อนว่า ัรนอยู่ในสภาพแวดล้อมของ conda ที่ใช้ทำงาน กับ Anaconda Navigator หรือเปล่า
       ตัวอย่าง อยู่ในสภาพแวดล้อมของ conda ที่ใช้ทำงาน กับ Anaconda Navigator
       (base)username@hostname:~/
       
       ตัวอย่าง ไม่อยู่ในสภาพแวดล้อมของ conda เป็นสถานะที่ต้องการ
       username@hostname:~/
       
ขั้นที่ 2. ทำการกำหนดไอพี ที่ต้องการใช้งาน 
       2.1 ถ้าต้องการกำหนดให้ใช้งาน ไอพี 127.0.0.1 ให้เรียกใช้คำสั่ง
           username@hostname:~/ iporg
       2.2 ถ้าต้องการกำหนดให้ใช้งาน ไอพี 10.1.63.44    ทำงานที่ ห้องทำงาน ตึก อิเล็กฯ ให้เรียกใช้คำสั่ง
           username@hostname:~/ ipelec
       2.3 ถ้าต้องการกำหนดให้ใช้งาน ไอพี 192.168.31.10 ทำงานที่ ห้องคอมฯ  ตึก อิเล็กฯ ให้เรียกใช้คำสั่ง
           username@hostname:~/ ipcomroomelec
       2.4 ถ้าต้องการกำหนดให้ใช้งาน ไอพี 192.168.1.50  ทำงานที่ Condo ให้เรียกใช้คำสั่ง
           username@hostname:~/ iphome
           
ขั้นที่ 3. ตรวจสอบผลการเปลี่ยนแปลงสภาพแวดล้อมด้วย คำสั่ง
       username@hostname:~/ cd catkin_ws
       username@hostname:~/catkin_ws/ . test_env.sh
       
       กรณีที่ไม่พบไฟล์นี้ให้ไปโหลดไฟล์นี้มาก่อนชื่อไฟล์ test_env.sh
       bash: test_env.sh :  No such  file or directory
       
       กรณีที่สามารถทำงานได้ถูกต้อง
        ROS เวอร์ชันที่ใช้ = 1
	ROS_PYTHON_VERSION = 3
	ROS_PACKAGE_PATH =/home/rospc/catkin_ws/src:/opt/ros/noetic/share
	ROS_PACKAGE_PATH= ROSLISP_PACKAGE_DIRECTORIES =/home/rospc/catkin_ws/devel/share/common-lisp
	ROS_ETC_DIR =/opt/ros/noetic/etc/ros
	ROS_MASTER_URI=http://127.0.0.1:11311
	ROS_LOCALHOST_ONLY=
	ROS_ROOT=/opt/ros/noetic/share/ros
	ROS_DISTRO=noetic
	ไอพีที่ใช้สำหรับเครื่อง Server http://127.0.0.1:11311
	ไอพีที่ใช้สำหรับเครื่องที่ทำหน้าที่เป็นโฮส 127.0.0.1
  
ขั้นที่ 4. ทดสอบ เรียกใช้คำสั่ง roscore เพื่อตรวจสอบว่า สร้างส่วนให้บริการ ROS Server ได้หรือไม่
       username@hostname:~/catkin_ws/ roscore
       
       กรณีที่สามารถทำงานได้ถูกต้อง
       
       username@hostname:~/catkin_ws$ roscore
		... logging to /home/rospc/.ros/log/e8ee946a-e917-11ef-a635-574f668e975e/roslaunch-rosnb-124211.log
		Checking log directory for disk usage. This may take a while.
		Press Ctrl-C to interrupt
		Done checking log file disk usage. Usage is <1GB.

		started roslaunch server http://127.0.0.1:33297/
		ros_comm version 1.17.0


		SUMMARY
		========

		PARAMETERS
		 * /rosdistro: noetic
		 * /rosversion: 1.17.0

		NODES

		auto-starting new master
		process[master]: started with pid [124219]
		ROS_MASTER_URI=http://127.0.0.1:11311/

		setting /run_id to e8ee946a-e917-11ef-a635-574f668e975e
		process[rosout-1]: started with pid [124229]
		started core service [/rosout]

ส่วนที่ 2. ทดสอบการทำการ make file จะมีการทำงานคล้ายกับคอมไพเลอร์ ด้วยคำสั่ง catkin_make หากพบตัวอย่างให้ใช้ catkin build ให้ใช้ catkin_make  แทน
              
ขั้นที่ 5. ทดสอบการทำการ make file 
       5.1โดยการเข้าไปใน พื้นที่ๆ สร้างขึ้นในตัวอย่างทั่วๆ ไป จะใช้ชื่อ CATKIN_WS
          cd ~/catkin_ws
       5.2 ตรวจสอบว่ามี directory ชื่อ /src หรือไม่ ถ้าไม่มี ตั้งแต่ ขั้นตอนหาไดเรกทอรี ชื่อ catkin_ws ให้ใช้คำสั่ง
          mkdir -p ~/catkin_ws/src
       5.3 ไปทำขั้นตอนที่ 5.1 และให้เรียกใช้งานคำสั่ง catkin_make
       ผลลัพธ์เมื่อทำงาน ได้ 100% แสดงว่าสามารถทำงานได้อย่างถูกต้อง โดยไม่ต้องสนใจชื่อ ของแพคเก็ตที่ทำการคอมไพล์
       	[  0%] Built target trajectory_msgs_generate_messages_py
		[ 50%] Built target turtlebot3_fake_node
		[100%] Built target turtlebot3_drive
   

ส่วนที่  3   -------------- การใช้งาน  Github  ---------------------
		echo "# ros_catkin_ws" >> README.md
		git init
		git add README.md
		git commit -m "first commit"
		git branch -M main
		git remote add origin https://github.com/Maew007/ros_catkin_ws.git
		git push -u origin main



		git remote add origin https://github.com/Maew007/ros_catkin_ws.git
		git branch -M main
		git push -u origin main
