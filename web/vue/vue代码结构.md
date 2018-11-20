
#   ����ṹ

        |-- src                              // Դ��Ŀ¼
        |   |-- components                   // vue�������
        |   |-- router                       // vue��·�ɹ���
        |   |-- App.vue                      // ҳ������ļ�
        |   |-- main.js                      // ��������ļ������ظ��ֹ������
        |-- static                           // ��̬�ļ�������һЩͼƬ��json���ݵ�
        |-- index.html                       // ���ʵ�ҳ��
.

        request
           |
           |
           |                    App.vue
           ��                  �L
       index.html  �� (main.js)   
           |                  �Irouter/index.js    ����   components + router
           |
           |       
           ��
       ��ҳ��Ӧ��

+   index.html�����η��ʵ�ҳ�棬�ṩע���\<div id="app">
+   App.vue����ҳ��ܣ��ṩ\<router-view>���͵���\<router-link>��
+   router/index.js��·���ļ���url-->components
+   src/main.js����������ļ����������ظ�ʵ����ע��·�ɣ����ظ��ֹ������




#   index.html �������

    <!DOCTYPE html>
    <html>
      <head>
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width,initial-scale=1.0">
        <title>subscription</title>
      </head>
      <body>
        <div id="app"></div>
        <!-- built files will be auto injected -->
      </body>
    </html>

#   src/main.js  �������
    import Vue from 'vue';
    import App from './App.vue';
    import router from './router/index.js';
    
    //�����͹��ظ�ʵ����ͨ�� router ���ò���ע��·�ɣ��Ӷ�������Ӧ�ö���·�ɹ���
    new Vue({
      el: "#app",
      router,
      components: {App},
      template: '<App/>',
    });
    
#   src/app.vue  ҳ�����
    <template>
      <div id="app">
        <img src="./assets/logo.png">
        <router-view></router-view>
      </div>
    </template>
    <script>
    export default {
      name: 'app'
    }
    </script>
    <style>
    #app {
      font-family: 'Avenir', Helvetica, Arial, sans-serif;
      -webkit-font-smoothing: antialiased;
      -moz-osx-font-smoothing: grayscale;
      text-align: center;
      color: #2c3e50;
      margin-top: 60px;
    }
    </style>
    
    
    <template></template> ��ǩ���������ݣ�����ģ���HTMLDom�ṹ 
    <script></script>     ��ǩ������js���ݣ������������дһЩҳ���js���߼����롣 
    <style></style>       ��ǩ������css���ݣ�ҳ����Ҫ��CSS��ʽ��

#   src/router/index.js ��·��
    import Vue from 'vue'
    import Router from 'vue-router'
    import Hello from '@/components/Hello'
    
    Vue.use(Router)
    
    export default new Router({
      routes: [//����·��
        {
          path: '/',        //����·��
          name: 'Hello',    //·������
          component: Hello  //·����Ҫ��������շ�ʽ������
        },
        {
          path:'*', redirect:'/'
        }
      ]









































