
Node.js �ǵ����̵��߳�Ӧ�ó��򣬵�����Ϊ V8 �����ṩ���첽ִ�лص��ӿ�
Node.js ���е��첽 I/O ���������ʱ���ᷢ��һ���¼����¼����С�
Node.js ����������󶼻�ַ��¼���
һ�� net.Server �������ÿ����������ʱ����һ���¼�
һ�� fs.readStream ��������ļ����򿪵�ʱ�򴥷�һ���¼�
������Щ�����¼��Ķ����� events.EventEmitter ��ʵ����



#	events

    //���� events ģ��
    var events = require('events');
    //���� eventEmitter ����
    var eventEmitter = new events.EventEmitter();
    //���¼����¼��Ĵ������
    var eventHandler = function connected() {
    	......
    }
    eventEmitter.on('eventName', eventHandler);
    //�����¼�
    eventEmitter.emit('eventName');
    //�����¼�
    eventEmitter.emit('eventName');
    
    
    var events = require('events'); 
	var emitter = new events.EventEmitter(); 
	emitter.on('someEvent', function(arg1, arg2) { 
	    console.log('listener1', arg1, arg2); 
	}); 
	emitter.on('someEvent', function(arg1, arg2) { 
	    console.log('listener2', arg1, arg2); 
	}); 
	emitter.emit('someEvent', 'arg1 ����', 'arg2 ����'); 

addListener(event, listener)
Ϊָ���¼����һ���������������������β����

on(event, listener)
Ϊָ���¼�ע��һ��������������һ���ַ��� event ��һ���ص�������

once(event, listener)
Ϊָ���¼�ע��һ�����μ��������� ���������ֻ�ᴥ��һ�Σ����������̽���ü�������

removeListener(event, listener)
�Ƴ�ָ���¼���ĳ���������������������Ǹ��¼��Ѿ�ע����ļ�������

removeAllListeners([event])
�Ƴ������¼������м������� ���ָ���¼������Ƴ�ָ���¼������м�������

setMaxListeners(n)
Ĭ������£� EventEmitters �������ӵļ��������� 10 ���ͻ����������Ϣ�� setMaxListeners ����������߼�������Ĭ�����Ƶ�������

listeners(event)
����ָ���¼��ļ��������顣

emit(event, [arg1], [arg2], [...])
��������˳��ִ��ÿ��������������¼���ע��������� true�����򷵻� false��



�෽��
listenerCount(emitter, event)
����ָ���¼��ļ�����������
events.EventEmitter.listenerCount(emitter, eventName) //�ѷ��������Ƽ�
events.emitter.listenerCount(eventName) //�Ƽ�



�¼�
newListener
	event - �ַ������¼�����
	listener - �����¼�����
	���¼�������¼�����ʱ��������
removeListener
	event - �ַ������¼�����
	listener - �����¼�����
	��ָ��������������ɾ��һ������������Ҫע����ǣ��˲�������ı䴦�ڱ�ɾ������֮�����Щ��������������

error
	�쳣���� error �¼������û����Ӧ�ļ�������Node.js ����������쳣���˳��������������Ϣ��
	emitter.emit('error'); 
    --> Error: Uncaught, unspecified 'error' event. 
























