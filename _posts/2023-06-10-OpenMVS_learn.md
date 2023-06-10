---
title: OpenMVS学习记录
author: Elliot Sun
date: 2023-06-10
category: Jekyll
layout: post
---  
# OpenMVS学习记录  
> 最近利用碎片化时间在学习一个三维重建系统OpenMVS。还没全学完，马马虎虎整理下
## 1 OpenMVS介绍与立体视觉基础  
 ...  
## 2 稠密重建  
稠密重建是深度估计（depth estimate）是重建流程中第一个环节，也是三维重建中最关键的
环节。在传统算法中比较经典实用的两个算法是PlanSweeping和PatchMatch两种算法。在平面Sweeping
算法中用的比较多的是SGM算法。OpenMVS框架实现这两种算法，可以通过参数控制测试这两种算法的效
果对比。本章节主要介绍SGM和PatchMatch两种算法的具体实现。  

OpenMVS中实现的SGM是通过对图像做校正，在视差层面下进行计算的（匹配关系由上面的三角测量转换），视差图可以与深度图相互转换。该算法也可不用对图像校正直接计算深度图（匹配关系由对极约束来转换），PatchMatch是直接计算深度图。  
### 2.1 数据准备  
OpenMVS输入是图像和对应的相机内参和外参，在数据准备阶段第一步是剔除无效的、未标定的、被废弃
的图像；第二步是给每个参考图像选择所有有用的邻域帧，这个邻域帧就是我们用来做匹配的帧，合适的选
择策略可以提升重建效果所以这步非常重要；最后就是基于马尔科夫随机场（MRF）优化，为每个参考图像
选择一个全局最佳的邻域视图。  
代码中图像映射关系：
<div align=center><img src=https://s1.ax1x.com/2023/06/10/pCV1gsA.png></div>  

## 3 曲面重建  
..  
## 4 Mesh Refinement  
..  
## 5 纹理贴图  
..  
