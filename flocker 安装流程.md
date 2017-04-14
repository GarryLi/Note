mkdir /data/software/
cd /data/software
git clone https://github.com/ClusterHQ/flocker
yum -y install epel-release(CentOS7中添加fedora的yum源)
yum install python-pip

yum install python-enchant gcc python-devel openssl-devel
pip install six
pip install -r requirements/all.txt

python setup.py install














注：
1、如果python版本为 2.7，且执行 pip install -r requirements/all.txt 时报 “no module named configparser” 的错误，则修改以下文件
/usr/lib/python2.7/site-packages/flake8/main/mercurial.py, /usr/lib/python2.7/site-packages/flake8/options/config.py
将 import configparser 注释掉，改为 
try:
    import configparser
except ImportError:
    import ConfigParser as configparser
重新执行 pip install -r requirements/all.txt
