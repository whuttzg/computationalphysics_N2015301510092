from __future__ import division#使得2/3不为0
import matplotlib.pyplot as plt  
import numpy as np
import math
def pendulum(FD):  #定义关于FD的函数
    plt.figure('graph z')
    w=[0 for x in range(0,1501)]#创建数列   
    theta=[0 for x in range(0,1501)]
    E=[0 for x in range(0,1501)]
    t=[0 for x in range(0,1501)]
    theta[0]=0.2#定义初始量
    w[0]=0
    t[0]=0
    dt=0.04
    for i in range(0,1500):#使用for循环语句 实现叠加
        w[i+1]=w[i] + (-math.sin(theta[i]) - 0.5 * w[i] + FD * math.sin((2/3) * t[i])) * dt#使用euler_cromer法构造叠加语句
        theta[i+1]=theta[i]+w[i+1]*dt
        while 1:                          #使用while循环使得theta处于-pi到pi之间
            if (theta[i+1]<-1*math.pi):
               theta[i+1]=theta[i+1]+2*math.pi
            if (theta[i+1]>math.pi):
               theta[i+1]=theta[i+1]-2*math.pi
            if (theta[i+1]>=-1*math.pi and theta[i+1]<=math.pi):
               break
        t[i+1]=t[i]+dt
        E[i] = 0.5 * (w[i] ** 2) * (9.8 ** 2) + 9.8 * 9.8 * (1 - math.cos(theta[i]))
    plt.figure('theta')#画出图像
    plt.xlabel("t")
    plt.ylabel("theta")
    plt.plot(t,theta)
    plt.figure('E')#画出图像
    plt.xlabel("t")
    plt.ylabel("E")
    plt.plot(t,E)
    plt.show()
pendulum(0) #运行函数
