习题2.19
棒球运动轨迹受空气影响，以及棒球自旋影响，使得球的轨迹十分复杂，本题讨论的是球的后自旋对射程的影响。
比较有自旋与无自旋状态
代码如下
import numpy as np
import pylab as pl
import math
v = 50
g = 9.8
angel = math.pi/4
vx1 = math.cos(angel)*v
vx2 = math.cos(angel)*v
vy1 = math.sin(angel)*v
vy2 = math.sin(angel)*v
x1 = 0
x2 = 0
y1 = 0
y2 = 0
dt = 0.05
X1 = [0]
X2 = [0]
Y1 = [0]
Y2 = [0]
while 1:
    B = 0.0039+0.0058/(1+math.exp((v-35)/5))
    S = 4.1*10**-4
    w = 66*math.pi
    x1 = x1+vx1*dt
    y1 = y1+vy1*dt
    vx1 = vx1-B*v*vx1*dt
    vy1 = vy1-g*dt-B*v*vy1*dt
    v = math.sqrt(vx1**2+vy1**2)
    X1.append(x1)
    Y1.append(y1)
    if Y1[-1]<0:
        break
while 1:
    B = 0.0039+0.0058/(1+math.exp((v-35)/5))
    S = 4.1*10**-4
    w = 66*math.pi
    x2 = x2+vx2*dt
    y2 = y2+vy2*dt
    vx2 = vx2-B*v*vx2*dt+S*vy2*w*dt
    vy2 = vy2-g*dt-B*v*vy2*dt-S*vx2*w*dt
    v = math.sqrt(vx2**2+vy2**2)
    X2.append(x2)
    Y2.append(y2)
    if Y2[-1]<0:
        break
def plot():
    pl.plot(X1,Y1,'r',label='no spin')
    pl.plot(X2,Y2,'b',label='backspin')
    pl.title('the trajectories of batted ball')
    pl.xlabel('x axis')
    pl.ylabel('y axis')
    pl.xlim(0.0,150.0)
    pl.ylim(0.0,50.0)
    pl.legend()
    pl.show()
plot() 
![image](https://github.com/whuttzg/computationalphysics_N2015301510092/blob/master/Exercise_05.png)
由此可见，球的自旋对落点有一定的影响，使其轨迹有更大的不确定性
