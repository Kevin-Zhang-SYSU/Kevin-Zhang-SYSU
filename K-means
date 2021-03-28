%在matlab里实现K-means算法

clear; %清除工作空间的内容
clc; %清除命令窗口的内容
data=xlsread('sonar.xls','A1:BH208'); %读取excel文件里的数据
daan=xlsread('sonar.xls','BI1:BI208'); %读取最后一列作为分类的标准答案
[m,n]=size(data); %m为行数，n为列数
C1=data(randperm(m,1),:); %随机初始化第一个聚类中心
C2=data(randperm(m,1),:); %随机初始化第二个聚类中心
pd=zeros(m,100); %创建一个矩阵存放每一个点所属的类
num=0; %初始化迭代次数
L1=zeros(1,n); %初始化存放第一类点的矩阵
L2=zeros(1,n); %初始化存放第一类点的矩阵
distance=[]; %建立一个矩阵，记录两个中心点随迭代次数改变而距离改变的值
while 1 %迭代开始
    L1=[]; %初始化存放第一类点的矩阵
    L2=[]; %初始化存放第一类点的矩阵
    numL1=0; %初始化每一类中点的个数
    numL2=0; %初始化每一类中点的个数
    num=num+1; %记录迭代的次数
    for i=1:m
        x_temp=data(i,:); %将每一个点都拿出来计算与两个中心点的距离
        d1=norm(x_temp-C1); %计算该点距离第一类中心点的距离
        d2=norm(x_temp-C2); %计算该点距离第二类中心点的距离
        if (d1<=d2) %若该点的距离到第一个中心点的距离更小
            pd(i,num)=1; %则将该点定义为第一类
            L1=[L1;data(i,:)]; %将该行向量存放到L1矩阵内
            numL1=numL1+1; %更新第一类中点的个数
        else
            pd(i,num)=2; %否则该点为第二类
            L2=[L2;data(i,:)]; %将该行向量存放到L2矩阵内
            numL2=numL2+1; %更新第二类中点的个数
        end
    end
    epsilon=0.01; %定义一个epsilon的值
    C11=C1; %保留前一次的第一类中心点C1
    C22=C2; %保留前一次的第一类中心点C2
    C1=mean(L1); %求出第一个簇的重心，更新中心点
    C2=mean(L2); %求出第二个簇的重心，更新中心点
    distance=[distance;norm(C11-C22)]; %记录最新中心点的距离
    dc1=norm(C1-C11); %计算第一个簇前后两个中心点的距离
    dc2=norm(C2-C22); %计算第二个簇前后两个中心点的距离
    if (dc1<epsilon&&dc2<epsilon) %判断距离是否小于epsilon
        break; %若小于epsilon，则停止迭代
    end
end
Center=[C1;C2]; %输出两个中心点
%现在开始计算每一次迭代的正确率，并作图
accuracy=zeros(1,num); %创建一个存放每一次迭代正确率的矩阵
for i=1:num  %每一列比较
    trueA=0; %初始化第一种情况对的个数
    trueB=0; %初始化第二种情况对的个数
    for j=1:m
        if(abs(daan(j,1)-pd(j,i))==1) %第一种情况，比较第i次迭代出的结果分类与标准分类相反
            trueA=trueA+1; %更新对的个数
        end
    end
    for j=1:m
        if(abs(daan(j,1)-pd(j,i))==0) %第二种情况，比较第i次迭代出的结果分类与标准分类相同
            trueB=trueB+1;  %更新对的个数
        end
    end
    if (trueA>=trueB) %比较两种情况对的个数，保证迭代的正确率最大
        true=trueA; %将正确率相对较高的情况保留
    end
    if (trueA<trueB) %比较两种情况对的个数，保证迭代的正确率最大
        true=trueB; %将正确率相对较高的情况保留
    end
    zql=true/m; %计算正确率
    accuracy(1,i)=zql; %将每一次的正确率保留到矩阵内
end
disp(Center); %输出两个中心点
t=1:1:num;
ax1=subplot(2,1,1); %创建子图一
plot(ax1,t,accuracy,'r-*'); %作出正确率随迭代次数更新而变化的图像
title(ax1,'K-means accuracy curve'); %设置图像标题
xlabel(ax1,'number of iterations'); %设置x轴说明
ylabel(ax1,'accuracy'); %设置y轴说明
distance=distance'; %列向量转置为行向量
k=1:1:num;
ax2=subplot(2,1,2); %创建子图二
plot(ax2,k,distance,'c-o'); %作出两个簇心随迭代次数改变距离的改变图像
title(ax2,'K-means heart distance cluster'); %设置图像标题
xlabel(ax2,'number of iterations'); %设置x轴说明
ylabel(ax2,'heart distance cluster'); %设置y轴说明
            
        

        
        
        
        
        
        
        
        
        
        
        
