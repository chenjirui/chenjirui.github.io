[�ʼ�������](https://www.jianshu.com/p/610d9bf0ae8b)

#	�ʼ�
+	MUA:Mail User Agent.�û��ʼ�����,�û�ͨ��MUA���շ����ʼ�
+	MTA: Mail Transfer Protocol.�ʼ��������,��SMTP��һ��ʵ��.
	���õ�MTA��sendmail,Postfix,�������ʼ��Ĵ���
+	MDA: Mail Deliver Agent,�ʼ��ַ�����.
	���𽫽��յ����ʼ��������ʼ���������.
	sendmail�Լ�PostfixĬ��ʹ�õ�MDA��procmail
+	MRA: Mail Receive Agent,�ʼ����մ���,����ʵ��IMAP,POP3Э��,
	������MUA����,���������ϵ��ʼ�ͨ��IMAP�Լ�POP3������ͻ���.
    ���õ�MRA��Dovecot.
+	LMTP:Local Mail Transfer Protocol.�����ʼ�����Э��,��SMTPЭ�����չ.
+	Postfix:һ����Դ��MTA������,����ͨ��SMTPЭ������͵��������ʼ��Լ��ɱ������ⷢ�͵��ʼ�.��sendMail����.�ֽ����еķ������׼�����Zimbra,IRedMail�ڲ�������Postfix��ΪMTA.
+	Dovecot:һ����Դ��IMAP�Լ�POP3������.ͨ����������֤�û�����Լ��ʼ��Ĵ���.
+	SPF, DKIM, DMARC:��֤���������

+	SMTPȫ����Simple Mail Transfer Protocol,���ʼ�����Э��, ��RFC5321����.
	��Ҫ�Ĺ������ǰ��ʼ���Ϣ�ӷ����˵��ʼ��������д��͵������˵��ʼ���������,
    ż������ʹ��MUA�������ʼ��Ļ�,Ҳ���ش����û��ʼ��������������Ĺ���, ���Ҳ������Э��
+	POP3,Post Office Protocol Version 3,�ʾ�Э�������,��RFC1939���ж���.
	��Ҫ�������û������ʼ�����������ĵ����ʼ�.
    ���������:�������ʼ����͵��ռ��˵��ʼ���������ʱ,�ռ��˿���ʹ���ʼ��ͻ��������ʼ�������,��δ�Ķ����ʼ��������Լ�������Ϣ��ȡ�ر��ؽ��д���.����ȡ�Ĺ�����,��ѡ����ȡ��ɾ���Լ���ȡ�겻ɾ�����ַ�ʽ,Ĭ��һ�㶼����ȡ�겻ɾ��
+	IMAP, Internet Message Access Protocol, ������Ϣ����Э��.�����pop3Э�������ʼ��Ĺ�����Ҫ����������������,IMAP�ṩ���û�Զ�̷����ʼ���������;��,���ͨ��IMAP,�û�����ֱ�ӹ����ʼ��������ϵ��ʼ�.

        		
                           DNS 
                          MX��¼
                          �J ��
                        �J   ��
                2.UDP �J     �� 4.SPF,DKIM,PTR
                    �J       ��
                  �J         ��
                MTA ----->> MTA ----->> MDA
                 ��   3.SMTP       5      ��
                 ��                       �� 6
          1.SMTP ��                       ��
                 ��          MRA ----->> /var/mal/username
                 ��           ��    8
                MUA          ��
                             �� 7.IMAP,POP3
                             ��
                             ��
                            MUA


	+	�ʼ������������ռ�
    
    

#	

+	�˿ڣ�25, 465, 587, 110, 995, 143, 993
	����ǽ

+	�Ƴ�sendmail��rpm -e sendmail ���� yum remove sendmail

+	������������

+	�޸�hostname��hostnamectl  set-hostname   mail.����

+	�޸�MTA��Ĭ���ʼ��������
alternatives --config mta
alternatives --display mta     # mat - status is manual

#	��װ postfix 
+	yum install postfix
#	���� postfix 
+	/etc/postfix/main.cf


# DELIVERY TO MAILBOX
#
# The home_mailbox parameter specifies the optional pathname of a
# mailbox file relative to a user's home directory. The default
# mailbox file is /var/spool/mail/user or /var/mail/user.  Specify
# "Maildir/" for qmail-style delivery (the / is required).
#
#home_mailbox = Mailbox
home_mailbox = Maildir/
myhostname

�ʾ�ϵͳ��������

mydomain

�ʾ�ϵͳ������

myorigin

�ӱ��������ʼ�����������

inet_interfaces

�����������ӿ�

mydestination

�ɽ����ʼ���������������

mynetworks

���ÿ�ת����Щ�������ʼ�

relay_domains

���ÿ�ת����Щ������ʼ�

#	���ݿ�
+	����mail���ݿ����Դ����ʼ���ص�ҵ��.���Ҵ����ʼ�����Ա.

create user 'mail_admin'@'localhost' identified by 'mail_13Ad';
GRANT SELECT, INSERT, UPDATE, DELETE ON mail.* TO 'mail_admin'@'localhost' IDENTIFIED BY 'mail_13Ad';
GRANT SELECT, INSERT, UPDATE, DELETE ON mail.* TO 'mail_admin'@'localhost.localdomain' IDENTIFIED BY 'mail_13Ad';
FLUSH PRIVILEGES;

	mail���ݿ���һ����4����,�ֱ�����������, �ʼ�ת��, �û���Ϣ�Լ�����·���ĸ���
	����������
	CREATE TABLE domains (domain varchar(50) NOT NULL, PRIMARY KEY (domain) );
    �ʼ�ת����
    CREATE TABLE forwardings (source varchar(80) NOT NULL, destination TEXT NOT NULL, PRIMARY KEY (source) );
    �û���
    CREATE TABLE users (email varchar(80) NOT NULL, password varchar(20) NOT NULL, PRIMARY KEY (email) );
    ����·����
    CREATE TABLE transport ( domain varchar(128) NOT NULL default '', transport varchar(128) NOT NULL default '', UNIQUE KEY domain (domain) );

#	Postfix
������������
����:/etc/postfix/mysql-virtual_domains.cf
user = mail_admin
password = mys123123
dbname = mail
query = SELECT domain AS virtual FROM domains WHERE domain='%s'
hosts = 127.0.0.1


�ʼ�ת������
����:/etc/postfix/mysql-virtual_forwardings.cf
user = mail_admin
password = mys123123
dbname = mail
query = SELECT destination FROM forwardings WHERE source='%s'
hosts = 127.0.0.1


������������
����: /etc/postfix/mysql-virtual_mailboxes.cf
user = mail_admin
password = mys123123
dbname = mail
query = SELECT CONCAT(SUBSTRING_INDEX(email,'@',-1),'/',SUBSTRING_INDEX(email,'@',1),'/') FROM users WHERE email='%s'
hosts = 127.0.0.1


�����ʼ����ļ�ӳ��
����:/etc/postfix/mysql-virtual_email2email.cf
user = mail_admin
password = mys123123
dbname = mail
query = SELECT email FROM users WHERE email='%s'
hosts = 127.0.0.1
























