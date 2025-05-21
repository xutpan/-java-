-java-

一、文件准备（2 个核心文件）
1. 创建Java 源文件（SimpleApp.java）
使用vim编辑器创建SimpleApp.java，内容如下：
vi SimpleApp.java

public class SimpleApp { 
public static void main(String[] args) {
 System.out.println("Containerized Java App!"); 
} 
}
2.创建Docker 配置文件（Dockerfile）
使用vim编辑器创建Dockerfile，内容如下：
vi  Dockerfile

# 使用 OpenJDK 8 轻量运行时镜像 
FROM openjdk:8-jdk-slim 
# 设置容器内的工作目录 
WORKDIR /app 
# 假设源文件名为 SimpleApp.java，根据实际情况调整 
COPY SimpleApp.java . 
# 编译 Java 源文件 
RUN javac SimpleApp.java 
# 定义容器启动命令 
CMD ["java", "SimpleApp"]


3. 在本地创建一个空目录（docker），并将两个文件(SimpleApp.java, Dockerfile)放入该目录(docker)中:
cp ~/SimpleApp.java  ~/docker/
cp ~/Dockerfile  ~/docker/
cd docker 
ls

4.在文件所在目录（docker）的终端中构建 Docker 镜像并执行以下命令：
docker build -t simple-java-app .

5.容器构建成功后，执行以下命令启动容器：
docker run simple-java-app
