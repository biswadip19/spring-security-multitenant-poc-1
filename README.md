This sample application consists of below key points/aspects :
--------------------------------------------------------------
Spring boot with customized multitenant framework
--------------------------------------------------
1. It handles dynamic implementation of single Dispatcher server, this dispatcher servlet is also being 
   a custom implementation of Servlet ( TenantDispatcherServlet ) to handle multiple tenants with their specified hostname or domain name.
   
2. Each request comes to TenantDispatcherServlet's Service method being parser and identified by the request host name and then being forwarded to specific tenant Dispatcher Servlet.
   
3. Each Tenant specific configurations components like number of tenants, tenant specific folder path, configuration class name has been kept dynamic based on the configuration provided in the properties file ( config3.properties ).

4. Tenant1WebConfig & Tenant2WebConfig implements WebMvcConfigurer with instantiating InternalViewResolver      	with required suffix and prefix.

5. CustomWebSecurityConfigurer is generic Web Security configurer adaptor handles both the tenants. It extends WebSecurityCOnfigurerAdaptor abstract class.

6. Importent note : This multi-tenant implementation requires exclusion of SecurityAutoConfiguration.class in SpringBootApplication in order to make the custom security framework working. ( This approach is not required in the other multi-tenant project named - multitenant )

7. Importent note :  This implementation does not require to specify the "FilterProcessingUrl" as /login
in the custom UsernamePasswordAuthenticationFilter.

8. This project also use Spring-boot-configuration-processor to use and implement the properties loading in the application in a sample bean in different formats like map, list & string format. It uses below new annotations :
				@PropertySource("classpath:config.properties")
				@ConfigurationProperties(prefix = "tenant") 

9. 




    