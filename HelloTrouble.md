
>Face to trouble when l am using Termux.

```shell
cat test.txt | sort > test.txt
# '>' 使shell在运行cat前就清空了test.txt
```

```shell
>-l; ls
#rm ./-l 可以移除此文件
```

```
apt update
Reading package lists... Done
E: Could not get lock /data/data/com.termux/files/usr/var/lib/apt/lists/lock - open (11: Try again)
E: Unable to lock directory /data/data/com.termux/files/usr/var/lib/apt/lists/
#当apt运行时被打断，就无法自己删除锁文件
#自行手动删除
```
