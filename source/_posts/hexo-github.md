title: 搭建hexo + github pages
---

## 0X1 安装包

### **Git**

### **[Node.js](http://nodejs.org)**
```bash
wget https://nodejs.org/dist/v0.12.6/x64/node-v0.12.6-x64.msi
// install
```
### **[Hexo](https://hexo.io) **

```bash
npm install -g hexo-cli
```

## 0X2 初始化

### 创建hexo文件夹

```bash
hexo init <folder>
```

### 安装Hexo插件

```bash
npm install hexo --save
npm install hexo-generator-index --save
npm install hexo-generator-archive --save
npm install hexo-generator-category --save
npm install hexo-generator-tag --save
npm install hexo-server --save
npm install hexo-deployer-git --save
npm install hexo-deployer-heroku --save
npm install hexo-deployer-rsync --save
npm install hexo-deployer-openshift --save
npm install hexo-renderer-marked@0.2 --save
npm install hexo-renderer-stylus@0.2 --save
npm install hexo-generator-feed@1 --save
npm install hexo-generator-sitemap@1 --save
```

### 安装主题

```bash
git clone https://github.com/litten/hexo-theme-yilia.git themes/yilia
npm install hexo-renderer-ejs --save
```
使用主题需要修改_config.yml中的theme参数，示例：
```yml
theme: carbon
```


## 0X3 使用和调试

### 启动本地服务器

```bash
hexo server
```

## 0X4 GitHub配置SSH keys

### 检查本机ssh keys

```bash
cd ~/.ssh
ls
// 查看
```

### 生成新的ssh keys

```bash
ssh-keygen -t rsa -C 'hyqiu.syen@gmail.com'
// 回车
// 输入加密串
// 生成成功
```

### 添加ssh keys至GitHub中

+ cat ~/.ssh/id_rsa.pub，复制输出内容
+ 打开连接[GitHub ssh设置](https://github.com/settings/ssh)，添加SSH key
+ 复制内容至Key中即可

### 测试

```bash
ssh -T git@github.com
// yes
// 查看是否成功
```

## 0X5 Hexo自动部署

### 部署至Github

修改_config.yml文件
```yml
deploy:
  type: git
  repository: git@github.com:jacksyen/jacksyen.github.io.git
  branch: master
```

### 部署命令行文件

```bash
hexo clean
hexo deploy --generate
```

## 0X6 常见问题

+ [livereload](http://livereload.com/)自动监控文件修改，无需F5，这里不建议使用，在安装过程中，遇到必须安装.net framework sdk 2.0，才能使用，但是安装后还是不行，sdk 2.0中并不包含VCBuild.exe文件，估计还得装VC等等，测试平台：`win7 x64`,`nodejs-2.11.2`




 
