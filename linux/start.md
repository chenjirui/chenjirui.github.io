#   gitblit
service gitblit start/stop/restart

#		supervisor
supervisord -c /etc/supervisord.conf

#		tomcat
/usr/local/tomcat/bin/startup.sh
/usr/local/tomcat/bin/shutdown.sh



����oracle���ݿ�
su - oracle
#��Oracle����
lsnrctl start
#����sqlplus
sqlplus /nolog
#ʹ��sysdab��ɫ��¼sqlplus
conn /as sysdba
#�������ݿ�
startup
#�ر�
shutdown
#ǿ�ƹر�
shutdown abort