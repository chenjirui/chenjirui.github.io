+	����jar��java -jar filepath.jar

javac Convertmp3.java


jar -cvf lamemp3.jar com/ruiaa/helper/*.class

jar -cvf lamemp3.jar Convertmp3.class


jar
�÷�: jar {ctxui}[vfmn0PMe] [jar-file] [manifest-file] [entry-point] [-C dir] files ...
ѡ��:
    -c  �����µ���
    -t  �г�����Ŀ¼
    -x  �ӵ�������ȡָ���� (������) �ļ�
    -u  �������е���
    -v  �ڱ�׼�����������ϸ���
    -f  ָ�������ļ���
    -m  ����ָ���嵥�ļ��е��嵥��Ϣ
    -n  �����µ�����ִ�� Pack200 �淶��
    -e  Ϊ���󵽿�ִ�� jar �ļ��Ķ���Ӧ�ó���ָ��Ӧ�ó�����ڵ�
    -0  ���洢; ��ʹ���κ� ZIP ѹ��
    -P  �����ļ����е�ǰ�� '/' (����·��) �� ".." (��Ŀ¼) ���
    -M  ��������Ŀ���嵥�ļ�
    -i  Ϊָ���� jar �ļ�����������Ϣ
    -C  ����Ϊָ����Ŀ¼�����������ļ�
����κ��ļ�ΪĿ¼, �������еݹ鴦��
�嵥�ļ���, �����ļ�������ڵ����Ƶ�ָ��˳���� 'm', 'f' �� 'e' ��ǵ�ָ��˳����ͬ��

ʾ�� 1: ���������ļ��鵵��һ����Ϊ classes.jar �ĵ�����:
       jar cvf classes.jar Foo.class Bar.class
ʾ�� 2: ʹ�����е��嵥�ļ� 'mymanifest' ���� foo/ Ŀ¼�е������ļ��鵵�� 'classes.jar' ��:
       jar cvfm classes.jar mymanifest -C foo/

ժ��<jar����İ����ĵ�>







javac
javac rrr.java
javac -classpath rr.jar;rrr.jar rrrr.java
javac -cp rr.jar;rrr.jar rrrr.java




