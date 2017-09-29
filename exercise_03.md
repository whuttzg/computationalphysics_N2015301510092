from scipy.integrate import odeint 
import numpy as N
import matplotlib.pyplot as plt
def f(y,t):
    return 10-y #常微分方程的形式
y0=0 #初始速度
a=0 #初始时间
b=20#停止时间
t=N.arange(a,b,0.00001)#规定计算步长
y=odeint(f,y0,t)#使用obeint函数求解    
plt.plot(t,y,'b')#将结果绘制成曲线   
plt.xlabel('time')#定义x轴为时间 
plt.title('velocity')#定义y轴为速度
plt.ylim([0,15]) #选择y轴的显示范围
plt.show #绘制成图
