FROM cassandra:3.11.0 

ENV TZ=Europe/Moscow

RUN cd /usr/lib/apt/methods && \
    ln -s http https && \ 
    touch /etc/apt/sources.list.d/mssql-release.list && \
    echo "deb [arch=amd64] https://packages.microsoft.com/debian/8/prod jessie main" > /etc/apt/sources.list.d/mssql-release.list && \
    cd /etc/apt/sources.list.d/ && \
    mv cassandra.list cassandra.old && \
    mv backports.list backports.old

RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EB3E94ADBE1229CF 

RUN apt-get update

RUN apt-get install -y apt-transport-https python-pip 
RUN pip install pytz

RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone