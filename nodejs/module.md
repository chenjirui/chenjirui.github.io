һ�� Node.js �ļ�����һ��ģ�飬
����ļ�������JavaScript ���롢JSON ���߱������C/C++ ��չ��
4 ��ģ�飨ԭ��ģ���3���ļ�ģ�飩


Node.js �ṩ�� exports �� require ��������
���� exports ��ģ�鹫���Ľӿڣ�
require ���ڴ��ⲿ��ȡһ��ģ��Ľӿڣ�������ȡģ��� exports ����


#	����ģ��

    //hello.js 
    //exports ����� world ��Ϊģ��ķ��ʽӿ�
    exports.world = function() {
      console.log('Hello World');
    }
    
    
    //�����װ
    module.exports = function() {
      // ...
    }
    //hello.js 
    function Hello() { 
        var name; 
        this.setName = function(thyName) { 
            name = thyName; 
        }; 
        this.sayHello = function() { 
            console.log('Hello ' + name); 
        }; 
    }; 
    module.exports = Hello;
    //main.js 
    var Hello = require('./hello'); 
    hello = new Hello(); 
    hello.setName('BYVoid'); 
    hello.sayHello(); 


#	����ģ��
	var hello = require('./hello');
	hello.world();
    //�����˵�ǰĿ¼�µ� hello.js �ļ���./ Ϊ��ǰĿ¼��node.js Ĭ�Ϻ�׺Ϊ js����






