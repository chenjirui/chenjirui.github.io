##���� frp ����ѹ
wget https://github.com/fatedier/frp/releases/download/v0.9.3/frp_0.9.3_linux_amd64.tar.gz
tar -zxvf frp_0.9.3_linux_amd64.tar.gz
cd frp_0.9.3_linux_amd64

# frpc.ini
# A:\frp\frpc -c .A:\frp\frpc.ini
type = http
local_ip = 127.0.0.1
local_port = 80
use_encryption = false
use_compression = true
custom_domains = lzrui.cn

# frps.ini
# /usr/local/frp/frps -c /usr/local/frp/frps.ini &
[common]
vhost_http_port = 7776
bind_port = 7777
token = 12905678
dashboard_port = 7500
dashboard_user = ruiaa
dashboard_pwd = frp139162


#	����������
sudo vim /etc/rc.local
���/home/frp/frps(frps�ļ��ľ��Ե�ַ) -c /home/frp/frps.ini(ͬ��) &
sudo chmod +x /etc/rc.d/rc.local

nohup /usr/local/frp/frps -c /usr/local/frp/frps.ini >/usr/local/frp/log.txt 2>&1 &

#	���������ȼ��������ļ�
./frps -c ./frps.ini --reload




