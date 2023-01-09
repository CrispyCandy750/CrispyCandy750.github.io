---
title: 使用hexo搭建博客
date: 2023-01-08 16:28:15
tags: 
- 笔记
- 博客
top: false
---

[感谢CodeSheep的技术分享](https://www.bilibili.com/video/BV1Yb411a7ty/?spm_id_from=333.1007.top_right_bar_window_history.content.click&vd_source=c749240dfe489e71ec336f64813c1bea)

## 1. 下载

### (1) 环境准备

[官网在这](https://nodejs.org/en/)

![image-20230107154512525](https://crispy-candy-image.oss-cn-beijing.aliyuncs.com/img/image-20230107154512525.png)

下载长期支持版的

然后一直安装即可

安装完有两个组件

![image-20230107154719439](https://crispy-candy-image.oss-cn-beijing.aliyuncs.com/img/image-20230107154719439.png)

然后在命令行操作

```shell
node -v #查看Node的版本
# v18.13.9  直接输出了，不用配置
npm -v  #包管理器
# 8.19.3  包管理器的版本
```

Hexo是需要Node.js生成的，因此需要先下载这个

### (2) 安装cnpm

我们需要npm包管理器来安装，但是国内的镜像太慢，因此要利用npm来安装cnpm，就是淘宝的源(npm是Node.js自带的包管理器，但是我们需要的是淘宝的源)

![image-20230107155236840](https://crispy-candy-image.oss-cn-beijing.aliyuncs.com/img/image-20230107155236840.png)

输入第一行指令，自动安装了

```shell
cnpm #输出信息就可以知道安装成功了
cnpm -v
```

### (3) 安装hexo框架

用cnpm来安装hexo框架

```shell
cnpm install -g hexo-cli
```

> -g是全局安装的意思

然后自动安装好hexo框架了

```
hexo -v # 验证安装
```

## 2. Hexo搭建博客

### (1) 初始化博客

先建立一个目录来存储博客文件，有什么问题将目录干掉重来即可

然后进入这个博客

```shell
hexo init # 初始化这个博客
```

等待一段时间安装好

![image-20230107160209013](https://crispy-candy-image.oss-cn-beijing.aliyuncs.com/img/image-20230107160209013.png)

![image-20230107160224116](https://crispy-candy-image.oss-cn-beijing.aliyuncs.com/img/image-20230107160224116.png)

这是博客基础的框架内容

### (2) 启动博客

然后启动博客

```shell
hexo s
```

![image-20230107160402826](https://crispy-candy-image.oss-cn-beijing.aliyuncs.com/img/image-20230107160402826.png)

在4000这个端口开了一个博客

localhost:4000

![image-20230107160424866](https://crispy-candy-image.oss-cn-beijing.aliyuncs.com/img/image-20230107160424866.png)

里面有hexo的内容

### (3) 新建一篇文章

```shell
hexo n "我的第一篇文章"
```

n是new的意思

![image-20230107160733566](https://crispy-candy-image.oss-cn-beijing.aliyuncs.com/img/image-20230107160733566.png)

自动创建了md的文章

可以看到文章都是在_posts这个目录中

然后可以用编辑器编辑了

```markdown
---
title: 我的第一篇文章
date: 2023-01-07 16:07:25
tags:
---
```

这是自动生成的内容，不要改了，在下面写内容

### (4) 生成一篇文章

回到blog目录

```shell
hexo clean
hexo g
```

> g是generate的意思，这个是将md文件生成页面文件

然后就生成这篇文章了

![image-20230107161312731](https://crispy-candy-image.oss-cn-beijing.aliyuncs.com/img/image-20230107161312731.png)

生成了2023/01/07这个了

### (5) 重新启动查看

```
hexo s # 重新打开hexo
```

![image-20230107161839129](https://crispy-candy-image.oss-cn-beijing.aliyuncs.com/img/image-20230107161839129.png)

## 3. 部署博客

博客肯定是要部署到远端的，没有服务器的话，可以免费部署到GitHub上

### (1) 新建仓库

![image-20230107162244991](https://crispy-candy-image.oss-cn-beijing.aliyuncs.com/img/image-20230107162244991.png)

名字必须是 昵称.github.io

![image-20230107162329388](https://crispy-candy-image.oss-cn-beijing.aliyuncs.com/img/image-20230107162329388.png)

### (2) 安装git插件

要部署到GitHub需要安装插件

到了blog目录下

```shell
cnpm install --save hexo-deployer-git
```

![image-20230107162516659](https://crispy-candy-image.oss-cn-beijing.aliyuncs.com/img/image-20230107162516659.png)

### (3) 配置

就是设置_config.yml文件

```yaml
# Deployment
## Docs: https://hexo.io/docs/one-command-deployment
deploy:
  type: 'git'
  repo: 'https://github.com/CrispyCandy750/CrispyCandy750.github.io.git' # 生成文件的http地址复制过来，使用SSh地址好像部署的时候不用密码
  branch: 'master'
```

### (4) 部署

```shell
hexo d
```

> d是deploy的意思

然后就会部署了

之前使用的SSH地址就不需要输入密码

然后刷新GitHub的仓库

![image-20230107163233006](https://crispy-candy-image.oss-cn-beijing.aliyuncs.com/img/image-20230107163233006.png)

### (5) 访问博客

仓库名就是博客的地址 `CrispyCandy750.github.io`

## 4. 自定义主题

### (1) 下载主题

这里演示如何自定义主题

https://github.com/litten/hexo-theme-yilia

在这个网站中设置的，下载主题

```shell
git clone https://github.com/litten/hexo-theme-yilia themes/yilia
```

将这个仓库下载到blog/themes/yilia下面



### (2) 配置主题

还是修改_conig.yml文件

```yaml
# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: yilia
```

将原来的主题换成yilia即可

![image-20230107164310243](https://crispy-candy-image.oss-cn-beijing.aliyuncs.com/img/image-20230107164310243.png)

![image-20230107164742266](https://crispy-candy-image.oss-cn-beijing.aliyuncs.com/img/image-20230107164742266-16730812627801.png)

发现博客主题已经变了

然后重新部署

```shell
hexo d
```

改了主题不是立马生效，多刷新一下

