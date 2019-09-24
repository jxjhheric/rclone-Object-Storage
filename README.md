# 用rclone 挂载Object Storage当本地盘
  申请Oracle Cloud永久免费服务中其实还有一个20GB的永久免费对象存储的功能！
开通地址
右侧菜单 – 对象存储 – 对象存储
![Alt text](https://img13.360buyimg.com/img/jfs/t1/43255/27/15443/44865/5d81fb68E7f588772/db3e4b8cfa6e6f19.png)

### Oracle Object Storage免费规则
>您可以免费在您的主区域中使用 20 GiB 的存储。您已经使用大约 0 字节。如果您在免费试用结束时使用的存储超过 20 GiB 且未升级，您的数据将被删除。您正在参与免费试用，可以存储无限数据。试用结束时，您将转换为“始终免费”账户。“始终免费”账户只允许在您的主区域中使用 20 GiB 的存储（对象存储和归档存储总和）。如果您在转换账户时使用的存储超过 20 GiB，您的数据将被删除。请在转换为“始终免费”之前，将使用量减少到 20 GiB 以内。

### 申请access_key 和secret_access_key
申请完Oracle Object Storage后，点击账号头像---账号邮箱，进入账号页面
![2019-09-24_124237.png](https://i.loli.net/2019/09/24/gTpfyEBramdvRul.png)

选择左边的客户密钥，生成access_key 和secret_access_key
![2019-09-24_124348.png](https://i.loli.net/2019/09/24/Rb8ZplcBqT47zVk.png)
**一定要记下access_key 和secret_access_key，**一会rclone配置的时候要用到
![2019-09-24_124444.png](https://i.loli.net/2019/09/24/aq2O53Zv4elmIjK.png)
![2019-09-24_124516.png](https://i.loli.net/2019/09/24/92HOi7lBVCwxZsf.png)
![2019-09-24_124640.png](https://i.loli.net/2019/09/24/jJVdTsxvr7oeOAL.png)

###  配置rclone
rclone ： https://rclone.org/downloads/  
winfsp ： http://www.secfs.net/winfsp/download/  
其中rclone的windows版需要解压，并添加解压目录到系统路径中。而依赖库winfsp下载完后一路Next直接安装就可以了。  
安装完后在cmd中输入命令行 
```
rclone.exe config 
```
选择Amazon S3
```
[oracle]
type = s3
provider = Other
env_auth = false
access_key_id = xxxxxxxxxxxxxxxxxxx
secret_access_key = xxxxxxxxxxxxxxxxxxxx
region =  
endpoint = https://[object_storage_namespace].compat.objectstorage.ap-tokyo-1.oraclecloud.com  具体见https://docs.cloud.oracle.com/iaas/Content/API/Concepts/apiref.htm说明
location_constraint =  
acl = private
```

