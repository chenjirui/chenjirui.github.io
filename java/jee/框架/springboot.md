#	ʹ��idea����springboot��Ŀ
+	New > Project > Spring Initializr > Web

#	��Ŀ�ṹ
+	src
	+	main
  	+	java/com/ruiaa/BootdemoApplication.java		��һ������main()�������࣬��������Ӧ�ó��򣨹ؼ���
  +	resources
  	+	static
    +	templates
    +	application.properties		��һ���յ�properties�ļ����������������
  +	pom.xml											��Maven����˵���ļ�

#	pom.xml

#	������Ŀ
+	Application.java��main����
+	�������� mvn spring-boot:run
+	jar������� mvn package

#	��̬��Դ����
src/main/resources/META-INF/resources
src/main/resources/resources
src/main/resources/static
src/main/resources/public

#	Starter
һ����������� Maven POM��
����Լ����spring-boot-starter-XYZ
+	spring-boot-starter-web ���ڹ��� RESTful Web ������ʹ�� Spring MVC �� Tomcat ��ΪǶ��ʽӦ�ó�������
+	spring-boot-starter-jersey �� spring-boot-starter-web ��һ���������ʹ�� Apache Jersey ������ Spring MVC
+	spring-boot-starter-jdbc ���ڽ��� JDBC ���ӳء������� Tomcat �� JDBC ���ӳ�ʵ�֡�



#	Ƕ��ʽ Tomcat ����

#	ע��
+	��������@SpringBootApplication = (Ĭ������)@Configuration + @EnableAutoConfiguration + @ComponentScan

+	��������
	+	�ࣺ@RestController = @Controller + @ResponseBody
  	+	@ResponseBody:��ע��ָʾ��������ֵ��Ӧ�󶨵�Web��Ӧ����
    +	@RestController����ʾ�û�������һ��֧��REST�Ŀ�����
  +	@RequestMapping:��һ���������������ַӳ���ע�⣬��������򷽷��ϡ�
  	+	�������ϣ���ʾ���е�������Ӧ����ķ��������Ըõ�ַ��Ϊ��·����
    +	���ݷ����Ĳ�ͬ����������GetMapping��PostMapping��PutMapping��DeleteMapping��PatchMapping���档

#	�Զ������ԣ�application.properties
+	com.ruiaa.propertyName=valve
+	ͨ��@Value("${������}")ע�������ض�Ӧ����������

		@Value("${com.neo.title}")
		private String title;

#	Beans������ע��
+	ʹ�� @ComponentScan ע������beans������� @Autowired ������ע��
+	��Ӧ�õ�main��ŵ��������ϲ㣬��root package������Ӧ������� @Component , @Service , @Repository , @Controller �ȣ������Զ�ע���Spring Beans��

    @Service
    public class DatabaseAccountService implements AccountService {
      private final RiskAssessor riskAssessor;
      
      //ʹ�ù�����ע���ȡһ����Ҫ��RiskAssessor bean
      @Autowired
      public DatabaseAccountService(RiskAssessor riskAssessor) {
        this.riskAssessor = riskAssessor;
      }
    
    }
    
    @Service���ڱ�עҵ������
    @Controller���ڱ�ע���Ʋ����
    @Repository���ڱ�ע���ݷ����������DAO���
    @Component��ָ�������������ù����ʱ�򣬿�ʹ�����ע����б�ע��


#	MVC
+	@RequestMapping(value = "/hello", method = RequestMethod.GET)
+	@ResponseBody ���ؽ��ֱ��д��Http Response Body�� �����ʽ��HttpMessageConverter������SpringMVC��Ĭ��Ϊjson���Զ��� java bean ����ת�� json ��
+	@RequestParam("paramName") ֱ���Զ�װ�ز���,���HTTP������û�иò���ʱSpring MVC�ͻᱨ��
+	@RequestParam(value = "paramName", defaultValue = "")
+	@PathVariable ��װ��URL·���е�ֵ��Ϊ����
+	@RestController = @Controller + @ResponseBody����@RestController�����൱��ÿ����������@RequestMapping�ģ��Զ������� @ResponseBody ע��
+	 response.sendRedirect("some-url"); �ض���

		@Controller
		public class HelloController {

    		@Autowired
    		private HelloService helloService;
    
    		@RequestMapping(value = "/hello", method = RequestMethod.GET)
    		public void sayHello(HttpServletRequest request, HttpServletResponse response) throws IOException {
        		String name = request.getParameter("name");
        		String msg = helloService.hello(name);
        		response.getWriter().println(msg);
    		}
        
        @RequestMapping(value = "/hello2/param", method = RequestMethod.GET)
        @ResponseBody
        public String sayHelloByParam(@RequestParam("name") String name) {
            return helloService.hello(name);
        }
    
        // URLʾ����  http://localhost:8080/hello2/path/jjj
        @RequestMapping(value = "/hello2/path/{name}", method = RequestMethod.GET)
        @ResponseBody
        public String sayHelloByPath(@PathVariable("name") String name) {
            return helloService.hello(name);
        }

		}

{
    "code": 200,
    "msg": "success",
    "exception": null,
    "data": "ppateeeeeeeeeeehbehrqwrfwqcvwqcp"
}
+	�Զ��巵��ֵת���� HttpMessageConverter
    
@EnableWebMvc
public class HelloWebMvcConfigurer extends WebMvcConfigurerAdapter {

    public static final ObjectMapper createObjectMapper() {
        ObjectMapper objectMapper = new ObjectMapper();
        objectMapper.setPropertyNamingStrategy(PropertyNamingStrategy.LOWER_CAMEL_CASE);
        // ����Ϊ��ʱ������ null, �մ����ռ��ϣ��ն��󣩣����������л���
        objectMapper.setSerializationInclusion(JsonInclude.Include.NON_EMPTY);
        // Date ���������л�ʱ����ʽΪ yyyy��MM��dd�� HHʱmm��ss�� ��
        objectMapper.setDateFormat(new SimpleDateFormat("yyyy��MM��dd�� HHʱmm��ss��"));
        objectMapper.configure(JsonParser.Feature.ALLOW_COMMENTS, true);
        objectMapper.configure(JsonParser.Feature.ALLOW_UNQUOTED_FIELD_NAMES, true);
        objectMapper.configure(JsonParser.Feature.ALLOW_SINGLE_QUOTES, true);
        objectMapper.configure(JsonParser.Feature.ALLOW_UNQUOTED_CONTROL_CHARS, true);
        // json�������õĸ�ʽ�����
        objectMapper.configure(SerializationFeature.INDENT_OUTPUT, true);
        // ������Ϊ�ջ�������ʱ���������л���
        objectMapper.configure(SerializationFeature.FAIL_ON_EMPTY_BEANS, false);
        // δ֪�����Բ����뷴���л���
        objectMapper.configure(DeserializationFeature.FAIL_ON_UNKNOWN_PROPERTIES, false);       
        return objectMapper;
    }

    @Override
    public void extendMessageConverters(List<HttpMessageConverter<?>> converters) {
        ObjectMapper objectMapper = createObjectMapper();
        MappingJackson2HttpMessageConverter convertor = new MappingJackson2HttpMessageConverter(objectMapper);
        //Spring MVC �п����кܶ� HttpMessageConverter ��������ʱ�Ǵ� converters �б��б�����ֱ���ҵ���һ�� HttpMessageConverter �����ܴ���ǰ��HTTP����Ϊֹ��
        //0Ϊ��һλ���������Ȩ
        converters.add(0, convertor);
    }
}

//�� @Import ע����������������
@Import(HelloWebMvcConfigurer.class)
@SpringBootApplication
public class HelloWebApp {

    public static void main(String[] args) {
        SpringApplication.run(HelloWebApp.class, args);
    }


}

#	MVC����
+	Spring Bootͨ��WebMvcAutoConfiguration���ṩһЩĬ������
+	ʹ��EnableWebMvcע�⣺ͬһ��Ӧ���У�ֻ����һ����EnableWebMvcע�����

    @Configuration
    @EnableWebMvc
    public class MyWebMvcConfigurer implements WebMvcConfigurer {
    
    }
    
    configurePathMatch	����HandlerMapping·��ƥ�����
    configureContentNegotiation	����·����������������ת������ز�������.pdf��β�����������PDF���ͻ���������
    configureAsyncSupport	�����첽��������ز���
    configureDefaultServletHandling	�����Ƿ���Ҫ���¹��ܣ����һ������û�б��κ�Handler�������Ƿ�ʹ��DefaultServletHttpRequestHandler�����д���
    addFormatters	���Ӷ����Converter��Formatter
    addInterceptors	����������
    addResourceHandlers	���Ӵ���̬��Դ��Handler
    addCorsMappings	���ÿ���������ز���
    addViewControllers	ʹ�������Controller������ָ����URL����;
    configureViewResolvers	���ý�Controller���ص���ͼ����ת������ͼ����ͼ������; �Ա������ͼ��Ⱦ
    addArgumentResolvers	���֧�ָ��Ի�����Controller�ķ����������͵�Resolver��
    addReturnValueHandlers	���֧�ָ��Ի�����Controller�����������͵Ĵ�������
    configureMessageConverters	������Ϣת������
    extendMessageConverters	��չ��Ϣת����
    configureHandlerExceptionResolvers	�����쳣������
    extendHandlerExceptionResolvers	��չ�쳣������


#	Hibernate  ��  JPA��Java Persistence API��Java�־ò�API  <-- Spring Data JPA	
[Spring Data JPA](https://www.jianshu.com/p/be542258802e)
+	1.��pom.xml������spring-boot-starter-data-jpa������ application�����ļ����������ݿ����ӡ�

    <!-- JPA -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-data-jpa</artifactId>
    </dependency>
    <dependency>
        <groupId>mysql</groupId>
        <artifactId>mysql-connector-java</artifactId>
    </dependency>
		
    //��application.properties�����ļ����������ݿ����Ӽ�JPA����
    spring.datasource.driverClassName = com.mysql.cj.jdbc.Driver
    spring.datasource.url = jdbc:mysql://127.0.0.1:3306/db?serverTimezone=UTC&characterEncoding=utf-8
    spring.datasource.username = root
    spring.datasource.password = 

    //ÿ�γ�������ʱ�����ݿ��Ĵ�����ԣ�create��ɾ���ϴκ󴴽���create-drop������ʱ�����˳�ʱɾ����update����һ�η���ʱ�����Ժ���£�validate���������±��������ֵ
    spring.jpa.hibernate.ddl-auto = update
    spring.jpa.show-sql = true

+	2.��д Entity �࣬���� JPA �淶������ʵ�塣


@Entity(name = "t_user")		// �������ݿ�����ơ�name:����
@Table(indexes = { 					// �������ݿ�������name:�������������ƣ� columnList:��������(������Ա�ʾ������������ unique=true:Ψһ����
	@Index(name = "ux_user_login_name", columnList = "loginName", unique = true), 
	@Index(name = "idx_user_age", columnList = "age,loginName"), 
})
public class User {

		//������Id����Ҫ��ע�ͣ�@Id��@GeneratedValue(strategy = GenerationType.AUTO)�Ż��Զ�����
    //����Ҫ�������ñ��ֶ����������ϼ�ע��@Column(name = "�ֶ���")
    
    //id����������
    @Id
    @GeneratedValue
    @Column(length = 20)
    private Long id;

    //�������շ�������
    //���ֶ��»�������������loginName -> login_name��
    @Column(length = 100, nullable = false)
    private String loginName;

    @Column(length = 3)
    private Integer age;

    @Column(length = 16, nullable = false)
    @Enumerated(EnumType.STRING)
    private UserStatus status = UserStatus.enable;

    @Temporal(TemporalType.TIMESTAMP)
    @Column(nullable = false)
    private Date registTime;

    public final Long getId() { return id; }

    public final void setId(Long id) { this.id = id; }
}

+	3.��д Repository �ӿڣ����� Spring Data �淶���������ݷ��ʽӿڣ�ע�⣬ֻҪ�ӿڣ�����Ҫ�κ�ʵ�֣�

//ʵ������ User, User �� ID ������ Long ���͵�
//��ʹ����ͨ�� Spring Bean һ������ @Autowired ���뼴��ʹ��
public interface UserRepository extends JpaRepository<User, Long> {

}

+	4.ʹ��ԭ��SQL��ѯ

		//SQL : src/main/java/META-INF/orm.xml 
		<?xml version="1.0" encoding="UTF-8" ?>
		<entity-mappings xmlns="http://xmlns.jcp.org/xml/ns/persistence/orm"    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"    xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/persistence/orm http://xmlns.jcp.org/xml/ns/persistence/orm_2_0.xsd"  version="2.1">
    		<named-native-query 									//��ʾ��һ����ԭ��SQL��ѯ��
    				name="User.findByAgeRange" 				//�������������������ѯ
        		result-class="com.example.User"		//�������ÿ����¼ת����User����
      		>
      		//ԭ����SQL��䣬��:��ʼ���Ǳ������������洫�����
      		<query><![CDATA[
          		select * from t_user as u
          		where u.age >= :minAge and u.age <= :maxAge
          		order by u.regist_time desc
      		]]></query>
    		</named-native-query>
		</entity-mappings>

		//�������
		public interface UserRepository extends JpaRepository<User, Long> {
    		@Query(nativeQuery = true, name = "User.findByAgeRange")
    		List<User> findByAgeRange(@Param("minAge") int minAge, @Param("maxAge") int maxAge);
		}

		//ʹ��
		userRepository.findByAgeRange(minAge, maxAge);

#	Mybatis
+	����

        <dependency>
            <groupId>org.mybatis.spring.boot</groupId>
            <artifactId>mybatis-spring-boot-starter</artifactId>
            <version>1.3.1</version>
        </dependency>

        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <scope>runtime</scope>
        </dependency>

+	�����ļ�application.yml(application.properties)

		spring:
	  datasource:
	     url: jdbc:mysql://127.0.0.1:3306/mytest?useUnicode=true&characterEncoding=utf-8
	     username: root
	     password: root
	     driver-class-name: com.mysql.jdbc.Driver
     
+	��Mysql���ݿ��д������ݱ�

+	����ʵ����

		public class User {
    		private Integer id;
    		private String name;
		    //ʡ�� get �� set ...
		}

+	����ӳ��Ĳ�����@Autowiredע��ʹ��

		@Mapper
		public interface UserMapper {
		    @Select("SELECT * FROM T_USER WHERE PHONE = #{phone}")
		    User findUserByPhone(@Param("phone") String phone);

		    @Insert("INSERT INTO T_USER(NAME, PASSWORD, PHONE) VALUES(#{name}, #{password}, #{phone})")
		    int insert(@Param("name") String name, @Param("password") String password, @Param("phone") String phone);
		}

    //ʹ��
    userMapper.insert("winterchen", "123456", "12345678910");
    User u = userMapper.findUserByPhone("12345678910");
    
    //��ɾ�Ĳ�
    @Select("SELECT * FROM T_USER WHERE PHONE = #{phone}")
    User findUserByPhone(@Param("phone") String phone);
    @Insert("INSERT INTO T_USER(NAME, PASSWORD, PHONE) VALUES(#{name}, #{password}, #{phone})")
    int insertByUser(User user);
    @Update("UPDATE T_USER SET NAME = #{name}, PASSWORD = #{password} WHERE PHONE = #{phone}")
    void update(User user);
    @Delete("DELETE FROM T_USER WHERE ID = #{id}")
    void delete(Integer id);
    
    //ʹ��Map
    @Insert("INSERT INTO T_USER(NAME, PASSWORD, PHONE) VALUES(" +
            "#{name, jdbcType=VARCHAR}, #{password, jdbcType=VARCHAR}, #{phone, jdbcType=VARCHAR})")
    int insertByMap(Map<String, Object> map);

    Map<String, Object> map = new HashMap<>();
    map.put("name","����");
    map.put("password","23423");
    map.put("phone", "13400000000");
    userMapper.insertByMap(map);

    //ʹ�ö���#{name}��#{age}�ͷֱ��Ӧ��User�����е�name��age����
    @Insert("INSERT INTO T_USER(NAME, PASSWORD, PHONE) VALUES(#{name}, #{password}, #{phone})")
    int insertByUser(User user);
    
    

+	�����������Ҫ�������ķ�������� @Transactional ע��
	+	��Applicationʹ��ע�� @EnableTransactionManagement ��������֧��	
	+	��ʹ��@Transactional��������������ڵ�Ԫ���Խ���֮����Զ��ع�

+	���ؽ���󶨣�@Results��@Result

    @Results({
            @Result(property = "name", column = "NAME"),
            @Result(property = "password", column = "PASSWORD"),
            @Result(property = "phone", column = "PHONE")
    })
    //���ֲ�ѯ
    @Select("SELECT NAME, PASSWORD, PHONE FROM T_USER")
    List<User> findAll();

+	��ҳ���PageHelper

#	filters
+	OrderedCharacterEncodingFilter��HiddenHttpMethodFilter

@Configuration
public class WebConfiguration {
    @Bean
    public RemoteIpFilter remoteIpFilter() {
        return new RemoteIpFilter();
    }
    
    @Bean
    public FilterRegistrationBean testFilterRegistration() {

        FilterRegistrationBean registration = new FilterRegistrationBean();
        registration.setFilter(new MyFilter());
        registration.addUrlPatterns("/*");
        registration.addInitParameter("paramName", "paramValue");
        registration.setName("MyFilter");
        registration.setOrder(1);
        return registration;
    }
    
    public class MyFilter implements Filter {
		@Override
		public void destroy() {
			// TODO Auto-generated method stub
		}

		@Override
		public void doFilter(ServletRequest srequest, ServletResponse sresponse, FilterChain filterChain)
				throws IOException, ServletException {
			// TODO Auto-generated method stub
			HttpServletRequest request = (HttpServletRequest) srequest;
			System.out.println("this is MyFilter,url :"+request.getRequestURI());
			filterChain.doFilter(srequest, sresponse);
		}

		@Override
		public void init(FilterConfig arg0) throws ServletException {
			// TODO Auto-generated method stub
		}
    }
}


#	@Configuration






#	����
@RunWith(SpringRunner.class)
@SpringBootTest
public class SpringbootMybatisDemo2ApplicationTests {


    @Autowired
    private UserMapper userMapper;


    @Test
    @Transactional
    public void test3(){
        userMapper.insert("����", "123456", "18600000000");

        User u = userMapper.findUserByPhone("18600000000");

        Assert.assertEquals("123456", u.getPassword());

        u.setName("����");
        u.setPassword("12312312");
        userMapper.update(u);

        u = userMapper.findUserByPhone("18600000000");

        Assert.assertEquals("12312312", u.getPassword());

        userMapper.delete(u.getId());

        u = userMapper.findUserByPhone("18600000000");

        Assert.assertEquals(null, u);
    }
}




















































