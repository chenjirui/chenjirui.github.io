# ��������һ������
$ sudo systemctl start apache.service
# ����ֹͣһ������
$ sudo systemctl stop apache.service
# ����һ������
$ sudo systemctl restart apache.service
# ɱ��һ������������ӽ���
$ sudo systemctl kill apache.service
# ���¼���һ������������ļ�
$ sudo systemctl reload apache.service
# ���������޸Ĺ��������ļ�
$ sudo systemctl daemon-reload
# ��ʾĳ�� Unit �����еײ����
$ systemctl show httpd.service



Supervisor

# /usr/lib/systemd/system/supervisord.service
# supervisord service for systemd (CentOS 7.0+)
[Unit]
Description=Supervisor daemon

[Service]
Type=forking
ExecStart=/usr/bin/supervisord -c /etc/supervisord.conf
ExecStop=/usr/bin/supervisorctl $OPTIONS shutdown
ExecReload=/usr/bin/supervisorctl $OPTIONS reload
KillMode=process
Restart=on-failure
RestartSec=42s

[Install]
WantedBy=multi-user.target

�������������
systemctl enable supervisord.service
����supervisor����
systemctl start supervisord.service
�ر�supervisor����
systemctl stop supervisord.service
����޸���supervisor.service�ļ�������ͨ��reload���������¼��������ļ�
systemctl reload supervisord.service











