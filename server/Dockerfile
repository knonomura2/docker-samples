FROM centos:7

RUN rpm -ivh https://github.com/griddb/griddb_nosql/releases/download/v4.2.1/griddb_nosql-4.2.1-1.linux.x86_64.rpm

RUN set -x &&\
su - gsadm -c "gs_passwd admin -p admin"

RUN set -x && \
sed -i -e s/\"clusterName\":\"\"/\"clusterName\":\"dockerGridDB\"/g \
/var/lib/gridstore/conf/gs_cluster.json

CMD su - gsadm -c \
"gs_startnode && gs_joincluster -c dockerGridDB -u admin/admin" &&\
tail -f /dev/null
