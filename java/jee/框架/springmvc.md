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

#	������Controller����Java�ࣩ
		public class CeshiController extends AbstractController {
		    @Override
		    protected ModelAndView handleRequestInternal(HttpServletRequest request,HttpServletResponse response) throws Exception {
        		System.out.println(request.getRequestURI());  // ��ȡController�����ƣ�����ַ
        		return new ModelAndView("index");  // �߼���
    		}
		}

#	DispatcherServlet�������ķַ�����web.xml
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


#	�༭ JSP ҳ�棬������ʾ

#	���� Controller ������ ViewResolver��action-servlet.xml
		<?xml version="1.0" encoding="UTF-8"?>
		<beans xmlns="http://www.springframework.org/schema/beans		"
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










































