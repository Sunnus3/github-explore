FROM hengyunabc/arthas

MAINTAINER zhangwei/pknfe@outlook.com

# 服务名称
ARG APP_NAME=explore-rest-api
# 服务目录
ARG SERVER_HOME=/usr/${APP_NAME}
# 启动脚本名称
ARG SHELL_SCRIPT=docker-entrypoint.sh
# jar包名称
ARG JAR_NAME=explore-rest-api-1.0-SNAPSHOT.jar
# jar包所在目录
ARG JAR_DIR=.

# copy jar包和相关依赖
COPY ${JAR_DIR}/${JAR_NAME} ${SERVER_HOME}/${JAR_NAME}
COPY ${JAR_DIR}/lib ${SERVER_HOME}/lib/

# add docker-entrypoint.sh脚本
ADD https://raw.githubusercontent.com/Arugal/fragment/master/docker/${SHELL_SCRIPT} ${SERVER_HOME}/${SHELL_SCRIPT}

ENV JAR_NAME=${JAR_NAME}

ENV REMOTE_DEBUG_PORT=20002

WORKDIR ${SERVER_HOME}

RUN chmod +x ${SHELL_SCRIPT}

RUN echo "Asia/Shanghai" > /etc/timezone

ENTRYPOINT [ "./docker-entrypoint.sh" ]