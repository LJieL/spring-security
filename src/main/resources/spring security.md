�ֲ�
domain����entity responsity��
Service
��controller�ֳ�web��api��
web ��ҳ����ת
api�� post ��¼֮��
dto


http.csrf().disable();//���403����post�����get���ᡣ
		
//�������csrf <input type="hidden" th:name="${_csrf.parameterName}" th:value="${_csrf.token}" th:if="${_csrf}" />




codetemplates ����ע��ģ��

@EnableGlobalMethodSecurity(securedEnabled=true) 

#����Ȩ�ޣ���д��û��¼ʱû����ʽ��ʾ
security.ignored[0]=/css/*
security.ignored[1]=/js/**
security.ignored[2]=/images/*
security.ignored[3]=/fonts/**
security.ignored[4]=/**/favicon.ico
security.ignored[5]=/**/**.png
security.ignored[6]=webjars/**

Spring Security ֧�ֵ�SpEL���ʽ���£�

|��ȫ���ʽ��|
| 
|authentication ����|�û���֤����
|denyAll����	  |      ���ʼ��Ϊfalse
|hasAnyRole(list of roles)����	|����û�����Ȩָ��������Ȩ�ޣ����Ϊtrue
|hasRole(role)   |	����û���������ָ����Ȩ�ޣ���� Ϊtrue
|hasIpAddress(IP Adress)|	�û���ַ
|isAnonymous()����|	�Ƿ�Ϊ�����û�
|isAuthenticated()��|��	���������û�
|isFullyAuthenticated����|	��������Ҳ����remember-me��֤
|isRemberMe()����|	remember-me��֤
|permitAll	ʼ��true
|principal	|�û���Ҫ��Ϣ����


@EnableGlobalMethodSecurity �������ö������:
prePostEnabled :����SpringSecurity��ǰע���Ƿ�����磺@PreAuthorize,@PostAuthorize`
secureEnabled : �����Ƿ�Spring Security�ı���ע�� [@Secured] �Ƿ����`
jsr250Enabled ������ JSR-250 annotations ע��[@RolesAllowed..] �Ƿ����.`

1.Ҫ�Զ���Spring Security��ʱ����Ҫ�̳���WebSecurityConfigurerAdapter����ɣ����������д��Ӧ������ 

2.ע��CustomUserService��Bean��Ȼ��ͨ����дconfigure��������Զ������֤��ʽ�� 

3.��configure(HttpSecurity http)�����У������˵�¼ҳ�棬���ҵ�¼ҳ���κ��˶����Է��ʣ�Ȼ�������˵�¼ʧ�ܵ�ַ��Ҳ������ע������ע������Ҳ���κ��˶����Է��ʵġ� 

4.permitAll��ʾ�������κ��˶����Է��ʣ�.anyRequest().authenticated(),��ʾ���������󶼱���Ҫ��Ȩ����֤�� 

5.����ͨ��ƥ������ƥ��·����antMatchers�������������Ա�ſ��Է���admin�ļ����µ����ݣ�.antMatchers
("/admin/**").hasRole("ROLE_ADMIN")��Ҳ��������admin�ļ����µ��ļ������ж����ɫ�����ʣ�д�����£�.antMatchers("/admin/**").hasAnyRole("ROLE_ADMIN","ROLE_USER") 

6.����ͨ��hasIpAddress��ָ��ĳһ��ip���Է��ʸ���Դ,����ֻ�������ipΪ10.1.2.20�������ȡadmin�µ���Դ����ʽΪ��.antMatchers("/admin/**").hasIpAddress("10.1.2.20")



sha256���� 
