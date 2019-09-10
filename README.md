## 使用Dockerfile搭建hadoop+spark单容器伪分布式服务
### 开发环境
ubuntu16.04  
docker  
### 搭建镜像环境
ubuntu16.04  
python3.5  
jdk1.8.0  
hadoop2.9.2  
spark2.4.4  
### 搭建过程
1.进入文件夹，创建镜像(时间大概15分钟)  
cd SparkHadoopAlone/  
docker build -t test .  
<img src="https://github.com/LiuChen-China/SparkHadoopAlone/blob/master/Static/Image/1.png" width=100%>
<img src="https://github.com/LiuChen-China/SparkHadoopAlone/blob/master/Static/Image/2.png" width=100%>

2.实例化容器后，开启容器，进入容器，top后可以看到java,ssh,hadoop,spark服务已开启  
docker run -it -d -p 8000:22 --name=test test  
docker exec -it test /bin/bash  
<img src="https://github.com/LiuChen-China/SparkHadoopAlone/blob/master/Static/Image/3.png" width=100%>
### 测试
紧接搭建过程第2点，此时可以通过xshell等工具进行远程连接容器或者直接在容器中操作  
1.将容器中的word.txt放入hadoop文件系统中  
hadoop fs -put word.txt /word.txt  
<img src="https://github.com/LiuChen-China/SparkHadoopAlone/blob/master/Static/Image/4.png" width=100%>
2.执行Test.py，即可看到word.txt的词频统计  
python3 Test.py  
<img src="https://github.com/LiuChen-China/SparkHadoopAlone/blob/master/Static/Image/5.png" width=100%>

