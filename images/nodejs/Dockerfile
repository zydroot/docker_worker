FROM registry.cn-qingdao.aliyuncs.com/centos-zyd/mynode:1.0

COPY ./config/package.json /mnt/app/webpack/
WORKDIR /mnt/app/webpack
RUN npm install
COPY . /mnt/app/webpack

EXPOSE 3001

#CMD ['nodejs', '/mnt/app/webpack/index']