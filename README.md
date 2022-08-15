发送post请求：http://localhost:8082/actuator/bus-refresh, 验证config-client和config-server重新读取配置文件

日志：Received remote refresh request. Keys refreshed [config.client.version, user data]

问题：springCloud config配置中心client端无法从server端（git）中获取配置文件值
解决：https://blog.csdn.net/mqiqimiao/article/details/89407677
原因：github上面的配置名称前缀必须和client端spring.application.name=config-client 保持一致。所以按照github上的配置文件的名字构成规则，
github上的配置文件名称应该是config-client-master.properties，否则程序启动报错， java.lang.IllegalArgumentException: Could not resolve placeholder 'xxxx' in value "${xxxx}"。
