# CORS Vulnerability Detector

一个用于检测CORS（跨域资源共享）配置漏洞的Burp Suite扩展插件。

## 功能特点

- 自动检测CORS配置漏洞
- 支持两种漏洞检测模式：
  - Access-Control-Allow-Origin: * 配置检测（低危）
  - Origin头值反射检测（为了方便区分显示高危）
- 内置请求限流机制，避免对目标系统造成过大压力
- 自动修改请求Origin头，无需手动干预
- 漏洞检测结果自动添加到Burp Scanner面板

## 安装方法

1. 下载最新版本的jar文件
2. 打开Burp Suite
3. 进入`Extender` -> `Extensions`标签页
4. 点击`Add`按钮
5. 在`Extension File`选项中选择下载的jar文件
6. 点击`Next`完成安装

## 使用说明

1. 安装插件后，插件会自动在后台工作
2. 所有HTTP请求都会被自动添加或修改Origin头为`https://baidu.com`
3. 当检测到CORS配置漏洞时，会自动在Burp Scanner的Issues面板中显示
4. 漏洞等级分类：
   - （为了方便区分显示高危）高危：服务器响应头反射了Origin头的值
   - 低危：服务器响应头包含`Access-Control-Allow-Origin: *`

## 技术实现

- 基于Burp Suite扩展API开发
- 实现了IBurpExtender和IHttpListener接口
- 使用Java语言开发，确保跨平台兼容性
- 内置5秒请求间隔的限流机制

## 注意事项

- 插件会自动修改所有请求的Origin头，如果不需要检测某些请求，请临时禁用插件
- 限流机制固定为5秒间隔，如需调整请修改源码中的REQUEST_INTERVAL值

## 关于作者

- 作者：零组攻防实验室@小妖
- 公众号：零组攻防实验室/x1aoYa0
- GitHub：https://github.com/Di-duo/CorsAttack

## 许可证

本项目采用MIT许可证，详细信息请参见LICENSE文件。