#	����
+	ȫ����ջ��full-stack����Ӧ�ó�����
+	���Ʒ�ת(IOC)��������ע�뵽���󣬶����Ǵ�����Ѱ����������
+	����������(AOP)����Ӧ�õ�ҵ���߼���ϵͳ�ķ�����뿪��
+	MVC���
+	�������
+	��Ԫ����

#	IoC����	Bean
+	������ʽ
	+	����XML�ļ�
  		
      id��Bean �����ơ� �� IOC �����б�����Ψһ�ġ��� id û��ָ����Spring �Զ���Ȩ�޶���������Ϊ Bean �����֡�id ����ָ��������֣�����֮����ö��š��ֺš���ո�ָ�
  		
      <bean id="helloWorld" class="com.spring.helloworld.HelloWorld">
        <!-- Ϊ���Ը�ֵ -->
        <property name="user" value="Jerry"></property>
    	</bean>
      
	+	����ע��
		+	���ɨ�裨component scanning����Spring�ܹ���classpath���Զ�ɨ�裬����ʵ���������ض�ע�������� 
      
      @Component:����ע�⣬��ʶ��һ����Spring����������
      @Resposity:��ʶ�־ò������
      @Service:��ʶ����㣨ҵ��㣩�����
      @Controller:��ʶ���ֲ������

      
      @AutowiredĬ�ϰ�����ƥ��ע��Bean;
      @Resource������ƥ��ע��Bean;
      @Inject��@Autowiredһ��������ע��Bean�ģ�ֻ������û��required���ԡ�

      
  	+	Springͨ��@Autowiredע��ʵ��Bean������ע�� 
  		
      //1.����ͨ��ע��ķ�ʽ����bean

      @Component 
      @Scope("prototype") //��̬��Bean
      public class Student {
      
      }

      
      @Scope(��prototype��)   
      @Lazy(true)   
      @Component(��userDao��)   
      public class UserDao {   
          ����   
          // �������ó�ʼ������   
          @PostConstruct  
          public void myInit() {   
      
          }   
      
          // �����������ٷ���   
          @PreDestroy  
          public void myDestroy() {   
          }   
      }
      
      //2.ͨ��@Autowireע��
      
      public class Use {
      
          @Autowired
          @Qualifier("car")
          private Car car;
      
          @Resource
          private  UserDao userDao; 
          ....
          public String toString(){
              return car.toString();
          }
      
      }

	+	����java����


+	��ȡBeanʵ��
	+	IOC ����ʵ��:BeanFactory��ApplicationContext
	
  +	BeanFactory��ͨ��������������̬��������&ʵ������������
  
  		public static void main(String[] args) {  
          //ʵ����BeanFactory  
          BeanFactory factory = new BeanFactory();  
          //���ó�ʼ������������xml·��  
          factory.init("spring.xml");  
          //ͨ��bean id ��ȡ����  
          Car car = (CourseService) factory.getBean("car");  
          System.out.print(car);   
      }  

	+	ApplicationContext
  		
      //�� IOC �����л�ȡ Bean ���� ApplicationContext �� getBean() ����
      //ClassPathXmlApplicationContext:����·���¼��������ļ�
			//FileSystemXmlApplicationContext:���ļ�ϵͳ�м��������ļ�

+	����ע��ķ�ʽ
	+	����ע��:setter����
  		<bean id="helloWorld2" class="com.spring.helloworld.HelloWorld">
        <!-- Ϊ���Ը�ֵ -->
        <!-- ͨ������ע��: ͨ�� setter ����ע������ֵ -->
        <property name="user" value="Tom"></property>
    	</bean>
      
	+	������ע��
  		//������ƥ�����
      <bean id="car" class="com.spring.helloworld.Car">
        <constructor-arg value="KUGA" index="0"></constructor-arg>
        <constructor-arg value="ChangAnFord" index="1"></constructor-arg>
        <constructor-arg value="250000" index="2"></constructor-arg>
      </bean>
      
      //������ƥ�����
      <bean id="car" class="com.spring.helloworld.Car">
        <constructor-arg value="KUGA" type="java.util.String"></constructor-arg>
        <constructor-arg value="ChangAnFord" type="string"></constructor-arg>
        <constructor-arg value="250000" type="float"></constructor-arg>
      </bean>

+	����������Bean
	+	ͨ�� <ref>Ԫ�ػ� ref ����Ϊ Bean �����Ի���������ָ���� Bean ������.

      <bean id="dao5" class="com.spring.ref.Dao"></bean>
      
      <bean id="service" class="com.spring.ref.Service">
          <!-- ͨ�� ref ����ֵָ����ǰ����ָ����һ�� bean! -->
          <property name="dao" ref="dao5"></property>
      </bean>
      <bean id="action" class="com.spring.ref.Action">
          <property name="service" ref="service2"></property>
          <!-- ���ü�������(�˽�) -->
          <property name="service.dao.dataSource" value="DBCP2"></property>
      </bean>

+	�ڲ� Bean
	+	Bean ʵ��������һ���ض�������ʹ��,����Ҫ�����κ� id �� name ����
  
      <bean id="service2" class="com.spring.ref.Service">
          <property name="dao">
              <!-- �ڲ� bean, �����������ڲ������. ���ܱ��ⲿ�� bean ������, Ҳû�б�Ҫ���� id ���� -->
              <bean class="com.spring.ref.Dao">
                  <property name="dataSource" value="c3p0"></property>
              </bean>
          </property>
      </bean>


+	null ֵ
	+	����ʹ��ר�õ� <null/> Ԫ�ر�ǩΪ Bean ���ַ����������������͵�����ע�� null ֵ
  
      <bean id="dao2" class="com.spring.ref.Dao">
        <!-- Ϊ Dao �� dataSource ���Ը�ֵΪ null, ��ĳһ�� bean ������ֵ���� null, ʹ��ʱ��ҪΪ������Ϊ null(�˽�) -->
        <property name="dataSource"><null/></property>
      </bean>

+	��������
	+	ͨ��һ�����õ� xml ��ǩ(����: <list>, <set> �� <map>) �����ü�������

    <bean id="user" class="com.spring.helloworld.User">
        <property name="userName" value="Jack"></property>
        <property name="cars">
            <!-- ʹ�� list Ԫ����װ�伯������ -->
            <list>
                <ref bean="car"/>
                <ref bean="car2"/>
            </list>
        </property>
    </bean>

    <!-- �����������͵� bean -->
    <util:list id="cars">
        <ref bean="car"/>
        <ref bean="car2"/>
    </util:list>

    <bean id="user2" class="com.spring.helloworld.User">
        <property name="userName" value="Rose"></property>
        <!-- �����ⲿ������ list -->
        <property name="cars" ref="cars"></property>
    </bean>

+	p �����ռ�

    <bean id="user3" class="com.spring.helloworld.User"
          p:cars-ref="cars" p:userName="Titannic">
    </bean>

+	bean ֮��Ĺ�ϵ
	+	�̳У�parent
    <bean id="user" class="com.spring.helloworld.User">
        <property name="userName" value="Jack"></property>
        <property name="cars">
            <!-- ʹ�� list Ԫ����װ�伯������ -->
            <list>
                <ref bean="car"/>
                <ref bean="car2"/>
            </list>
        </property>
    </bean>
    
    <!-- bean ֮��ʹ�� parent ����ɼ̳� --> 
    <bean id="user4" parent="user" p:userName="Bob"></bean>
    
    <bean id="user6" parent="user" p:userName="ά������"></bean>

    
  +	������depends-on��ǰ��������Bean���ڱ�Beanʵ����֮ǰ������
    <bean id="user5" parent="user" p:userName="Backham" depends-on="user6"></bean>

    
	+	������ref
    <bean id="userDao" class="com.spring.ref.UserDao">
    </bean>

    <bean id="userService" class="com.spring.ref.UserService">
        <property name="userDao" ref="userDao">
        </property>  
    </bean>

    <bean id="userAction" class="com.spring.ref.UserAction">
        <property name="userService" ref="userService">
        </property>
    </bean>

+	bean ��������singleton��prototype
    <bean id="helloWorld" 
        class="com.spring.helloworld.HelloWorld" 
        scope="singleton"
        init-method="init"
        destroy-method="destroy">
        <property name="userName" value="atguigu"></property>
    </bean>
    
    singleton	��SpringIOC�����н�����һ��Beanʵ����Bean�Ե����ķ�ʽ����
    prototype	ÿ�ε���getBean()ʱ���᷵��һ���µ�ʵ��
    request	ÿ��HTTP���󶼻ᴴ��һ���µ�Bean�����������������WebApplicationContext����
    session	ͬһ��HTTP session����һ��Bean����ͬ��HTTP sessionʹ�ò�ͬ��Bean�����������������WebApplicationContext����



















