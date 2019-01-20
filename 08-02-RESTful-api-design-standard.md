## REST API设计规范

### 1、协议

使用https协议

### 2、路径

由于REST API是面向资源的，所以路径中只能出现名词，不能出现动词，所用名词尽量参考数据库表的设计,例如：
https://xx.com/api/movies
https://xx.com/api/theaters

### 3、http请求方式

1. GET（SELECT）：从服务器取出资源（一项或多项）。

2. POST（CREATE）：在服务器新建一个资源。

3. PUT（UPDATE）：在服务器更新资源（客户端提供改变后的完整资源）。

4. PATCH（UPDATE）：在服务器更新资源（客户端提供改变的属性）。

5. DELETE（DELETE）：从服务器删除资源。

使用例子：

GET /movies：列出所有电影

POST /movies：新建一个电影

PUT /movies/ID：更新某个指定电影的信息


### 4、过滤信息

如果对资源的需求不是全部，那么需要提供过滤的参数，例如：

http://127.0.0.1:8000/api/comments/?movie=%E6%B5%B7%E7%8E%8B *返回对电影海王的评论*

### 5、数据格式

使用json数据格式进行数据传递。

### 7、状态码

200 OK - [GET]：服务器成功返回用户请求的数据，该操作是幂等的（Idempotent）。

201 CREATED - [POST/PUT/PATCH]：用户新建或修改数据成功。

202 Accepted - [*]：表示一个请求已经进入后台排队（异步任务）

204 NO CONTENT - [DELETE]：用户删除数据成功。

400 INVALID REQUEST - [POST/PUT/PATCH]：用户发出的请求有错误，服务器没有进行新建或修改数据的操作，该操作是幂等的。

401 Unauthorized - [*]：表示用户没有权限（令牌、用户名、密码错误）。

403 Forbidden - [*] 表示用户得到授权（与401错误相对），但是访问是被禁止的。

404 NOT FOUND - [*]：用户发出的请求针对的是不存在的记录，服务器没有进行操作，该操作是幂等的。

406 Not Acceptable - [GET]：用户请求的格式不可得（比如用户请求JSON格式，但是只有XML格式）。

410 Gone -[GET]：用户请求的资源被永久删除，且不会再得到的。

422 Unprocesable entity - [POST/PUT/PATCH] 当创建一个对象时，发生一个验证错误。

500 INTERNAL SERVER ERROR - [*]：服务器发生错误，用户将无法判断发出的请求是否成功。

参考资料： [Rest API规范](https://blog.csdn.net/pkueecser/article/details/50193881)