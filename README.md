# fd
-----------------
This is good project for a man who want to learn springboot dubbo 
server:
  port: 9020
spring:
  profiles:
    active: git
  application:
    name: zfbh-config
  cloud:
    config:
      server:
        enabled: true
        discovery:
          enabled: true
        git:
          uri: https://gitee.com/lxf1994/zfpt/zfbhConfigFiles/trunk
          username: 597143874@qq.com
          password: afeilovemeng
          default-label: master
#
#        svn:
#          uri: https://101.201.146.205/svn/LINE-PD-ZF/ZFBH/2代码类/版本V3.0/zfbhConfigFiles
#          username: zhanchuanyu
#          password: zcy0678
#          default-label: trunk

management:
  endpoints:
    web:
      exposure:
        include: "*"
  endpoint:
    health:
      show-details: always
#服务发现注册配置
eureka:
  instance:
    prefer-ip-address: true #使用IP注册
    instance-id: ${spring.cloud.client.ip-address}:${server.port}
    ##续约更新时间间隔设置5秒，m默认30s
    lease-renewal-interval-in-seconds: 5
    health-check-url-path: /actuator/health
  client:
    serviceUrl:
      #服务中心配置
      defaultZone: http://127.0.0.1:9010/eureka/