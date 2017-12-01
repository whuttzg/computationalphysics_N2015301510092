4.16
模拟地球，木星和太阳的三体运动。同时改变木星的质量，探究质量不同时的轨迹有何区别。
由于是三体运动，计算其中之一的坐标时，要同时考虑另外两个星体对其的引力作用。 
代码如下：
k=float(input('please input the mass of the sun divided by the mass of the Jupiter='))
Gms=4*math.pi*math.pi
Gme=Gms/330000
Gmj=Gms/kx1=[-2.066]
y1=[0]
x2=[-1.066]
y2=[0]
x3=[3.133] 
y3=[0]
vx1=[0]
vy1=[-0.0004415*math.sqrt(Gms/1)]
vx2=[0] 
vy2=[math.sqrt(Gms/1)] 
vx3=[0]
vy3=[math.sqrt(Gms/5.2)]
t=[0]
dt=0.002
while t[-1]<20:
r12=math.sqrt((x1[-1]-x2[-1])**2+(y1[-1]-y2[-1])**2)
r13=math.sqrt((x1[-1]-x3[-1])**2+(y1[-1]-y3[-1])**2)
r23=math.sqrt((x2[-1]-x3[-1])**2+(y2[-1]-y3[-1])**2)

ox1=-Gme*(x1[-1]-x2[-1])/(r12**3)-Gmj*(x1[-1]-x3[-1])/(r13**3)
ox2=-Gms*(x2[-1]-x1[-1])/(r12**3)-Gmj*(x2[-1]-x3[-1])/(r23**3)
ox3=-Gms*(x3[-1]-x1[-1])/(r13**3)-Gme*(x3[-1]-x2[-1])/(r23**3)

oy1=-Gme*(y1[-1]-y2[-1])/(r12**3)-Gmj*(y1[-1]-y3[-1])/(r13**3)
oy2=-Gms*(y2[-1]-y1[-1])/(r12**3)-Gmj*(y2[-1]-y3[-1])/(r23**3)
oy3=-Gms*(y3[-1]-y1[-1])/(r13**3)-Gme*(y3[-1]-y2[-1])/(r23**3)

vx1.append(vx1[-1]+ox1*dt)
vx2.append(vx2[-1]+ox2*dt)
vx3.append(vx3[-1]+ox3*dt)

vy1.append(vy1[-1]+oy1*dt)
vy2.append(vy2[-1]+oy2*dt)
vy3.append(vy3[-1]+oy3*dt)

x1.append(x1[-1]+vx1[-1]*dt)
x2.append(x2[-1]+vx2[-1]*dt)
x3.append(x3[-1]+vx3[-1]*dt)

y1.append(y1[-1]+vy1[-1]*dt)
y2.append(y2[-1]+vy2[-1]*dt)
y3.append(y3[-1]+vy3[-1]*dt)

t.append(t[-1]+dt)
fig=matplotlib.pyplot.figure(figsize=[8,8])
matplotlib.pyplot.plot(x1,y1,label='Sun',linewidth=2)
matplotlib.pyplot.plot(x2,y2,label='Earth') 
matplotlib.pyplot.plot(x3,y3,label='Jupiter') 
matplotlib.pyplot.legend(loc='upper right')
matplotlib.pyplot.xlabel('x(AU)')
matplotlib.pyplot.ylabel('y(AU)')
matplotlib.pyplot.title('ms=1mj')
matplotlib.pyplot.xlim(-5,5) 
matplotlib.pyplot.ylim(-2,15)
木星为其真实质量时：
![image](https://github.com/whuttzg/computationalphysics_N2015301510092/blob/master/Exercise_10%2001.png)
木星为真实质量的十倍时：
![image](https://github.com/whuttzg/computationalphysics_N2015301510092/blob/master/Exercise_10%2002.png)
木星为真实质量的100倍时：
！[image](https://github.com/whuttzg/computationalphysics_N2015301510092/blob/master/Exercise_10%2003.png)
木星为其质量1000倍时：
![image](https://github.com/whuttzg/computationalphysics_N2015301510092/blob/master/Exercise_10%2004.png)
由此可见，当木星质量越大，地球轨道扰动越大
在此感觉麻家兴同学的帮助！
