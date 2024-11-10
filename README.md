
在 Linux 上使用 `screen` 是一种保持进程持续运行的便捷方式，即使用户断开 SSH 连接，进程也不会中断。


我在使用VSCode连接AutoDL时，不知道如何能够使进程保持运行，后查阅资料可以使用screen命令完成该需求。


## 连接远程服务器


首先使用VSCode或者PyCharm连接到远程服务器


## 启动一个新的 `screen` 会话



```


|  | screen -S mysession |
| --- | --- |


```

`-S mysession`：为这个会话命名为 `mysession`，方便后续管理。


## 在 `screen` 会话中启动你的程序


启动会话后，你可以运行任何想要保持运行的程序，例如：



```


|  | python train.py |
| --- | --- |


```

## 分离 `screen` 会话（保持进程运行）


按下以下组合键来分离 `screen` 会话，但不会终止运行的程序：



```


|  | Ctrl + A, 然后按 D |
| --- | --- |


```

* `Ctrl + A`：这是 `screen` 的命令前缀。
* `D`：表示分离（detach）。


## 查看当前所有 `screen` 会话



```


|  | screen -ls |
| --- | --- |


```

输出示例：这里的7171是会话ID，mysession是会话名



```


|  | There is a screen on: |
| --- | --- |
|  | 7171.mysession  (11/09/2024 08:39:43 PM)        (Detached) |
|  | 1 Socket in /run/screen/S-root. |


```

## 恢复（重新连接）到 `screen` 会话


使用 `screen -r <会话名或ID>` 来终止会话。



```


|  | # 根据会话名 |
| --- | --- |
|  | screen -r mysession |
|  |  |
|  | # 或根据会话 ID |
|  | screen -r 7171 |


```

如果你只启动了一个 `screen` 会话，也可以直接使用：



```


|  | screen -r |
| --- | --- |


```

## 终止指定`screen` 会话


使用 `screen -X -S <会话名或ID> quit` 来终止会话。



```


|  | # 根据会话名 |
| --- | --- |
|  | screen -X -S mysession quit |
|  |  |
|  | # 或根据会话 ID |
|  | screen -X -S 7171 quit |


```

使用 `kill` 命令杀掉会话进程，`kill ID`



```


|  | # 杀掉进程 |
| --- | --- |
|  | kill 7171 |


```

 本博客参考[FlowerCloud机场](https://hushicha.org)。转载请注明出处！
