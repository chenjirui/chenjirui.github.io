启动oracle数据库
su - oracle
#打开Oracle监听
lsnrctl start
#进入sqlplus
sqlplus /nolog
#使用sysdab角色登录sqlplus
conn /as sysdba
#启动数据库
startup
#关闭
shutdown
#强制关闭
shutdown abort