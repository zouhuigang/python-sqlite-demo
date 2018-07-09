### 生成requirements.txt

    pip freeze > requirements.txt (如果报错，将pip降级成9.x)
    python -m pip install --user --upgrade pip==9.0.3

### 测试

添加用户:

    curl -i -X POST -H "Content-Type: application/json" -d '{"username":"zhg","password":"123456"}' http://127.0.0.1:5000/api/users

用户登录:
    curl -u zhg:123456 -i -X GET http://127.0.0.1:5000/api/resource

用一个错误的用户名和密码登录:

    curl -u zhg:gg -i -X GET http://127.0.0.1:5000/api/resource

生成token:

    curl -u zhg:123456 -i -X GET http://127.0.0.1:5000/api/token

用生成的token，认证

    curl -u eyJhbGciOiJIUzI1NiIsImlhdCI6MTUzMTEyMjMwOCwiZXhwIjoxNTMxMTIyOTA4fQ.eyJpZCI6Mn0.P6z-GbaFc_7e-6Fo2FJkq7u9ItScab1im3BHRF6P7ls:x -i -X GET http://127.0.0.1:5000/api/resource



### 语法

q:
    TypeError: object of type 'filter' has no len()

a2:

    python2中，filter函数会返回一个list,python3中，会返回一个迭代器。
    可以使用l = [x for x in n if x > 3]

q:

    ubuntu ModuleNotFoundError: No module named '_sqlite3'

a:

   sudo apt-get install libsqlite3-dev 
   yum install sqlite3-devel -y
   然后重新make重新安装python吧
   然后查看
    /usr/bin/python3.7/lib/python3.7/lib-dynload
    发现：
    _sqlite3.cpython-37m-x86_64-linux-gnu.so　即可！

q:

    E: Sub-process /usr/bin/dpkg returned an error code (1)

a:

    cd /var/lib/dpkg

    sudo mv info info.bak

    sudo mkdir info
    sudo apt-get install libsqlite-dev