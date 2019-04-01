# pytest安装及使用
## 安装
```
pip install -U pytest
```
## 如何编写pytest测试样例
- 测试文件以test_开头(或者以_test结尾），需要在py文件内import pytest
- 测试类以Test开头，并且不能带用init方法
- 测试函数以test_开头
- 断言使用基本的assert
## 运行模式
运行pytest时会找**当前目录及其子目录下**所有符合pytest测试样例命名规则的文件、方法、类
1. 运行后生成html测试报告
安装pytest-html
```
pip install -U pytest-html
```
运行
```
pytest --html=report.html
```
2. 运行指定样例
样例代码 test_py.py
```
import pytest
class TestClassOne:
    def test_one(self):
        assert 1==1
    def test_two(self):
        assert 'd' in 'sd'
class TestClassTwo:
    def test_three(self):
        assert 1+1==2
```
模式1：运行test_py.py的所有测试样例
```
pytest test_py.py
```
模式2：运行TestClassOne类下的两个test函数
```
pytest test_py.py::TestClassOne
```
模式3：运行TestClassOne下的test_one
```
pytest test_py.py::TestClassOne::test_one
```
3. 多进程运行cases
安装pytest-xdist：
```
pip install -U pytest-xdist
```
运行, NUM为并发的进程数：
```
pytest test_py.py -n NUM
```
4. 重试运行cases
case失败，可以自动重试。安装pytest-rerunfailures
```
pip install -U pytest-rerunfailures
```
运行, NUM为重试次数：
```
pytest test_py.py --reruns NUM
```
5. 显示调试脚本print内容， 命令末尾加-s
运行：
pytest test_py.py -s
6. 显示测试覆盖率
安装pytest-cov：
```
pip install -U pytest-cov
```
(可选)配置覆盖率测试忽略路径，在测试路径下新建.coveragerc，以下为样例
```
[run]
omit = 
    venv/*
    main.py
```
对测试目录下的所有测试样例进行覆盖率测试：
```
pytest --cov=./      // 无配置文件
pytest --cov=./ --cov-config ./.coveragerc     //加载配置文件.coveragerc
```
## pytest参数化管理
[参考链接](https://www.jianshu.com/p/89c568a21b57)





