%用matlab实现最速下降法

function A=CountA(f,a,b)%此函数功能是计算A的值
df1=diff(f,'x1');df2=diff(f,'x2');%分别对x1,x2求一次偏导数
df11=diff(f,'x1',2);
df12=diff(df1,'x2');
df21=diff(df2,'x1');
df22=diff(f,'x2',2);%分别求出四个二阶偏导数的值
x1=a;x2=b;%给x1,x2传入值
m=subs(df11);
n=subs(df12);
i=subs(df21);
j=subs(df22);%将值带入四个二阶偏导数中，求出对应偏导数的值
A=[m,n;i,j];%返回A的值
end


function z=Alpha(f,epsilon,a,b)%通过此函数求出每一次迭代的x坐标
x1=a;x2=b;%将a,b的值传入x1,x2中
A=CountA(f,x1,x2);%获得A的值
x0=[x1,x2]';%将x1,x2放入矩阵x0中，作为迭代的起点
df1=diff(f,'x1');%对x1求一阶偏导
df2=diff(f,'x2');%对x2求一阶偏导
grad=[df1,df2]';%求出f的梯度
g=subs(grad);%将数值代入，得到该点的梯度大小
p=-g;%求出p,为下面算alpha做准备
puts=x0;%puts矩阵的作用是记录每一次迭代出来的结果，保留迭代的过程
while(norm(abs(g))>epsilon)%当被epsilon条件限制时，不断进行迭代
    alpha=(p)'*p/((p)'*A*p);%计算alpha的值
    x0=x0+alpha*p;%更新x0的值
    puts=[puts;x0];%将迭代出来的结果放入puts矩阵中记录
    a=[1,0]*x0;b=[0,1]*x0;
    x1=a;x2=b;%更新x1的值
    g=subs(grad);%更新该点梯度值
    p=-g;%更新p值
end
z=puts;%返回puts矩阵
end

syms x1 x2 %设置变量x1,x2
X=[x1,x2]; %将x1,x2放入矩阵X中
fx=2*X(1)^2+4*X(2)^2-6*X(1)-2*X(1)*X(2);%构造目标函数fx
epsilon=0.1;%给定一个epsilon的值作为边界
a=1;b=1;%给定初始位置x0
z=Alpha(fx,epsilon,a,b)%传入函数计算

%% 用surf和mesh的作图
clear; clc; close all;
x = -10:0.1:10; y = -10:2:10;
[X,Y] = meshgrid(x,y);  % 获取网格
Z = 2*X.^2+4*Y.^2-6*X-2*X.*Y;  % 设定Z的范围
subplot(1,2,1); 
mesh(X,Y,Z);  % 显示绘图的线，但是表格中间没有填充颜色
title('mesh draw');
subplot(1,2,2); 
surf(X,Y,Z);  % 显示绘图的线，表格中间有填充的颜色
title('surf draw');
