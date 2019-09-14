setlocal 是指批处理本地化的一种操作，使启动批处理文件中环境变量的本地化。本地化将持续出现到匹配的 endlocal 命令或者到达批处理文件结尾为止。

1. 在执行 SETLOCAL 之后所做的环境改动只限于批处理文件
2. 要还原原先的设置，必须执行 ENDLOCAL
3. 达到批处理文件结尾时，对于该批处理文件的 **每个尚未执行的 SETLOCAL 命令**，都会有一个隐含的 ENDLOCAL 被执行。

**语法**

`setlocal {enableextensions | disableextensions} {enabledelayedexpansion | disabledelayedexpansion}`

**参数**

`enableextensions` ：启用命令扩展，直到出现匹配的 endlocal 命令为止，不考虑 setlocal 命令之前的设置。

`disableextensions` ：禁用命令扩展，直到出现匹配的 endlocal 命令，无论 setlocal 命令之前的设置如何。

> 在XP中并没有看到命令扩展的使用

`enabledelayedexpansion` ：启用变量延迟，直到出现匹配的 endlocal 命令，无论 setlocal 命令之前的设置如何。

`disabledelayedexpansion` ：禁用变量延迟，直到出现匹配的 endlocal 命令，无论 setlocal 命令之前的设置如何。

**备注**

1. 在批处理文件或脚本外使用 setlocal，是没有任何作用的

2. 改变环境变量：在运行批处理文件时使用 setlocal 更改环境变量。运行setlocal后所做的环境更改是批处理文件的本地更改。当 cmd.exe 遇到 endlocal 命令或到达批处理文件的末尾时，它会还原以前的设置

3. 在批处理程序中可以有多个 setlocal 或 endlocal 命令(即命令嵌套)

4. 测试批处理文件的命令扩展：setlocal 命令设置 ERRORLEVEL 变量。如果你传递{enableextensions | disableextensions} 或 {enabledelayedexpansion | disabledelayedexpansion} 这些参数，则ERRORLEVEL变量设置为零(0)。否则，将其设置为1(1)。可以在批处理脚本中使用此方法来确定扩展是否可用，例如：

   ```shell
   verify other 2>nul 
   setlocal enableextensions 
   if errorlevel 1 echo Unable to enable extensions
   ```

   由于在禁用命令扩展名时，cmd 不设置 ERRORLEVEL 变量，因此当你将 ERRORLEVEL 变量与无效参数一起使用时，验证命令会将 ERRORLEVEL 变量初始化为非零值。此外，如果你使用 setlocal 命令和参数{enableextensions | disableextensions} 或 {enabledelayedexpansion | disabledelayedexpansion} ，并且它没有将 ERRORLEVEL 变量设置为1(1)，则命令扩展名不可用。有关启用和禁用命令扩展插件的详细信息，请参阅相关主题中的cmd。

