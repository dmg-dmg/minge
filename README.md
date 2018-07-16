hello,this is my first blog about weekly newspapers

 周报完成情况

1.github创建库           ✔

2.创建README.md          ✔

3.创建一个hugo的博客      ✔

4.Dockerfile             ✔

5.build.sh               ✔

6.run.sh                 ✔

7.周报                    ✔    

 周报完成过程

1. 建立库

hugo new site myblog 就可以建一个库

2.注册一个GitHub账号，建立一个新的仓库，建立时勾选README.md

3.创建一个hugo博客

在hugo上挑一个主题，克隆到本地themes中，修改config.toml内容

4.创建Dockerfile

FROM registry.saas.hand-china.com/tools/debian:jessie 

COPY mgblog/ /myblog/

ADD hugo_0.44_Linux-64bit.deb /tmp/hugo.deb

RUN dpkg -i /tmp/hugo.deb \ 

&& rm /tmp/hugo.deb

WORKDIR myblog/

CMD hugo

CMD  hugo server --baseUrl=192.168.99.100 --bind=0.0.0.0

EXPOSE 1313  

5.build.sh(docker build -t mgblog:v1.0 .)

run.sh(docker run -d -p 1313:1313 --name=mgblog mgblog:v1.0)

6.hugo server 正常情况下localhost:1313/可以显示主题

7.$ sh build.sh

Sending build context to Docker daemon  17.31MB

8.$ sh run.sh

a7d2e98cc8730554e5a1bf4a60ecf0e3028afbff6fab7c7a29c3ca0fcce9879f

9.git add .

git commit -m"我的博客"

git push





