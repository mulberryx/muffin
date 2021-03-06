mongodb不支持事务，所以，在你的项目中应用时，要注意这点。无论什么设计，都不要要求mongodb保证数据的完整性
但是mongodb提供了许多原子操作，比如文档的保存，修改，删除等，都是原子操作
所谓原子操作就是要么这个文档保存到Mongodb，要么没有保存到Mongodb，不会出现查询到的文档没有保存完整的情况

#### eg
db.books.findAndModify({
  query: {
    _id: 123456789,
    available: { $gt: 0 }
  },
  update: {
    $inc: { available: -1 },
    $push: { checkout: { by: "abc", date: new Date() } }
  },
})

#### =============================================================================================
#### 原子操作常用命令
#### 用来指定一个键并更新键值，若键不存在并创建
$set
{ $set : { field : value } }

#### 用来删除一个键
$unset
{ $unset : { field : 1} }

#### $inc可以对文档的某个值为数字型（只能为满足要求的数字）的键进行增减的操作
$inc
{ $inc : { field : value } }

#### 
$push
{ $push : { field : value } }

#### 可以追加多个值到一个数组字段内
$pushAll
{ $pushAll : { field : value_array } }

#### 从数组field内删除一个等于value值
$pull
{ $pull : { field : _value } }

#### 增加一个值到数组内，而且只有当这个值不在数组内才增加
$addToSet

#### 删除数组的第一个或最后一个元素
$pop
{ $pop : { field : 1 } } 

#### 修改字段名称
$rename
{$rename : { old_field_name : new_field_name }}

#### 位操作，integer类型
$bit
{$bit : { field : {and : 5}}}
