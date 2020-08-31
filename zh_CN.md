## Impulse Core 使用说明
#### >>>安装注意事项
0. 需要完整的配置环境（干净的系统环境）
1. 需要至少JavaJDK 8及以上版本的JavaJDK程序
2. 需要至少Python 3.8.x及以上版本的PythonSDK程序
3. 需要至少1.14.4版本的Fabric-Loader，具体版本请看Impulse Core对应的版本

#### >>>如何安装
##### Step 1：
- 将JavaJDK 8+安装在计算机中
- 将PythonSDK 3.8+安装在计算机中

##### Step 2：
- 将Impulse自动构建程序下载并上传至计算机中
- 解压缩Impulse自动构建程序压缩宝

##### Step 3：
- 双击Build.bat命令行文件
- 等待构建完成（具体请参照计算机的网络环境，部分较差网络可能会导致Build Failed）

##### Step 4：
- 寻找自动构建程序./BuildJars文件夹
- 在./BuildJars文件夹中通常会找到类似Impulse-v1.0.0-fabric.jar等的Java运行程序

##### Step 5：
- 将构建出来的Java运行程序放入任意位置，并使用以下启动参数启动该Java运行程序
`java -Xmx1024M -Xms1024M -jar Impulse-v1.0.0-fabric.jar`
> 请注意，该命令行脚本仅作为示范使用，实际生产环境中请按照自行环境斟酌

##### Step 6：
- 运行该命令行脚本，等待Impulse第二次下载完毕
- 下载完毕后，服务端会提示请同意eula协议，那么请关闭服务端，并打开eula.txt文件，将布尔值修改为true，保存并关闭即可
- 再次运行命令行，没问题的话系统将提示服务端已开启。那么请根据自行条件修改impulse.yml文件即可

#### >>>impulse.yml设置文件
请根据以下汉化内容自行修改配置文件，切不可直接复制粘贴到文件中！
```
# impulse Core Config 1.0.0
# 这里是impulse服务端的设置文件

# 配置文件版本（请勿修改）
config-version=1

# 是否启用Fabric-API（最好不要动）
enable-fabricapi=true

# 是否启用Fabric-Carpet
enable-carpetmod=true

# 是否启用QuickFunctions
enable-quickfunctions=true

# 是否启用MCD或MCDR插件支持
enable-mcdaemonsupport=true

# 是否启用多世界管理（推荐镜像服使用）
enable-multidims=false

# 是否记录玩家日志
enable-playerlogs=true

# 是否启用服务器日志
enable-systemlogs=true

# 监听客户端模组选项
client-mods-listen:
  # 是否启用该选项:
  enable=false
  # 是否开启白名单模式，如果为否，则为黑名单模式
  whitelist-mode=false
  # 名单列表（是否为黑名单或白名单取决于上一条布尔值的情况）
  lists:
  - xxx
  - xxx
  - xxx
  # 是否开启踢人模式，如果为否，则将不符合要求的玩家名与UUID记录在日志中
  kick-mode=false
  # 是否开启监测客户端是否有注入外挂的情况（需要在客户端配置impulse-security模组）
  dll-import-listen=false
```
