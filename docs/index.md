# LLM+ADB快速构建企业专属Chatbot

## 背景介绍
ChatGPT的火爆带动AIGC行业近期非常火热，客户对于智能客服，构建企业知识库用于智能问答，写作助手等相关需求非常旺盛；随着ChatGPT 推出Retrieval plugin的方案推出，向量数据库（企业知识库）+ 大语言模型 可以快速帮助企业构建专属的chatbot； 本服务是对文章《云原生数据仓库AnalyticDB(ADB)+LLM：构建AIGC时代下企业专属Chatbot》的一个开源实现部署。模型基于ChatGLM-6B，是由清华大学团队开发的是一个开源的、支持中英双语的对话语言模型，基于 General Language Model (GLM) 架构，具有 62 亿参数。本文介绍如何通过计算巢快速完成从0到1部署，在30分钟内可以快速构建企业专属聊天机器人（已经支持ChatGLM2-6B模型）
<img src="1.png" width="1000" align="bottom"/>


## 服务介绍
**一站式企业专属Chatbot**：通过对Langchain+ChatGLM2-6B（开源大模型）+AnalyticDB for PostgreSQL的部署，一键搭建企业专属知识库+Chatbot应用；（依赖资源： ECS + AnalyticDB for PostgreSQL）**代运维服务**：如果部署遇到问题，可通过代运维服务授权运维人员使用大模型服务（免费）[<img src="2.png" width="400" align="bottom"/>](https://computenest.console.aliyun.com/user/cn-hangzhou/serviceInstanceCreate?ServiceId=service-ab3bac294c3140649e56)[<img src="3.png" width="400" align="bottom"/>](https://computenest.console.aliyun.com/user/cn-hangzhou/serviceInstanceCreate?ServiceId=service-ddfecdd9b626465f85b6)         
[一站式企业专属大模型](https://computenest.console.aliyun.com/user/cn-hangzhou/serviceInstanceCreate?ServiceId=service-ddfecdd9b626465f85b6) ｜  [代运维服务](https://computenest.console.aliyun.com/user/cn-hangzhou/serviceInstanceCreate?spm=a2c6h.13046898.0.0.4ea76ffa7HRcSM&ServiceId=service-ab3bac294c3140649e56)

## 部署一站式企业专属Chatbot   
### 创建流程
1. 单击[部署链接](https://computenest.console.aliyun.com/user/cn-hangzhou/serviceInstanceCreate?ServiceId=service-ddfecdd9b626465f85b6 )
2. 进入开通配置界面

    <img src="4.png" width="1000" align="bottom"/>
    
   依次填写完服务实例名，选择地域，配置GPU服务的规格，登录密码及访问白名单，ADBPG的实例规格和存储及数据库密码，点击**确认订单**

3. 确认订单页会显示基础配置和账单，节点创建则进入创建环节

    <img src="5.png" width="1000" align="bottom"/>
   
4. 点击去列表查看，会看到创建中的实例，正常情况约20min完成创建

    <img src="6.png" width="1000" align="bottom"/>
    
   <img src="7.png" width="1000" align="bottom"/>

### 管理资源（可选）
1. 点击服务实例，进入后可以看到服务详情，等待创建完成，整个流程约20分钟
    
    <img src="8.png" width="1000" align="bottom"/>
   
    创建过程中包括拉起ECS资源用以部署Retrieval服务，预部署开源大语言模型，拉起ADB-PG实例用以构建企业专属知识库，联通vpc网络，设置安全组等资源并对外提供服务；
   
    <img src="9.png" width="1000" align="bottom"/>
   
2. 待部署完成通过Endpoint的地址进行访问
    
    <img src="10.png" width="1000" align="bottom"/>
   
3. 点击资源则可查看关联的安全组，AnalyticDB for PostgreSQL实例，VPC，VSM，GPU服务器信息
    
    <img src="11.png" width="1000" align="bottom"/>
   
4. 如果在创建的时候填写的白名单地址不正确则可点击安全组id查看：
    
    <img src="12.png" width="1000" align="bottom"/>
    
   点击便捷，可修改访问的地址范围，或入群进行支持，配置可参考[文档](https://help.aliyun.com/document_detail/444747.html)进行；
    
    <img src="13.png" width="1000" align="bottom"/>

## 开始使用企业专属ChatBot
1. 进入计算巢服务后，选择【我的服务】-> 【查看实例】查看所有目前保有的实例；
    
    <img src="14.png" width="500" align="bottom"/>
   
2. 点击进入所保有的实例后，可在概览页点击EndPoint所指向的服务登陆Chatbot首页；
    
    <img src="15.png" width="1000" align="bottom"/>
    
   <img src="16.png" width="1000" align="bottom"/>
    
   注：如果发现访问不通，检查是否开通了VPN，关闭VPN

3. 知识库文档选择新建知识库
    
    <img src="17.png" width="900" align="bottom"/>
   
4. 选择知识库库名称DEMO，点击红框位置，上传文件：

    <img src="18.png" width="900" align="bottom"/>
   
5. 点击红色框位置上传并加载：

    <img src="19.png" width="900" align="bottom"/>
   
6. 完成文件上传后，即可开始想知识库进行提问
    
    <img src="20.png" width="1000" align="bottom"/>

## 代运维服务(可选）
代运维服务实在遇到问题的时候授权服务商进行运维操作。

1. 选择需要运维的计算巢服务

    <img src="21.png" width="1000" align="bottom"/>

    <img src="22.png" width="1000" align="bottom"/>

    点击创建后即可对后台运维服务进行授权；

## 常见问题
1. 登录ADBPG实例；

    <img src="23.png" width="1000" align="bottom"/>

    <img src="24.png" width="1000" align="bottom"/>

    <img src="25.png" width="1000" align="bottom"/>

    输入创建服务的的用户名和密码；
    
    <img src="26.png" width="1000" align="bottom"/>

    <img src="27.png" width="1000" align="bottom"/>

    可查询已有知识库和文档向量
