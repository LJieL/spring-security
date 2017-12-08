分层
domain（放entity responsity）
Service
（controller分成web和api）
web ：页面跳转
api： post 登录之类
dto


http.csrf().disable();//解决403错误，post会出错，get不会。
		
//如果开启csrf <input type="hidden" th:name="${_csrf.parameterName}" th:value="${_csrf.token}" th:if="${_csrf}" />




codetemplates 代码注释模板

@EnableGlobalMethodSecurity(securedEnabled=true) 

#跳过权限，不写则没登录时没有样式显示
security.ignored[0]=/css/*
security.ignored[1]=/js/**
security.ignored[2]=/images/*
security.ignored[3]=/fonts/**
security.ignored[4]=/**/favicon.ico
security.ignored[5]=/**/**.png
security.ignored[6]=webjars/**

Spring Security 支持的SpEL表达式如下：

|安全表达式　|
| 
|authentication 　　|用户认证对象
|denyAll　　	  |      结果始终为false
|hasAnyRole(list of roles)　　	|如果用户被授权指定的任意权限，结果为true
|hasRole(role)   |	如果用户被授予了指定的权限，结果 为true
|hasIpAddress(IP Adress)|	用户地址
|isAnonymous()　　|	是否为匿名用户
|isAuthenticated()　|　	不是匿名用户
|isFullyAuthenticated　　|	不是匿名也不是remember-me认证
|isRemberMe()　　|	remember-me认证
|permitAll	始终true
|principal	|用户主要信息对象


@EnableGlobalMethodSecurity 可以配置多个参数:
prePostEnabled :决定SpringSecurity的前注解是否可用如：@PreAuthorize,@PostAuthorize`
secureEnabled : 决定是否Spring Security的保障注解 [@Secured] 是否可用`
jsr250Enabled ：决定 JSR-250 annotations 注解[@RolesAllowed..] 是否可用.`

1.要自定义Spring Security的时候，需要继承自WebSecurityConfigurerAdapter来完成，相关配置重写对应方法。 

2.注册CustomUserService的Bean，然后通过重写configure方法添加自定义的认证方式。 

3.在configure(HttpSecurity http)方法中，设置了登录页面，而且登录页面任何人都可以访问，然后设置了登录失败地址，也设置了注销请求，注销请求也是任何人都可以访问的。 

4.permitAll表示该请求任何人都可以访问，.anyRequest().authenticated(),表示其他的请求都必须要有权限认证。 

5.可以通过匹配器来匹配路径，antMatchers方法，假设管理员才可以访问admin文件夹下的内容：.antMatchers
("/admin/**").hasRole("ROLE_ADMIN")，也可以设置admin文件夹下的文件可以有多个角色来访问，写法如下：.antMatchers("/admin/**").hasAnyRole("ROLE_ADMIN","ROLE_USER") 

6.可以通过hasIpAddress来指定某一个ip可以访问该资源,假设只允许访问ip为10.1.2.20的请求获取admin下的资源，格式为：.antMatchers("/admin/**").hasIpAddress("10.1.2.20")



sha256加密 
