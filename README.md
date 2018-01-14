# AppiumLibrary-HaiXia

Library version:1.6

---

### **介绍**

本文档是我行的Robotframework-AppiumLibrary的底层关键字的使用手册。

---

### **关键字**

#### Open Application
 - 功能
 
 开启设备
 
 - 参数
 
remote_url, alias=None, **kwargs

 - 例子
<table>
    <tr>
        <td>Open Application</td>
        <td>http://localhost:4723/wd/hub</td>
        <td>platformName=Android</td>
        <td>platformVersion=7.0</td>
        <td>deviceName=b251f00d</td>
        <td>udid=b251f00d</td>
        <td>app=${CURDIR}/Haixiabank.apk</td>
        <td>appPackage=com.haixia</td>                                   
        <td>appActivity=.ui.SplashScreenActivity</td>
        <td>unicodeKeyboard=True</td>   
        <td>resetKeyboard=True</td>
    </tr>
</table>

#### Close Application
 - 功能
 
 关闭设备

#### Reset Application
 - 功能
 
 重启设备

#### Set Application Timeout
 - 功能
 
 设置Appium超时时长
 
 - 参数
 
seconds

 - 例子
<table>
    <tr>
        <td>Set Application Timeout</td>
        <td>120</td>
    </tr>
</table>

#### Get Appium Timeout
 - 功能
 
 获取Appium超时时长

#### Get Source
 - 功能
 
 获取页面DOM代码

#### Lock
 - 功能
 
 锁定设备
 
 - 参数
 
seconds=1

 - 例子
<table>
    <tr>
        <td>Lock</td>
        <td></td>
    </tr>
    <tr>
        <td>Lock</td>
        <td>2</td>
    </tr>
</table>

#### Background App
 - 功能
 
 跳转桌面一段时间后，返回APP界面
 
 - 参数
 
seconds=5

 - 例子
<table>
    <tr>
        <td>Background_App</td>
        <td></td>
    </tr>
    <tr>
        <td>Background_App</td>
        <td>10</td>
    </tr>
</table>

#### Shake
 - 功能
 
 手机摇一摇，只适用IOS手机

#### Landscape
 - 功能
 
 定制横屏

#### Portrait
 - 功能
 
 定制竖屏

#### Get Current Context
 - 功能
 
 获取当前界面Context

#### Get Contexts
 - 功能
 
 获取所有Context

#### Switch To Context
 - 功能
 
 切换context
 
 - 参数
 
context_name

 - 例子
<table>
    <tr>
        <td>Switch To Context</td>
        <td>Native_App</td>
    </tr>
</table>

#### Get Network Connection Status
 - 功能
 
 获取APP网络连接状态，只适用于Android。

#### Set Network Connection Status
 - 功能
 
 设置APP网络连接状态，只适用于Android。

 - 参数
 
capability_name

 Value | Alias| Data | Wifi | Airplane Mode  
 ---| ---| ---|---|---|
 0      | (None)           | 0      |   0    | 0       
 1      | (Airplane Mode)  | 0      |   0    | 1       
 2      | (Wifi only)      | 0      |   1    | 0      
 4      | (Data only)      | 1      |   0    | 0       
 6      | (All network on) | 1      |   1    | 0       
 
 - 例子
<table>
    <tr>
        <td>Set Network Connection Status</td>
        <td>6</td>
    </tr>
</table>

#### Get Capability
 - 功能
 
 获取desired capability配置参数
 
 - 参数
 
capability_name

 - 例子
<table>
    <tr>
        <td>Get Capability</td>
        <td>appActivity</td>
    </tr>
</table>

#### Pull File
 - 功能
 
 输出手机指定目录path的text文档内容，只适用于Android。
 
 - 参数
 
path, decode=True

 - 例子
<table>
    <tr>
        <td>Pull File</td>
        <td>storage/emulated/0/Download/example.txt</td>
    </tr>
</table>

#### Push File
 - 功能
 
 给手机指定目录path的text文档写入data，只适用于Android。
 
 - 参数
 
path, data, encode=True

 - 例子
<table>
    <tr>
        <td>Push File</td>
        <td>storage/emulated/0/Download/example.txt</td>
        <td>12ab测试</td>
    </tr>
</table>

#### Get Activity
 - 功能
 
 获取APP当前Activity

#### Start Activity
 - 功能
 
 开启指定Activity，只适用于Android。
 
 - 参数
 
appPackage, appActivity, **opts

```
- _appPackage_ - The package containing the activity to start.
- _appActivity_ - The activity to start.
- _appWaitPackage_ - Begin automation after this package starts (optional).
- _appWaitActivity_ - Begin automation after this activity starts (optional).
- _intentAction_ - Intent to start (opt_ional).
- _intentCategory_ - Intent category to start (optional).
- _intentFlags_ - Flags to send to the intent (optional).
- _optionalIntentArguments_ - Optional arguments to the intent (optional).
- _stopAppOnReset_ - Should the app be stopped on reset (optional)?
```

 - 例子
<table>
    <tr>
        <td>Start Activity</td>
        <td>com.haixia</td>
        <td>.ui.SplashScreenActivity</td>
    </tr>
</table>

#### Wait Activity
 - 功能
 
 等待指定Activity，只适用于Android。
 
 - 参数
 
activity, timeout, interval=1

 - 例子
<table>
    <tr>
        <td>.ui.SplashScreenActivity</td>
        <td>5</td>
    </tr>
</table>

#### Press Keycode
 - 功能
 
 按物理按键代码，只适用于Android。
 
 - 参数
 
keycode, metastate=None

 - 例子
 
开启拨号键
<table>
    <tr>
        <td>Press Keycode</td>
        <td>5</td>
    </tr>
</table>

#### Long Press Keycode
 - 功能
 
 长按物理按键代码，只适用于Android。
 
 - 参数
 
keycode, metastate=None

#### Capture Page Screenshot
 - 功能
 
 截屏，只能在APP原生页面及无反截屏的情况下可以使用,自定义储存至输出报告路径。
 
 - 参数
 
filename=None

#### Wait Until Element Is Visible
 - 功能
 
 测试等待至某元素属性为可见
 
 - 参数
 
locator, timeout=None, error=None

 - 例子
<table>
    <tr>
        <td>Wait Until Element Is Visible</td>
        <td>id=menu_list_layout</td>
        <td>error=元素无法找到</td>
    </tr>
</table>

#### Wait Until Page Contains
 - 功能
 
  测试等待至页面出现指定字符串
 
 - 参数
 
text, timeout=None, error=None

 - 例子
<table>
    <tr>
        <td>Wait Until Page Contains</td>
        <td>交易成功</td>
        <td>20</td>
        <td>error=交易不成功</td>
    </tr>
</table>

#### Wait Until Page Does Not Contain
 - 功能
 
 测试等待至页面指定字符串消失
 
 - 参数
 
text, timeout=None, error=None

 - 例子
<table>
    <tr>
        <td>Wait Until Page Does Not Contain</td>
        <td>交易失败</td>
        <td>20</td>
    </tr>
</table>

#### Wait Until Page Contains Element
 - 功能
 
 测试等待至页面出现指定定位元素
 
 - 参数
 
locator, timeout=None, error=None

 - 例子
<table>
    <tr>
        <td>Wait Until Page Contains Element</td>
        <td>id=menu_list_layout</td>
        <td>20</td>
    </tr>
</table>

#### Wait Until Page Does Not Contain Element
 - 功能
 
 测试等待至页面指定定位元素消失
 
 - 参数
 
locator, timeout=None, error=None

 - 例子
<table>
    <tr>
        <td>Wait Until Page Does Not Contain Element</td>
        <td>id=ContainerOfCoverView</td>
        <td>20</td>
        <td>error=元素一直存在</td>
    </tr>
</table>
