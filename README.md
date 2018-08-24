1. mongod.conf文件为mongodb的启动文件
   => bin目录中的 mongod文件是用来指定一个启动文件来启动 mongodb 的，mongo 文件时用来连接 mongodb 的


2. 启动 mongodb 命令:
   => ./bin/mongod -f conf/mongod.conf (-f: 指定一个文件)
   => 启动成功后，data和log目录分别会多出一些文件，
   => 并且 mongodb 将处于等待连接的状态

3. 连接 mongodb 命令:
   => ./bin/mongo 127.0.0.1:12345 (端口为之前在mongod.conf文件中定义的)
   => 连接成功后，终端下面会有一个向右的箭头表示+

4. 关闭 mongodb 命令:
   => db.shutdownServer() || 直接杀掉进程也可以（kill）

5. 数据库操作
   => 切换/创建数据库: use + 数据库名称
   => 删除当前数据库: db.dropDatabase()
   => 当前数据库中创建表(集合): db.user.insert({"name": "tang"}), 该命令创建一个名为user的表，并向其中插入了一条数据
   => 删除当前数据库中的表: db. + 表的名称 + .drop()

6. 表(集合)的操作
   => .insert({x: 1}) 单个插入数据操作
   => for (var i=1;i<100;i++) db.num.insert({x: i}) 循环插入数据操作 
   => .find() => 查找表中所有的数据
   => .find({x: 1}) 查找表中具体的某一种数据
   => .count() 查看数据数目
   => .skip(num) 过滤掉开始的数据
   => .limit(num) 限制返回的数据条数
   => .sort({x: num}) 当num为正时，正序排序，为负时，逆序排序
   => .update(old, new) 更新表中的某一条数据(只能更新一条)
   => .update({z: 3}, {$set: {y: 3}}) 更新表中的某一条数据中的一部分 {x: 1,y: 2, z: 3} => {x: 1,y: 3,z: 3}
   => .update(old, new, true) 更新一条原本不存在的数据的，自动创建并更新 (第三个参数表示更新的数据不存在时，自动创建)
   => .update({x: 1}, {$set: {x: 2}}, false, true) 更新所有符合条件的数据 (把所有包含x: 1的数据中的x改为2)
   => .remove({x: 1}) 删除所有包含有x:1的数据
   => .getIndexes() 查看索引









. mongodb 中的结构:
   => mongodb  (mongodb 数据库这个软件)
   => 数据库 (show dbs 即可查看所有的数据库)
   => 表(集合) (show collections 即可查看所有的表)