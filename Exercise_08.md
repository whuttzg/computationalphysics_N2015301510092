3.31
模拟当一个方形的边界内有一个圆形内边界的情况 
代码如下：
import pylab as pl
import math
class billiard_problem:
    def __init__(self,x0=0.78,y0=0.99,x1=-1.0,x2=1.5,y1=-1.0,y2=1.5,R=0.5,
                   v0=0.2,theta0=math.pi/7,dt=0.002):
        self.x=[x0]
        self.y=[y0]
        self.x1=x1
        self.x2=x2
        self.y1=y1
        self.y2=y2
        self.r=R
        self.vx=[v0*math.cos(theta0)]
        self.vy=[v0*math.sin(theta0)]
        self.v0=v0
        self.theta=[theta0]
        self.t=[0]
        self.dt=dt
        self.cx=[R]
        self.cy=[0]
    def run(self):
        i=0
        while(i<=800000):
            if not (self.x1<=self.x[-1]<=self.x2):
                self.theta.append(math.pi-self.theta[-1])
            if not (self.y1<=self.y[-1]<=self.y2):
                self.theta.append(-self.theta[-1])                           
            if (self.x[-1]**2+self.y[-1]**2<=self.r**2):
                self.theta.append(2*math.atan(self.vy[-1]/self.vx[-1])+math.atan(self.y[-1]/self.x[-1]))              
            #遇到边界时反向
            self.vx.append(self.v0*math.cos(self.theta[-1]))
            self.vy.append(self.v0*math.sin(self.theta[-1]))
            self.x.append(self.x[-1]+self.vx[-1]*self.dt)
            self.y.append(self.y[-1]+self.vy[-1]*self.dt)
            self.t.append(self.t[-1]+self.dt)
            i=i+1
    def drawcircle(self):
        i=0
        while (i<2*math.pi):
            self.cx.append(self.r*math.cos(i))
            self.cy.append(self.r*math.sin(i))
            i=i+0.01
    def showresult(self):
        pl.plot(self.x,self.y,)
        pl.plot(self.cx,self.cy,'r.')
        pl.xlim(self.x1,self.x2)
        pl.ylim(self.y1,self.y2)
        pl.xlabel("x")
        pl.ylabel("y")
        pl.show()
a=billiard_problem()
a.run()
a.drawcircle()
a.showresult()
1.圆形内边界在中心
