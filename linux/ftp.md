#   vsftpd
+   yum install -y vsftpd
+   vi /etc/vsftpd/vsftpd.conf
    +   anonymous_enable=NO ��������������
    +   local_enable=YES ����ʹ�ñ����ʻ�����FTP�û���¼��֤
    +   chroot_local_user=YES  chroot_list_enable=YES  chroot_list_file=/etc/vsftpd/chroot_list
    
        ��/etc/vsftpd.chroot_list�ļ����г����û��������л�������Ŀ¼��δ���ļ����г����û��������л�������Ŀ¼��
        
    +   ascii_upload_enable=YES ascii_download_enable=YES ֧��ASCIIģʽ���ϴ�������
    +   allow_writeable_chroot=YES �����ļ�������
+   touch /etc/vsftpd/chroot_list ����
+   systemctl restart vsftpd.service ����vsftpd
+   systemctl start vsftpd.service    # ��������
+   systemctl status vsftpd.service   # ����״̬�鿴
+   
+   �½�FTP�û� useradd -d /var/ftp/public_root -g ftp -s /sbin/nologin ftpuser
+   �޸ĸ�FTP�û����� passwd ftpuser
+   
+   ftp:
    +   open host
    +   ls
    +   put/send LocalFile [RemoteFile]  ��� mput *.txt 
    +   get RemoteFile [LocalFile]  ��� mget *.txt 
    +   lcd ����Ŀ¼·��  !chdir �鿴��ǰĿ¼
    +   cd ������Ŀ¼    dir �鿴��ǰĿ¼
    +   bye
    