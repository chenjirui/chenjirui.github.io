�г���ǰ�洢�豸�ϵ�swapʹ�����
swapon -s

���̵Ŀ��ÿռ�
df -h


����Swap�ļ�
��Ŀ¼��/���´���һ������swapfile���ļ�
���ݵĴ�����ʽ��fallocate����������ܹ�����һ��Ԥ����ָ����С�ռ���ļ�����������ָ���һ��4GB���ļ���
sudo fallocate -l 4G /swapfile



����Swap�ļ�
chmod 600 /swapfile
mkswap /swapfile
swapon /swapfile

Swap�ļ�������Ч 
vi /etc/fstab
�ļ�ĩβ����
/swapfile   swap    swap    sw  0   0

���
swapon -s

















