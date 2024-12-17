# 快速启动

## 1.  二级标题

正文

## 2. 二级标题

使Shell示例:

```shell
docker run --name postgres \
  -e POSTGRES_PASSWORD=mysecretpassword \
  -p 5432:5432 \
  -d postgres
```

SQL示例

```sql
CREATE DATABASE brconnector_db;
```

## 3. 测试

现在,您有了第一个管理员用户,其API密钥为"br_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"。

使用`curl`命令并带上API密钥来测试服务器:

```shell
curl "http://localhost:8866/admin/api-key/list" \
  -H "Authorization: Bearer br_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" 
```

您会得到如下的输出:

```json
{"success":true,"data":{"items":[],"total":"0","limit":20,"offset":0}}
```

!!! note
    您可以使用这个 <https://github.com/aws-samples/sample-client-for-amazon-bedrock> 客户端来测试，[请查看如何配置](../user-manual/sample-client-for-bedrock.md)。
    Since 0.0.8, this client has been built into the docker image. The access address is: `http(s)://your-endpoint/brclient/`