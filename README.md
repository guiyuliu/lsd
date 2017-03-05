# lsd
# lsd在matlab中的编译及使用

标签（空格分隔）： 代码使用

---
##编译方法

`mex -O -output lsd lsd_matlab.c lsd.c`

将后面两个c文件整合起来变成一个mexw文件lsd.mexw64  
然后就可以像函数一样在matlab中调用lsd

###函数说明
%function lines=lsd(im)  
%INPUT  
%	im: double valued gray image  
%OUTPUT  
%	lines<Nx5>: line segments found in im, x1 y1 x2 y2 width  
###调用示例

    I=imread('test.png');
    I=rgb2gray(I);
    lines=lsd(double(I))
##编译error:
*无法解析的外部符号 mxErrMsgTxt，该符号在函数 mexFunction 中被引用*  
solution：在新的MATLAB版本中，mxErrMsgTxt函数已经被取消，意义为输出错误信息并终止程序，可修改lsd_Matlab.c如下：

    {
    mexPrintf("Not enough i/o parameters! exit...");
     return;
    }


