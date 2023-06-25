#!/usr/bin/env python

import rospy
from geometry_msgs.msg import Twist

def move_robot():
    # Inisialisasi node ROS dengan nama "move_robot"
    rospy.init_node('move_robot', anonymous=True)
    
    # Membuat objek publisher untuk mengirim perintah ke topik '/cmd_vel'
    velocity_publisher = rospy.Publisher('/cmd_vel', Twist, queue_size=10)
    
    # Membuat objek pesan Twist untuk mengatur kecepatan robot
    vel_msg = Twist()
    
    # Menentukan kecepatan linear dan angular
    linear_speed = 0.2   # Kecepatan linear (m/s)
    angular_speed = 0.5  # Kecepatan angular (rad/s)
    
    # Mengisi nilai kecepatan linear dan angular pada pesan Twist
    vel_msg.linear.x = linear_speed
    vel_msg.angular.z = angular_speed
    
    # Menentukan waktu awal
    start_time = rospy.Time.now().to_sec()
    
    # Loop hingga robot bergerak selama 5 detik
    while rospy.Time.now().to_sec() - start_time < 5:
        # Mengirim pesan ke topik '/cmd_vel'
        velocity_publisher.publish(vel_msg)
    
    # Menghentikan robot dengan mengirim kecepatan nol
    vel_msg.linear.x = 0
    vel_msg.angular.z = 0
    velocity_publisher.publish(vel_msg)

if __name__ == '__main__':
    try:
        # Memanggil fungsi move_robot
        move_robot()
    except rospy.ROSInterruptException:
        pass
