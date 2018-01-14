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
