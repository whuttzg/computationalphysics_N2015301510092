题目 3.20
代码如下：import pylab as pl
import math
class bifurcation_diagram:
    def __init__(self,q=0.5,g=9.8,l=9.8,OmegaD=2.0/3.0,FD=1.35,theta=0.20):
        self.omega=[0]
        self.theta=[theta]
        self.q=q
        self.g=g
        self.l=l
        self.OmegaD=OmegaD
        self.FD=FD
        self.t=[0]
        self.dt=2*math.pi/(500*OmegaD)
        self.Theta=[]
        self.Omega=[]
        self.fd=[]
    def calculate(self):
        for i in range(25000):
            self.t.append(self.t[i] + self.dt)
            omega1=self.omega[-1]-(self.g/self.l)*\
            math.sin(self.theta[-1])*self.dt -self.q*self.omega[-1]*self.dt +\
            self.FD*math.sin(self.OmegaD*self.t[-1])*self.dt
            self.omega.append(omega1)            
            #这是omega（i+1）的算式
            theta1=self.theta[-1]+self.omega[-1]*self.dt
            #这是theta（i+1）
            while(theta1>=math.pi):
                 theta1-=2*math.pi
            while(theta1<=-math.pi):
                 theta1+=2*math.pi
            self.theta.append(theta1)
        for i in range(40):
            self.Theta.append(self.theta[500*(i+7)])
            self.Omega.append(self.omega[500*(i+7)])
            self.fd.append(self.FD)
    def show_results(self):
        pl.plot(self.fd, self.Theta,'b.')
        pl.title('$Bifurcatioin$ $diagram$')
        pl.xlabel('$F_{D}$')
        pl.ylabel('$\\theta$(radians)')
for i in range(150):
    a=bifurcation_diagram(FD=1.34+i/1000.0)
    a.calculate()
    a.show_results()
 ![image](https://github.com/whuttzg/computationalphysics_N2015301510092/blob/master/Exercise07.png)
 由此得到对应关系图
