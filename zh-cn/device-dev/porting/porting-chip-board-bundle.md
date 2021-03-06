# 三方组件适配


如果需要使用third_party目录下与产品相关的三方组件，可能需要对三方组件进行适配，下面以比较常用的mbedtls为例，介绍下适配步骤，注意本小节中仅介绍如何将适配的代码与OpenHarmony的编译框架融合，不会详细介绍mbedtls本身的原理和适配代码的具体逻辑，这些内容请参考mbedtls官方网站上的适配指南。


1. 编写适配层代码
   根据mbedtls官网的适配指南，编写需要的适配层代码，以适配硬件随机数举例，下面的路径都是相对third_party/mbedtls的路径：

   1. 拷贝include/mbedtls/config.h到ports目录下，并修改打开MBEDTLS_ENTROPY_HARDWARE_ALT开关。
   2. 在ports目录下创建entropy_poll_alt.c文件include并实现entropy_poll.h中的硬件随机数接口
   3. 在BUILD.gn中的mbedtls_sources中增加刚才适配的entropy_poll_alt.c的路径
   4. 在BIULD.gn中的lite_library("mbedtls_static")中增加一行MBEDTLS_CONFIG_FILE指定新配置文件的位置
         
       ```
       lite_library("mbedtks_static") {
         ...  
         defines += ["MBEDTLS_CONFIG_FILE=<../port/config.h>"]
         ...
       }
       ```

   注意，上面的修改最好都新建一个config或者新建一个xxx_alt.c文件来修改，不要直接在原先的代码中修改，侵入式的修改会导致后续版本升级出现大量零散冲突，增加升级维护成本。

2. 制作patch
   由于上面的适配是硬件相关的，上库代码时，不能直接放到通用的third_party/mbedtls目录中，因此需要将上面的修改制作成patch，在编译之前通过打patch的方式注入到代码中。

   1. 首先增加设备的patch配置文件device/&lt;company&gt;/&lt;board&gt;/patch.yml
   2. 编辑device/&lt;company&gt;/&lt;board&gt;/patch.yml，增加要打的patch的信息：
         
       ```
       # 需要打patch的路径，路径均为相对代码根目录的路径
       third_party/mbedtls:
         # 该路径下需要打的patch存放路径
         - device/<company>/<board>/third_party/mbedtls/adapter.patch
       third_party/wpa_supplicant:
         # 当一个路径下有多个patch的时候会依次执行patch
         - device/<company>/<board>/third_party/wpa_supplicant/xxxxx.patch
         - device/<company>/<board>/third_party/wpa_supplicant/yyyyy.patch
       ...
       ```
   3. 制作上述**步骤1**修改的patch并放到对应的目录即可

3. 使用带patch的编译
   想要在编译的时候带上patch，其他步骤不变，仅需要在触发编译的时候加上 --patch，例如全编译的命令编程

     
   ```
   hb build -f --patch
   ```

   > ![icon-caution.gif](public_sys-resources/icon-caution.gif) **注意：**
   > 最后一次打patch的产品信息会被记录，在进行下一次编译操作时，会对上一次的patch进行回退（即执行`patch -p1 -R &lt; xxx`），回退patch失败或新增patch失败均会终止编译过程，请解决patch冲突后再次尝试编译。

