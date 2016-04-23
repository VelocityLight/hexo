---
title: Bezier Curve
date: 2016-03-11 23:28:40
tags:
- Bezier Curve
categories:
- IT
---
Bezier Curve Problem.<!--more-->
# Bezier Curve
[TOC]

## Question
> - 折线平滑为贝塞尔曲线
> - 曲率连续

## Before
平面上已知n+1个数据点Pi(xi, yi), i = 0, 1, 2, ... , n 。在相邻两点Pi和Pi+1之间使用三次Bezier曲线连接。

> **解析:**
> - 四个控制点确定三次贝塞尔曲线，除起点终点外还有两个控制点，如何确定?
> - 第一条和最后一条线段的贝塞尔曲线
> - 使曲率连续

## Solve
曲率连续及控制点求解：
![\[参考文献\]](http://www.zheng-hang.com/zb_users/upload/2015/04/201504121428776867406226.png)
<br>
第一条和最后一条线段：
![enter image description here](http://www.zheng-hang.com/zb_users/upload/2015/04/201504121428777915191225.jpg)
使用第一种方法：
$ A_0:(x_0 + a(x_1 - x_0), y_0 + b(y_1 - y_0)) $
$ B_{n-1}:(x_n - a(x_n - x_{n-1}), y_n - b(y_n - y_{n-1})$
其中a，b为任意正整数


## 绘制曲线：
```
typedef struct point{
    double x, y;
} Geometry_Point;
//插值
void lerp(Geometry_Point &dest, Geometry_Point a, Geometry_Point b, double t) {
    dest.x = a.x + (b.x - a.x) * t;
    dest.y = a.y + (b.y - a.y) * t;
}
//根据t得出像素坐标dest,t范围为[0,1]
void bezier(Geometry_Point &dest, Geometry_Point a, Geometry_Point b,
            Geometry_Point c, Geometry_Point d,  double t) {
    Geometry_Point ab, bc, cd, abbc, bccd;
    lerp(ab, a, b, t); //point between a and b
    lerp(bc, b, c, t);
    lerp(cd, c, d, t);
    lerp(abbc, ab, bc, t);
    lerp(bccd, bc, cd, t);
    lerp(dest, abbc, bccd, t); //point on bezier-curve
}
```
## 关于曲率连续：
上述的方法使得曲线的切线斜率连续。在多数的情况下，我们常常需使得曲率也连续，即二阶导相等。
此时不仅要求$B_{i-1}$和$A_i$都在$P_i$所做的切线上，还需满足如下等式：
$$ (\frac{\overline{B_{i-1}P_i}}{\overline{P_iA_i}})^2 = \frac{\overline{A_{i-1}B_{i-1}}*\sin\angle{A_{i-1}B_{i-1}P_i}}{\overline{A_iB_i} * \sin\angle{P_iA_iB_i}} , i=1, 2, 3, ..., n-1$$
此时需要使用迭代的方法，反复迭代最终达到收敛，从而得到控制点。

<br>
感谢阅读这份文档, Thanks。
这是一个贝塞尔绘制示例脚本。请点击 [曲线绘制](http://myst729.github.io/bezier-curve/ ) 
<br>