# Chevereto: Ultimate image and video sharing software

<p align="center">
    <a href="https://chevereto.com"><img alt="Chevereto" src="chevereto.svg" width="80%"></a>
</p>

配置环境php 8.1 mysql 8.0.1
新建网站-添加伪静态-添加ssl
将nginx.conf的伪静态拷贝到宝塔伪静态中
安装chevereto
进入宝塔面板 → PHP设置 → 禁用函数 → 检查是否包含以下关键函数：删掉其中禁用函数
* move_uploaded_file（必须解除禁用）
* exec、shell_exec（部分程序可能依赖这些函数处理文件）
* proc_open
* putenv

编辑源代码
如果错误导致应用程序无法启动，您可以通过编辑源代码来强制显示错误。这将允许在应用程序引导过程的早期进行调试。
打开app/legacy/load/register-handlers.php
改变这个：
$doDebug = in_array($debugLevel, [2, 3], true) || isDebug();
对此：
//$doDebug = in_array($debugLevel, [2, 3], true) || isDebug();
$doDebug = true;

就可以启动使用了
