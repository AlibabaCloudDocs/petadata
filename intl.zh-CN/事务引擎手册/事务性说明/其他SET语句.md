# 其他SET语句 {#concept_itd_vpk_x2b .concept}

-   其它的环境变量均被解析器拦截，报告给用户一个 warning 消息，即设置环境变量的动作未执行。

-   非事务中，环境变量设置过程与 begin 语句开启的过程相同，均为延迟开启。即用户的环境变量语句或 begin 语句到达后，立即向用户报告 ok 结果。待用户真正的请求到达时，再根据请求涉及的后端分区，进行一轮独立的环境变量设置或 begin 的过程。完成后，再进行实际的请求投递。若这轮延迟的环境变量设置或 begin 失败，则向用户报错，用户下次请求到达时，仍然会进行一轮新的环境变量设置或 begin 的过程。


