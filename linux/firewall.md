https://www.cnblogs.com/zhansu/p/9231793.html

vultr��80�˿ڣ�
1.�鿴����ǽ�汾��
firewall-cmd --version
2.�鿴����ǽ״̬
firewall-cmd --state
3.���80�˿ڵ�Ȩ��
firewall-cmd --zone=public --add-port=80/tcp --permanent
����壺
--zone #������
--add-port=80/tcp #��Ӷ˿ڣ���ʽΪ���˿�/ͨѶЭ��
--permanent #������Ч��û�д˲���������ʧЧ
4.��������ǽ
systemctl restart firewalld

firewall-cmd --list-all