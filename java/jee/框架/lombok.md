[Lombok ����ƪ�͹���](https://zhuanlan.zhihu.com/p/32779910)
<dependency>
    <groupId>org.projectlombok</groupId>
    <artifactId>lombok</artifactId>
    <version>1.16.18</version>
    <scope>provided</scope>
</dependency>


+  @Data��ע�����࣬�ṩ���������Ե� get �� set �Լ�equals��canEqual��hashCode��toString ����

+  @Setter��ע�������� ��Ϊ���������ṩ set ������ע�����࣬Ϊ�������е������ṩ set ����

+  @Getter��

+  @Log4j��ע���� �� �ϣ�Ϊ���ṩһ�� ������Ϊ log �� log4j ��־�����ṩĬ�Ϲ��췽����

+  @AllArgsConstructor��ע���� �� �ϣ�Ϊ���ṩһ��ȫ�εĹ��췽�����������ע������в��ṩĬ�Ϲ��췽����

+  @NoArgsConstructor��ע���� �� �ϣ�Ϊ���ṩһ���޲εĹ��췽����

+  @EqualsAndHashCode��ע���� �� ��, �������� equals��canEqual��hashCode ������

+  @NonNull��ע���� ���� �ϣ����Զ�����һ�����ڴ˲����ķǿռ�飬�������Ϊ�գ����׳�һ����ָ���쳣��Ҳ����һ��Ĭ�ϵ��޲ι��췽����

+  @Cleanup�����ע������ ���� ǰ�棬���Ա�֤�˱����������Դ�ᱻ�Զ��رգ�Ĭ���ǵ�����Դ�� close() �������������Դ�������رշ�������ʹ�� @Cleanup(��methodName��) ��ָ��Ҫ���õķ�����Ҳ������Ĭ�ϵĹ��췽��

+  @ToString�����ע������ �� �ϣ������������в����� toString ��������������Ĭ�ϵĹ��췽����

+  @RequiredArgsConstructor�����ע������ �� �ϣ�ʹ���������д��� @NonNull ע��Ļ��ߴ��� final ���εĳ�Ա�������ɶ�Ӧ�Ĺ��췽����

+  @Value�����ע������ �� �ϣ������ɺ����в����Ĺ��췽����get ���������⻹�ṩ��equals��hashCode��toString ������

+  @SneakyThrows�����ע������ ���� �ϣ����Խ������еĴ����� try-catch �����������������쳣���� catch ���� Lombok.sneakyThrow(e) ���쳣�׳�������ʹ�� @SneakyThrows(Exception.class) ����ʽָ���׳������쳣��Ҳ������Ĭ�ϵĹ��췽����

+  @Synchronized�����ע������ �෽�� ���� ʵ������ �ϣ�Ч���� synchronized �ؼ�����ͬ����������������ͬ�������෽����ʵ��������synchronized �ؼ��ֵ�������ֱ������ class ����� this ���󣬶� @Synchronized ��������ֱ��� ˽�о�̬ final ���� lock �� ˽�� final ���� lock����Ȼ��Ҳ�����Լ�ָ�������󣬴���Ҳ�ṩĬ�ϵĹ��췽����