https://www.jianshu.com/p/0a83ccb4c388


+	export:���ڶ��������ģ�飨һ���ļ��������Ϊһ��ģ�飩�����Ľӿڡ�

+	import:������һ��ģ���м�����һ������export�ӿڵ�ģ�顣

      //a.js
      var name="LXN";
      var echo=function(value){
        console.log(value)
      }
      export {name, echo}
      //ͨ��������������name��echo ������������export���
      //���ϵ�export {name}����д��export name
      
      //b.js
      //ͨ��import��ȡa.js�ļ����ڲ�����
      import {name, echo} from "./a.js"
      console.log(name)  //LXN
      echo(name) //LXN
      
+	export default:Ĭ�����������Ҫ֪����Ҫ����ģ��ı�����

      //a.js
      var name="LXN";
      export default name  
      //name���ܼӴ����ţ�ע��������÷�����
      //һ���ļ�ֻ����һ��export default
      //�˴��൱��Ϊname����ֵ��LXN������һ��ϵͳĬ�ϵı�����default
      //export default����ʵ����ֻ�����һ������default�ı��������������治�ܸ�����������䣬��export��Ҫ�������������ߴ�������Ϊ�����
      
      //b.js
      //��ʵ��a.js�ļ���export default���һ������default�ı�����Ȼ��ϵͳ����Ϊ��ȡ�������֣����Կ���Ϊimport��ģ�����κα��������Ҳ���Ҫ�ô����Ű���
      import any from "./a.js"
      import anyname from "./a.js"
      console.log(any,anyname) //LXN,LXN















