% I know you will come
% Send this to your girl/boy friend, don't thank me !
clc
clear
[X,Y,Z] = meshgrid(linspace(-3,3,101));
F = -X.^2.*Z.^3-(9/80).*Y.^2.*Z.^3+(X.^2+(9/4).*Y.^2+Z.^2-1).^3;
hFigure = figure;
sz = get(hFigure, 'Position');
set(hFigure, 'Position', [sz(1)-0.15*sz(3) sz(2) 1.3*sz(3) sz(4)]);
set(hFigure,'color','w', 'menu','none')
hAxes = axes('Parent',hFigure,'NextPlot','add',...
    'DataAspectRatio',[1 1 1],... 
    'XLim',[30 120],'YLim',[35 65],'ZLim',[30 75]);
view([-39 30]);
axis off
hidden on
p = patch(isosurface(F,-0.001));
set(p,'FaceColor','w','EdgeColor','none');
 
for iX = [35 38 41 45 48 51 54 57 61 64 67] 
    plane = reshape(F(:,iX,:),101,101);
    cData = contourc(plane,[0 0]);
    xData = iX.*ones(1,cData(2,1));
    plot3(hAxes,xData,cData(2,2:end),cData(1,2:end),'k');
    pause(.1), drawnow
end
 
for iY = [41 44 47 51 55 58 61]
    plane = reshape(F(iY,:,:),101,101);
    cData = contourc(plane,[0 0]); 
    yData = iY.*ones(1,cData(2,1));
    plot3(hAxes,cData(2,2:end),yData,cData(1,2:end),'k');
    pause(.1), drawnow
end
for iZ = [36 38 40 42 44 46 48 50 52 54 56 58 60 62 64 66 69 71]
    plane = F(:,:,iZ);
    cData = contourc(plane,[0 0]); 
    startIndex = 1; 
    if size(cData,2) > (cData(2,1)+1) 
        startIndex = cData(2,1)+2;
        zData = iZ.*ones(1,cData(2,1)); 
        
        plot3(hAxes,cData(1,2:(startIndex-1)),...
            cData(2,2:(startIndex-1)),zData,'k');
    end
    zData = iZ.*ones(1,cData(2,startIndex));
    plot3(hAxes,cData(1,(startIndex+1):end),...
        cData(2,(startIndex+1):end),zData,'k');
    pause(.1), drawnow
end
set(p,'faceColor','r','EdgeColor','w');
pause(.2)
set(p,'faceColor','w','EdgeColor','r')
pause(.2)
text(7,50,70,'I', 'fontWeight','bold','FontAngle','italic','fontsize',100)
pause(.5)
text(80,50,43,'YOU', 'fontWeight','bold','FontAngle','italic','fontsize',100)
pause(.2)
%设置签名
line([20 80],[50 50],[52.5 52.5], 'color','k')
line([50 50],[20 80],[52.5 52.5], 'color','k')
line([50 50],[50 50],[30 80], 'color','k')
text(20,50,50,'x')
text(48,20,50,'y')
text(45,50,80,'z')
text(30,60,30,'(x^2+9/4y^2+z^2-1)^3');
