# 解决Windows端口被占用问题

## 1. 查询当前系统中所有端口的使用情况
```bash
netstat -ano
```

## 2. 查询指定端口
```bash
netstat -ano | findstr "端口号"
```

## 3. 根据PID杀死进程
```bash
taskkill -F -PID "进程PID号" 
```

