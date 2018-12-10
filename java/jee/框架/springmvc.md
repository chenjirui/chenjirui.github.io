Request������
��> DispatcherServlet�����ķַ����� 
��> HandlerMapping��������ӳ�䣩 
��> Controller���������� 
��> ModelAndView��ģ�ͺ���ͼ�� 
��> ViewResolver����ͼ�������� 
��> View����ͼ�� 
Response����Ӧ��
--------------------- 

DispatcherServlet��HandlerMapping��ViewResolver ֻ��Ҫ��XML�ļ�������

#   ������Controller����Java�ࣩ
        public class CeshiController extends AbstractController {
            @Override
            protected ModelAndView handleRequestInternal(HttpServletRequest request,HttpServletResponse response) throws Exception {
                System.out.println(request.getRequestURI());  // ��ȡController�����ƣ�����ַ
                return new ModelAndView("index");  // �߼���
            }
        }

#   DispatcherServlet�������ķַ�����web.xml
        <web-app version="2.5" xmlns="http://java.sun.com/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd">

            <!-- ���� DispatcherServlet�������к�׺Ϊaction��url���й��� -->
            <servlet>
                <servlet-name>action</servlet-name>
                <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
            </servlet>
            <servlet-mapping>
                <servlet-name>action</servlet-name>
                <url-pattern>*.action</url-pattern>
            </servlet-mapping>
        </web-app>


#   �༭ JSP ҳ�棬������ʾ

#   ���� Controller ������ ViewResolver��action-servlet.xml
        <?xml version="1.0" encoding="UTF-8"?>
        <beans xmlns="http://www.springframework.org/schema/beans       "
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
            xsi:schemaLocation="http://www.springframework.org/schema/beans
                        http://www.springframework.org/schema/beans/spring-beans-3.2.xsd">

            <!-- ���� Controller -->
            <bean name="/home.action" class="spring.mvc.controller.CeshiController" />

            <!-- �ڲ���Դ��ͼ��������ǰ׺ + �߼��� + ��׺ -->
            <bean id="internalResourceViewResolver" class="org.springframework.web.servlet.view.InternalResourceViewResolver">
                <property name="prefix" value="/WEB-INF/pages/"/>
                <property name="suffix" value=".jsp"/>
            </bean>
        </beans>
        *


#   RequestMapping

    @Target({ElementType.METHOD, ElementType.TYPE})         //�����ڷ��������������ʹ��
    @Retention(RetentionPolicy.RUNTIME)
    @Documented
    @Mapping
    public @interface RequestMapping {
        String name() default "";                           //�ַ���
        String[] value() default {};                        //�ַ�������
        String[] path() default {};
        RequestMethod[] method() default {};
        String[] params() default {};
        String[] headers() default {};
        String[] consumes() default {};
        String[] produces() default {};
    }

+   value,path : ������ͬ�����Ի��������������һ�����ԣ������ʡ��

      @Controller                             //Controller�ϲ����@RequestMappingע��
      public class UserController {
      
          @RequestMapping("/login")           //����URL�������Web��Ŀ¼
          public String login() {
              return "success";
          }
      }
      
      @Controller                             //Controller���@RequestMappingע��
      @RequestMapping("/user")                //���ע���������Web��Ŀ¼
      public class UserController {
      
          @RequestMapping("/login")           //�����ϵ�����������ϵ�·��
          public String login() {
              return "success";
          }
      }

+   method:�����������������ĺ�������
      
      @RequestMapping(path = "/login", method=RequestMethod.GET)
      
      @RequestMapping(path = "/login", method={RequestMethod.POST,RequestMethod.GET})
      
+   params:���������������ʵ�ֽ�һ���Ĺ�������

      @RequestMapping(path = "/user/login", params={"username=aaa","password=123456"})
      public String login() {
          return "success";
      }
      //����������/user/login?username=aaa&password=123456
      //����������HTTP 404

+   headers:��������ͷ

      @RequestMapping(path = "/user/login", headers="Host=localhost:8080")
      public String login() {
          return "success";
      }
      //��ʾֻ���ձ�������������

+   ��ռλ����URL��{id} --> @PathVariable("id")

      @RequestMapping(value="/user/{id}", method=RequestMethod.GET)
      public String show(@PathVariable("id") Integer id) {
          return "success";
      }




























