# 压力测试

参考: <https://developer.aliyun.com/article/872437>

!!! info "注意"
    下面的文档生成自代码中的注释/文档注释/模块注释/方法注释/函数注释，文档风格参考[代码文档](../index.md)中的说明. 或参考: [mkdocstrings-python-code-style]

---------

<!--代码路径, 控制代码块文档解析选项: https://mkdocstrings.github.io/python/usage/configuration/docstrings/#docstring_options-->
::: tests.pressure

python性能测试的库地址: https://pypi.org/project/locust/

- 优点简洁轻便，拥有web可视化界面
- 缺点python有gil锁，压力测试效果可能没那么好，需要编写相关的测试代码

apache家族测试性能的软件：https://github.com/apache/jmeter

- 优点压测更优秀
- 缺点配置安装会麻烦一些，需要安装java环境