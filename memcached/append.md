#### append 命令

memcached append 命令用于向已存在 key(键) 的 value(数据值) 后面追加数据

```memcached
append key flags exptime bytes [noreply]
value
```

#### 参数说明
- key：键值 key-value 结构中的 key，用于查找缓存值
- flags：可以包括键值对的整型参数，客户机使用它存储关于键值对的额外信息 
- exptime：在缓存中保存键值对的时间长度（以秒为单位，0 表示永远）
- bytes：在缓存中存储的字节数
- noreply（可选）： 该参数告知服务器不需要返回数据
- value：存储的值（始终位于第二行）（可直接理解为key-value结构中的value）

- 在 Memcached 中存储一个键 runoob，其值为 memcached
- 使用 get 命令检索该值
- 使用 append 命令在键为 runoob 的值后面追加 "redis"
- 使用 get 命令检索该值

```memcached
set runoob 0 900 9
memcached
STORED
get runoob
VALUE runoob 0 9
memcached
END
append runoob 0 900 5
redis
STORED
get runoob
VALUE runoob 0 14
memcachedredis
END
```

#### 输出信息
- STORED：保存成功后输出
- NOT_STORED：该键在 memcached 上不存在
- CLIENT_ERROR：执行错误