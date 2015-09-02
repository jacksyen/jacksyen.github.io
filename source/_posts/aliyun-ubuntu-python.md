title: 阿里云ubuntu14.04 python Image模块问题
date: 2015-09-02
---

## 0X1 说明
在使用阿里云的时候（ubuntu14.04 64位，python v2.7.6），Image模块提示找不到，使用pip安装也不行的问题

## 0X2 解决办法
```bash
// 删除原有的PIL包
rm -rf /usr/local/lib/python2.7/dist-packages/PIL
apt-get install libjpeg-dev libfreetype6-dev zlib1g-dev libpng12-dev
wget http://effbot.org/downloads/Imaging-1.1.7.tar.gz
tar xzvf Imaging-1.1.7.tar.gz
cd Imaging-1.1.7
// 修改安装环境参数
vi setup.py
    TCL_ROOT = '/usr/lib/x86_64-linux-gnu' 
	JPEG_ROOT = '/usr/lib/x86_64-linux-gnu' 
	ZLIB_ROOT = '/usr/lib/x86_64-linux-gnu' 
	TIFF_ROOT = '/usr/lib/x86_64-linux-gnu' 
	FREETYPE_ROOT = '/usr/lib/x86_64-linux-gnu' 
	LCMS_ROOT = '/usr/lib/x86_64-linux-gnu
// 创建freetype软连接
sudo ln -s /usr/include/freetype2 /usr/local/include/freetype
python2.7 setup.py install
```
