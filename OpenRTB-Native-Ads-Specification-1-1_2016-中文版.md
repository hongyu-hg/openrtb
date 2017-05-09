# OpenRTB Native Ads Specification 中文版

身为一个程序狗，英文不好， 又找不到中文资料， 自己翻译了一个，不严谨，带到坑里不负责：）

##简介
为了开发 Native Ad媒体和平台间的自动化购的开放协议， Native Ad 小组委员会于2014年成组建。

ABOUT THE IAB’S TECHNOLOGY LAB
##关于IAB技术实验室
就是这个实验室开发了OpenRTB协议， OpenRTB2.3 Native的Object就几个字段，鬼知道还有这么长的一个文档，写代码的时候才细读，被坑得不要不要的。

###实验室的更多细节去官网查看
http://www.iab.com/organizations/iab-tech-lab/

Native Ads Specification原始文档可以在www.iab.com(三字母的好域名呀）找到。 

IAB 联系方式:

  Melissa Gallo

  Director of Product, Programmatic Automation and Data IAB Technology Laboratory

  melissa@iab.com
##开源协议
Creative Commons Attribution 3.0 License


###目录（感觉github的Markdown生成目录不是很好用， 就先不加链接了）
修改日志

1.简介

  1.1 综述

  1.2 项目历史

  1.3 可利用资源

  1.4 历史版本

2. Native Ads 基础

  2.1 IAB 六种类型的广告单元

  2.2 Deep Dive on In-Feed Ad Units(这里有另外一个文档，好像是跟Feed相关，后面更新）

  2.3 数据格式

  2.4 版本标识

3. bid request 细节

  3.1 Native Object 层级关系 
  
4. Native Ad 标记细节

  4.1 Native Markup Request 对象
  
  4.2 Assert 对象
  
  4.3 Title 对象
  
  4.4 Img 对象
  
  4.5 Video 对象
  
  4.6 Data 对象
  
5. Native Ad Bid 响应标记

  5.1 Native Ad 创意Json。 
  
  5.2 Native 对象
  
  5.3 Asset 对象
  
  5.4 Title 对象
  
  5.5 Image 对象
  
6. Bid Request/response 示例

    6.1 苹果墙示例
        
        6.1.1 Bid Request
        
        6.1.2 Bid Response
    
    6.2 聊天列表示例
    
        6.2.1 Bid Request
        
        6.2.2 Bid Response
    
    6.3 信息流和视频元素示例
    
        6.3.1 Bid Request
        
        6.3.2 Bid Response

    6.4 Google 文本广告
    
        6.3.1 Bid Request
        
        6.3.2 Bid Response
        
7. 参考列表

    7.1 Native Layout IDs
    
    7.2 Native Ad Unit IDs
    
    7.3 Data Asset Types
    
    7.4 Image Asset Types
    
8. 应用笔记

    8.1 Multi placement Bid Requests


# 3 Bid 请求
RTB 对话始于exchange或者其他兼容的服务发起一个bid请求到一个出价方。bid请求包含一个bid request对象。 




## Native Ad 返回数据

Native 的广告返回格式和内容和标准的openrtb 一致， 区别在于ad creative 是怎样返回的。 native creative 应该返回一个编码过的json字符串在Bid Object的adm字段。注意： 有些实现选择直接用Object而不是用json字符串。

### 5.1 Native 返回数据


