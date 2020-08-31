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
  # 是否启用该选项
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
  
# 服务器RealTime设置
realtime-settings:
  # 是否启用该选项
  enable=true
  # 客户端是否受到RealTime的影响
  client-mode=true
  # 是否影响全局时钟（红石服不推荐开启，由于TPS降低可能会造成红石信号延迟较大）
  global-timer-mode=false

# 客户端渲染设置
client-graph-settings:
  # 是否将地毯端的tick warp时间加速应用在客户端
  carpet-tickwarp=true
  # 是否将地毯端的tick freeze应用在客户端
  carpet-tickfreeze=true
  # 是否将地毯端的tick step应用在客户端
  carpet-tickstep=true

# 服务端类加载器设置
servercore-classesloader-settings:
  # 是否将API类切换至全局广播
  global-mode-api-class=true
  # 是否将security类切换至全局广播
  global-mode-security-class=false
  # 是否检测强制类注入
  enable-force-importclasses=true

# 服务端加密设置
servercore-security-settings:
  # 是否加密数据包传输
  enbale-sha256-packs=true
  # 是否加密客户端数据
  enable-sha256-clientdata=true
  # 是否加密服务端数据
  enable-sha256-serverdata=true
  # 是否在启动时混淆源码（可能会导致额外基于Mixin的Mod失效）
  enable-random-func=false
  
# i18n设置
language=zh_CN
global=ShangHai
```
#### >>>指令与函数
这里列举了所有Impulse Core核心加入的指令，其中部分指令执行需要4级权限（op）
```
/impulse - Impulse冲动核心母指令
/help - 帮助指令
/healthreport - 使用斯波克给服务器跑个分
/timings - 使用斯波克查看服务器的Timings
/fabric - FabricAPI母指令
/carpet - CarpetMod母指令
/qf - QuickFunction母指令
/reload - 重载所有Mod、datapacks、worlds以及impulse.yml、server文件等
!!MCDR - MCDR母指令
```

#### >>>注意事项
- /reload指令仅建议在特殊时期使用，由于其需要加载几乎所有的服务端功能，需要耗费大量的运算时间，可能会导致服务器跳刻的情况发生
- /timings指令来自于Spark插件，反馈也由Spark执行并代理网站
- 如不想重载所有东西，可以在/reload指令后面加上参数，例如
```
/reload mods - 仅重载模组
/reload datapacks - 仅重载数据包
/reload worlds - 仅重载世界
/reload carpet - 仅重载CarpetMod
/reload qf - 仅重载QuickFunctions
/relaod server - 仅重载impulse.yml文件、server.properties文件
/reload mcdr - 仅重载MCDR
```
- RealTime不建议在有大量红石的服务器中启用，RealTime的本质意义就是在服务器跳刻时，不影响玩家的正常饮食、走路、交互、挖矿等延迟，但是会导致红石进程大量迂回从而造成红石机器卡死
- 服务端核心内所有加密都由SHA-256式加密并打乱顺序
- 一些功能需要客户端配备Impulse-security模组才能完成，为防止玩家删除该模组，请额外寻找支持的MD5校验启动器
