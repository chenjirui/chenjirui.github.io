#   ��װ����
npm install vue-router --save-dev
    
#   ��������    
    
    <!-- ʹ�� router-link ���������. -->
    <!-- ͨ������ `to` ����ָ������. -->
    <!-- <router-link> Ĭ�ϻᱻ��Ⱦ��һ�� `<a>` ��ǩ -->
    <router-link to="/bar">Go to Bar</router-link>
    <!-- ·�ɳ��� -->
    <!-- ·��ƥ�䵽���������Ⱦ������ -->
    <router-view></router-view>

    // 2������·��
    // ÿ��·��Ӧ��ӳ��һ�����
    // ˭�ȶ���ģ�˭�����ȼ�����ߡ�
    import Vue from 'vue'
    import Router from 'vue-router'
    import Hello from '@/components/Hello'
    Vue.use(Router);
    const routes = [
      { 
        path: '/foo', component: Foo 
      },
      {
        path: '/menu/:menu', component: submenu, 
        children: [                                     //Ƕ��
          {path: '/home/home', component: homehome}     //�� / ��ͷ��Ƕ��·���ᱻ������·��
        ]
      },
      {
        path:'*', redirect:'/'                          //�ض���*
      }
    ]

    // 3������ router ʵ����
    const router = new VueRouter({
      routes // (��д) �൱�� routes: routes
    })
    
    // 4�������͹��ظ�ʵ����
    new Vue({
      el: "#app",
      router,
      components: {App},
      template: '<App/>',
    });

#   ����·��

    routes: [
      {
        path: '/user/:userId',
        name: 'user',
        component: User
      }
    ]
    
    // ����/user/123
    <router-link :to="{ name: 'user', params: { userId: 123 }}">User</router-link>
    router.push({ name: 'user', params: { userId: 123 }})

    
#   ����

+   ͨ�� this.$router ����·����

        this.$router.go(-1);            //����
        this.$router.push('/');
        
        router.go(n)
        // �� history ��¼����ǰ���ߺ��˶��ٲ�
        // ���� window.history.go(n)
        
        router.push(location, onComplete?, onAbort?)
        // �������� history ջ���һ���µļ�¼���������������˰�ťʱ�����ص�֮ǰ�� URL��
        // ���ڵ��<router-link :to="...">
        router.push('/user')
        router.push({ path: '/user' })        
        router.push({ name: 'user', params: { userId }})         // -> /user/123
        router.push({ path: `/user/${userId}` })                 // -> /user/123
        router.push({ path: '/user', query: { id: '123' }})      // -> /user?id=123
        
        router.replace(location, onComplete?, onAbort?)
        // ������ history ����¼�¼�������滻����ǰ�� history ��¼��
        // <router-link :to="..." replace>

+   ͨ�� this.$route  ���ʵ�ǰ·��

        this.$route.params.username;    //��ѯ����


#   ��̬·�� :id
    
    routes: [
      // ��̬·������ ��ð�ſ�ͷ
      { path: '/user/:id', component: User }
    ]

    //��ѯ
    $route.params.id

#   �����������Ӧ·�ɲ����ı仯��watch��beforeRouteUpdate

    const User = {
      template: '...',
      watch: {
        '$route' (to, from) {
          // ��·�ɱ仯������Ӧ...
        }
      }
    }
    
    //����ʹ�� 2.2 ������� beforeRouteUpdate ������
    const User = {
      template: '...',
      beforeRouteUpdate (to, from, next) {
        // react to route changes...
        // don't forget to call next()
      }
    }


#   �ض��������
    new VueRouter({
      routes: [
        { path: '/a', redirect: '/b' },             // �� /a �ض��� /b
        { path: '/c', redirect: { name: 'foo' }},   // �ض����Ŀ����һ��������·��
        { path: '/d', redirect: to => { ... }},     // ��̬�����ض���Ŀ�꣬����Ŀ��·��('/d')��Ϊ������return �ض���� �ַ���·��/·������
        { path: '/e', component: E, alias: '/f' },  // /e �ı����� /f�����û����� /f ʱ��URL �ᱣ��Ϊ /f������·��ƥ����Ϊ /e�������û����� /e ���������ɵؽ� UI �ṹӳ�䵽����� URL
     ]
    });












