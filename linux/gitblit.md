#   gitblit
+   java -version ���java����
+   wget http://dl.bintray.com/gitblit/releases/gitblit-1.8.0.tar.gz
+   mkdir -p /opt/gitblit
+   mkdir -p /opt/gitblit/repertory
+   cd /opt/gitblit
+   tar -zxvf gitblit-1.8.0.tar.gz
+   vi ./data/defaults.properties
    +   git.repositoriesFolder=/opt/gitblit/repertory
    +   server.httpPort=3345
    +   server.httpsPort = 0
    +   server.httpsBindInterface=localhost
+   vi ./service-centos.sh
    +   GITBLIT_PATH=/opt/gitblit/gitblit-1.8.0
    +   GITBLIT_BASE_FOLDER=/opt/gitblit/repertory
    +   GITBLIT_HTTP_PORT=3345
    +   GITBLIT_HTTPS_PORT=0
+   ֱ������
+		java -jar /opt/gitblit/gitblit-1.8.0/gitblit.jar --baseFolder data
+   ��̨����
+   ���޸�service-centos.sh����ִ��һ�Σ�./install-service-centos.sh
+   service gitblit start/stop/restart
+   ��ʼ����Ա�˺�admin admin
