FROM python:3.8.3
ENV APP_ROOT /src
ENV CONFIG_ROOT /config
RUN mkdir ${CONFIG_ROOT} ${APP_ROOT}
COPY requirements.txt ${CONFIG_ROOT}/
RUN pip install --no-cache-dir -r ${CONFIG_ROOT}/requirements.txt
WORKDIR ${APP_ROOT}
ADD . ${APP_ROOT}
