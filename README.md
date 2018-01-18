# AppiumLibrary-HaiXia

Library version:1.6

---

### **介绍**

本文档是我行的Robotframework-AppiumLibrary的底层关键字的使用手册。

---

### **定位策略**

策略 | 案例 | 备注 
---| ---| ---
identifier | identifier=my_element	
id | id=my_element	
className | class=my_class
name | name=my_element | appium1.5后失效
xpath | xpath=//android.widget.Button[contains(@content-desc,'同意')]
css_selector | css=.my_button
accessibility_id | accessibility_id=my_button | Android、IOS通用，IOS里要打开Accessibility权限
juery | jquery=input[value=填写完啦][class=btBlue] | 适用于H5页面
link_text | text=my_text | 定位含链接属性的文本标签
tag_name | tag=EditText
android_uiautomator | android=UiSelector().description('Apps') | 适用于Android系统
ios_uiautomator | ios=.buttons().withName('Apps') | 适用于IOS10以下
ios_predicate | type == 'XCUIElementTypeButton' AND label == '更多信息' | IOS10及以上限定
ios_class_chain | XCUIElementTypeWindow[1]/XCUIElementTypeOther[1] | IOS10及以上限定
默认 | my_element | 默认为识别id标签


---

### **关键字详情**

#### Open Application
 - 功能
 
 开启设备，端口设置的注意事项如下：
 Appium通过Chromedriver内建混合应用支持，同时确保开发将WebView的setWebContentsDebuggingEnabled设置为true，4.4之前的设备使用 Selendroid支持webview 测试（"automationName": "selendroid"）。
 
 uiautomator2驱动下——
    udid、chromeDriverPort、systemPort、automationName
    
 wda驱动下——
 真机：
    udid、wdaLocalPort
 虚拟机：
    udid、deviceName、platformVersion、wdaLocalPort
    
 Safari驱动下——
    browserName、udid、wdaLocalPort、webkitDebugProxyPort
    
 不安装APP——
    noReset=True
    
 Android键盘设置——
    unicodeKeyboard=True、resetKeyboard=True
    
 微信WebView——
    微信打开debugx5.qq.com，可以在任何聊天窗口内输入这个网址，并打开它，勾选“是否打开TBS内核Inspector调试功能”；然后，设置chromeOptions类选项，如：androidProcess", "com.tencent.mm:appbrand0")//对应被测小程序appbrand0
 
 其他详见：https://github.com/appium/appium/blob/master/docs/cn/writing-running-appium/caps.md
 
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
        <td>appActivity=.ui.Splash1ScreenActivity</td>
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
        <td>.ui.Splash1ScreenActivity</td>
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
        <td>.ui.Splash1ScreenActivity</td>
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

#### Zoom
 - 功能
 
 实现元素的放大，appium1.7上存在BUG
 
 - 参数
 
locator, percent=200, steps=1

```
    - element - the element to zoom
    - percent - (optional) amount to zoom. Defaults to 200%
    - steps - (optional) number of steps in the zoom action
```

#### Pinch
 - 功能
 
 实现元素的缩放，appium1.7上存在BUG
 
 - 参数
 
locator, percent=200, steps=1

```
    - element - the element to pinch
    - percent - (optional) amount to pinch. Defaults to 200%
    - steps - (optional) number of steps in the pinch action
```

#### Swipe
 - 功能
 
 实现屏幕滑动，若偏移量和间隔时间过短，效果与点击相同。在Android系统中，offset_x与offset_y为目标点坐标；在IOS系统中，offset_x与offset_y为偏移量。
 
 - 参数
 
start_x, start_y, offset_x, offset_y, duration=1000

 - 例子

Android点击
<table>
    <tr>
        <td>Swipe</td>
        <td>230</td>
        <td>400</td>
        <td>230</td>
        <td>400</td>
        <td>100</td>
    </tr>
</table>

IOS滑动
<table>
    <tr>
        <td>Swipe</td>
        <td>230</td>
        <td>400</td>
        <td>830</td>
        <td>400</td>
    </tr>
</table>

#### Swipe By Percent
 - 功能
 
 百分比滑动，原理与Swipe类似，进行了优化，Androi/IOS输入方式相同，均为起始坐标
 
 - 参数
 
start_x, start_y, end_x, end_y, duration=1000

 - 例子

右向左滑动
<table>
    <tr>
        <td>Swipe By Percent</td>
        <td>90</td>
        <td>30</td>
        <td>10</td>
        <td>30</td>
        <td>1200</td>
    </tr>
</table>

#### Scroll
 - 功能
 
 元素间滚动
 
 - 参数
 
start_locator, end_locator

#### Scroll Down
 - 功能
 
 向下滚动，定位元素要有滚动属性，appium1.7上存在BUG
 
 - 参数
 
locator

#### Scroll Up
 - 功能
 
 向上滚动，定位元素要有滚动属性，appium1.7上存在BUG
 
 - 参数
 
locator

#### Long Press
 - 功能
 
 长按某个元素
 
 - 参数
 
locator

#### Tap
 - 功能
 
 多次敲击，默认次数为1
 
 - 参数
 
locator, count=1

#### Click A Point
 - 功能
 
 点击一个坐标点，间隔不得过短。
 
 - 参数
 
 x=0, y=0, duration=1000

 - 例子
<table>
    <tr>
        <td>Click A Point</td>
        <td>400</td>
        <td>600</td>
    </tr>
</table>

#### Click Element At Coordinates
 - 功能
 
 类似Click A Point，点击坐标点。
 
 - 参数
 
coordinate_X, coordinate_Y

#### Clear Text
 - 功能
 
 唯一定位条件下，清空该元素的输入文本。
 
 - 参数
 
locator

#### Click Element
 - 功能
 
 唯一定位条件下，点击该元素
 
 - 参数
 
locator

#### Input Text
 - 功能
 
 唯一定位条件下，给该元素输入文本
 
 - 参数
 
locator

#### Hide Keyboard
 - 功能
 
 IOS隐藏键盘
 
 - 参数
 
key_name=None

#### Page Should Contain Text
 - 功能
 
 断言，页面应存在指定字符串，否则报错。
 
 - 参数
 
text, loglevel='INFO'

 - 例子
<table>
    <tr>
        <td>Page Should Contain Text</td>
        <td>交易成功</td>
    </tr>
</table>

#### Page Should Not Contain Text
 - 功能
 
 断言，页面不应存在指定字符串，否则报错。
 
 - 参数
 
text, loglevel='INFO'

#### Mobile Clear Text
 - 功能
 
 清空指定元素的输入文本，定位方法详见定位策略。
 
 - 参数
 
locator, position=1

 - 例子
<table>
    <tr>
        <td>Mobile Clear Text</td>
        <td>id=PrdName</td>
    </tr>
</table>

#### Mobile Click Element
 - 功能
 
 点击指定元素，定位方法详见定位策略。
 
 - 参数
 
locator, position=1

 - 例子
<table>
    <tr>
        <td>Mobile Click Element</td>
        <td>id=menu_list_layout</td>
        <td>3</td>
    </tr>
</table>

#### Mobile Input Text
 - 功能
 
 给指定元素输入文本，定位方法详见定位策略。
 
 - 参数
 
locator, text, position=1

 - 例子
<table>
    <tr>
        <td>Mobile Input Text</td>
        <td>xpath=//android.widget.Button[contains(@content-desc,'下一步')]</td>
    </tr>
</table>

#### Mobile Input Value
 - 功能
 
 给指定元素输入值，方法类似Mobile Input Text。
 
 - 参数
 
locator, value, position=1

#### Mobile Element Is Present
 - 功能
 
 检查指定元素是否存在，存在返回True，不存在返回False
 
 - 参数
 
locator

#### Mobile Get Element Attribute
 - 功能
 
 获取指定元素属性，属性包括name, contentDescription, text, className, resourceId, enabled, checkable, checked, clickable, focusable, focused, longClickable, scrollable, selected, displayed，定位方法详见定位策略。
 
 - 参数
 
locator, attribute, position=1

 - 例子
<table>
    <tr>
        <td>Mobile Get Element Attribute</td>
        <td>xpath=//android.widget.Button[contains(@content-desc,'下一步')]</td>
        <td>contentDescription</td>
    </tr>
</table>

#### Mobile Get Element Bounds
 - 功能
 
 获取指定元素边界属性，返回值为tuple，定位方法详见定位策略。
 
 - 参数
 
locator, position=1

 - 例子
<table>
    <tr>
        <td>Mobile Get Element Bounds</td>
        <td>accessibility_id=查询</td>
    </tr>
</table>

#### Mobile Get Element Location
 - 功能
 
 获取指定元素左上角location，返回值为key为x轴与y轴坐标的dict，定位方法详见定位策略。
 
 - 参数
 
locator, position=1

#### Mobile Get Element Size
 - 功能
 
 获取指定元素size大小，返回值为key为width与 height的dict，定位方法详见定位策略。
 
 - 参数
 
locator, position=1

#### Mobile Element Should Be Disabled
 - 功能
 
 断言，页面指定元素属性为disabled，否则报错。
 
 - 参数
 
locator, loglevel='INFO', position=1

#### Mobile Element Should Be Enabled
 - 功能
 
 断言，页面指定元素属性为enabled，否则报错。
 
 - 参数
 
locator, loglevel='INFO', position=1

#### Mobile Element Name Should Be
 - 功能
 
 断言，判断指定元素name属性是否存在，定位方法详见定位策略。
 
 - 参数
 
locator, expected, position=1

 - 例子
<table>
    <tr>
        <td>Mobile Element Name Should Be</td>
        <td>id=menu_list_name</td>
        <td>信用卡</td>
    </tr>
</table>

#### Mobile Element Text Check
 - 功能
 
 判断指定元素text属性是否存在，存在返回True,不存在返回False，定位方法详见定位策略。
 
 - 参数
 
locator, expected, position=1

#### Mobile Element Attribute Should Match
 - 功能
 
 断言，判断指定元素指定属性是否匹配，定位方法详见定位策略。
 
 - 参数
 
locator, attr_name, match_pattern, position=1, regexp=False

 - 例子
<table>
    <tr>
        <td>Mobile Element Attribute Should Match</td>
        <td>id=menu_list_name</td>
        <td>name</td>
        <td>转账汇款</td>
    </tr>
</table>

#### Mobile Click Text Button
 - 功能
 
 根据文本点击按钮，定位方法详见定位策略。
 
 - 参数
 
text, position=1

 - 例子
<table>
    <tr>
        <td>Mobile Click Text Button</td>
        <td>信用卡</td>
    </tr>
</table>

#### Mobile Long Press Text Button
 - 功能
 
 根据文本长按按钮，定位方法详见定位策略。
 
 - 参数
 
text, position=1

#### Mobile Get Elements Num
 - 功能
 
 返回指定元素的个数 0-n，定位方法详见定位策略。
 
 - 参数
 
locator

 - 例子
<table>
    <tr>
        <td>${element_num}</td>
        <td>Mobile Get Elements Num</td>
        <td>id=menu_list_name</td>
    </tr>
</table>

#### Mobile Get Text Button Num
 - 功能
 
 返回指定文本按钮元素的个数0-n，定位方法详见定位策略。
 
 - 参数
 
text

#### Mobile Swipe In Element
 - 功能
 
 Android方法，在指定元素内滑动，每次上下滑动元素一半可视长度。
 
 - 参数
 
locator, position=1

#### Mobile Jsexecute
 - 功能
 
 H5界面运行简单js代码。
 
 - 参数
 
locator

 - 例子
<table>
    <tr>
        <td>Mobile Jsexecute</td>
        <td>$("[value='填写完啦']").click();</td>
    </tr>
</table>

#### Page Should Contain Element
 - 功能
 
 断言，判断界面应存在指定元素，不存在则报错。
 
 - 参数
 
locator, loglevel='INFO'

#### Page Should Not Contain Element
 - 功能
 
 断言，判断界面不应存在指定元素，存在则报错。
 
 - 参数
 
locator, loglevel='INFO'

#### Mobile Page Should Contain Element
 - 功能
 
 类似Page Should Contain Element，断言，判断界面应存在指定元素，不存在则报错，定位方法详见定位策略。
 
 - 参数
 
locator, position=1, loglevel='INFO'

#### Mobile Page Should Not Contain Element
 - 功能
 
 类似Page Should Not Contain Element，断言，判断界面不应存在指定元素，存在则报错，定位方法详见定位策略。
 
 - 参数
 
locator, position=1, loglevel='INFO'

#### Mobile Element Should Contain Text
 - 功能
 
 断言，判断指定元素应存在字符串expected，不存在则报错，定位方法详见定位策略，message为自定义报错内容。
 
 - 参数
 
expected, locator, position=1, message=''

 - 例子
<table>
    <tr>
        <td>Mobile Element Should Contain Text</td>
        <td>生活缴费</td>
        <td>class=android.widge.TextView</td>
        <td></td>
        <td>对应元素不存在</td>
    </tr>
</table>

#### Mobile Element Should Not Contain Text
 - 功能
 
 断言，判断指定元素不应存在字符串expected，存在则报错，定位方法详见定位策略。
 
 - 参数
 
expected, locator, position=1, message=''

#### Get Elements
 - 功能
 
 输出指定定位条件的元素集合，结果为WebElement链表类型。
 
 - 参数
 
locator, first_element_only=False, fail_on_error=True

 - 例子
<table>
    <tr>
        <td>@{elements}</td>
        <td>Get elements</td>
        <td>id=menu_list_name</td>
    </tr>
    <tr>
        <td>Click Element</td>
        <td>@{elements}[0]</td>
        <td></td>
    </tr>
</table>

#### Open Gt
 - 功能
 
 打开GT软件，输入APP序列号，仅限Android系统；注意：这里需要保证手机开启root权限，如果遇到“Read-only file system”的错误需要，给系统路径赋予最高权限，常用的语句有：
adb remount
adb shell su后mount -o remount rw /system
adb shell su后mount -o remount,rw /system
恢复原来状态则将rw改为ro
 
 - 参数
 
device

#### Start Gt
 - 功能
 
 开启GT监控，输入APP序列号、appPackage，监控内容包括cpu、cpu时间片、物理内存pss、内存PrivateDirty、流量、帧率，仅限Android系统
 
 - 参数
 
device, package

 - 例子
<table>
    <tr>
        <td>Start Gt</td>
        <td>b251f01d</td>
        <td>com.haixia</td>
        <td>.ui.Splash1ScreenActivity</td>
        <td>7.0</td>
    </tr>
</table>

#### End Gt
 - 功能
 
 结束GT监控，输入APP序列号、appPackage，仅限Android系统
 
 - 参数
 
device, package

 - 例子
<table>
    <tr>
        <td>End Gt</td>
        <td>b251f01d</td>
        <td>com.haixia</td>
        <td>7.0</td>
    </tr>
</table>

#### background
 - 功能
 
 重新唤起APP当前appPackage，输入APP序列号、appPackage，仅限Android系统
 
 - 参数
 
device, package

#### Mobile Detect Click
 - 功能
 
 寻找图片区域在APP界面中的位置，并点击，特征点查询算法包括SIFT、SURF、ORB等
 
 - 参数
 
inputimg, alogorithm = 'SIFT'

- 例子
<table>
    <tr>
        <td>Mobile Detect Click</td>
        <td>${CURDIR}/test.png</td>
        <td>ORB</td>
    </tr>
</table>

#### Mobile Detect
 - 功能
 
 断言，寻找图片区域在APP界面中的位置，找不到则报错，方法类似Mobile Detect Click
 
 - 参数
 
inputimg, alogorithm = 'SIFT'

#### Mobile Image Compare
 - 功能
 
 手机UI截图比对，比对算法包括直方图法HIST、平均哈希法AHASH、差异值哈希DHASH、感知哈希法PHASH等
 
 - 参数
 
inputimg, alogorithm = 'PHASH'

#### Mobile Device Time
 - 功能
 
 获取当前APP对应的设备时间

#### Mobile Active Ime Engine
 - 功能
 
 获取APP当前输入法

#### Mobile Activate Ime Engine
 - 功能
 
 变更APP当前输入法

 - 参数
 
ime

- 例子
<table>
    <tr>
        <td>Mobile Activate Ime Engine</td>
        <td>com.sohu.inputmethod.sogou.xiaomi/.SogouIME</td>
    </tr>
</table>

#### Mobile Tap
 - 功能
 
 多点触碰,坐标成对输入,最后一项可输入duration

 - 参数
 
*args

- 例子
<table>
    <tr>
        <td>Mobile Tap</td>
        <td>500</td>
        <td>1000</td>
        <td>600</td>
        <td>1300</td>
    </tr>
</table>

#### Mobile Drag And Drop
 - 功能
 
 滑动拖拽

 - 参数
 
origin, destination

- 例子
<table>
    <tr>
        <td>Mobile Activate Ime Engine</td>
        <td>id=bt_login</td>
        <td>id=bt_register</td>
    </tr>
</table>
 
---
