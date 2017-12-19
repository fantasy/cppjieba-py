# cppjieba-py

cppjieba-py 是 [cppjieba](https://github.com/yanyiwu/cppjieba)的 Python 封装。

## 性能

测试[方案](https://yanyiwu.com/work/2015/06/14/jieba-series-performance-test.html)：先按行读取文本围城到一个数组里，然后循环对围城每行文字作为一个句子进行分词。因为只对围城这本书分词一遍太快了，容易误差。 所以循环对围城这本书分词50次。基本上每次分词耗时都很稳定。 分词算法都是采用【精确模式】。

| 方案        | 速度             |
| ------------- |:-------------:|
| cppjieba-py      | 8s  |
| jieba      | 77s    |


## 使用

下面是一个使用 cppjieba-py 进行分词的例子

```python
# -*- coding: utf-8 -*-
from cppjieba_py import jieba 

jieba_instance = jieba("cppjieba/dict/user.dict.utf8")
seg_list = jieba_instance.cut("我来到北京清华大学")
print("Full Mode: " + "/ ".join(seg_list))  # 全模式


seg_list = jieba_instance.cut("他来到了网易杭研大厦")  # 默认是精确模式
print(", ".join(seg_list))

seg_list = jieba_instance.cut_for_search(
    "小明硕士毕业于中国科学院计算所，后在日本京都大学深造")  # 搜索引擎模式
print(", ".join(seg_list))
    
```

## 安装

* 从源代码安装

	```
	$ git clone --recursive https://github.com/fantasy/cppjieba-py
	$ python setup.py build 
	$ python setup.py install 
	```