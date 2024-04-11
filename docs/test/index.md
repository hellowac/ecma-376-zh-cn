# 测试

**测试目标**
    : 提升项目的稳定性/容错性/抗压性

**测试时间**
    : 功能完成时、上线之前、解决bug之后

**测试环境**
    : 开发测试服、开发本地

**测试人员**
    : 功能开发人、测试人员

**测试目的**
    : 发现系统bug、系统瓶颈、优化方向

**测试方法**
    : web页面操作、写python代码
  
## 测试工具

**web浏览器**
    : 点击功能、测试业务是否流程通常

**python代码**
    : 由开发人员，编写测试逻辑的代码。

    1. 测试前置条件说明；
    2. 测试业务逻辑说明;
    3. 测试代码实现；
    4. 测试结果说明；

## 测试流程示例

http接口测试相对简单， 更重要的是，各个接口联合起来的业务是否能顺利流畅的执行完成。

pytest使用参考: <https://learning-pytest.readthedocs.io/zh/latest/doc/intro/getting-started.html>

## mock
此模块主要用于模拟，无法再测试时调用的函数，但是测试过程中需要的这个函数，此时使用mock模拟，通常用于外部的网络请求
项目地址： https://mock.readthedocs.io/en/latest/

示例:

1. 编写测试逻辑

    ```python
    # <project>/tests/function.py
    import requests
    
    # 登陆测试
    def test_login():
        url = 'http://localhost:8001/login'
        data = dict(username='test', password="123456")
        response = requests.post(url, data=data)
        assert response.status_code == 200
    
    ```

2. 执行测试文件

    ```shell
    cd <project>   # 到项目目录
    pytest tests/login.py  # 执行测试文件
    ```
