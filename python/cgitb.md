import cgitb


cgitb.enable(display=1, logdir=None, context=5, format="html")
    display 1���������������0�� ������ 
    logdir ����еĻ���д����Ŀ¼��
    context ��ʾ���������Χ�Ĵ�������
    format �Ƿ���ʾΪHTML������'html'֮�������ֵ��������ʾΪ���ı�,text
    ...cgitb.enable(logdir=os.getcwd(), format='text')

cgitb.handle(info=None)
info Ӧ���Ǻ����쳣���͡��쳣ֵ��traceback�������Ԫ�飬������ͬsys.exc_info()���ص�������
������ṩinfo�����sys.exc_info�л�ȡ��