---
layout: post
title: Spring MVC + sql server 整合通用 mapper
categories: sqlserver
description: Spring MVC + sql server 整合通用 mapper
keywords: sql server
---

***爱上一个人,心会一直低,低到泥土里,在土里开出花来,如此卑微却又如此欣喜。***  

# pom 增加 jar 包
```xml
<mapper.version>4.0.0</mapper.version> 
 <dependency>
      <groupId>tk.mybatis</groupId>
      <artifactId>mapper</artifactId>
      <version>${mapper.version}</version>
  </dependency>
```

# Spring - mybatis 的配置文件
```xml
    <!--在Spring中配置Mapper接口 -->
    <bean class="tk.mybatis.spring.mapper.MapperScannerConfigurer">
        <!-- 为映射器接口文件设置基本的包路径 -->
        <property name="basePackage" value="com.platform.dao" />
    </bean>
```

# 通用 MyMapper 
```java
import tk.mybatis.mapper.common.Mapper;
import tk.mybatis.mapper.common.SqlServerMapper;

public interface MyMapper<T> extends Mapper<T> {
    //TODO
    //FIXME 特别注意，该接口不能被扫描到，否则会出错
}
```

# Mapper.java 文件 
```java

import java.util.List;
import com.platform.entity.MrMsgRecord;
import com.platform.utils.MyMapper;

public interface MrMsgRecordMapper extends MyMapper<MrMsgRecord> {

    /**
    * 根据条件查询，主键倒序排序
    */
    List<MrMsgRecord> selectByQuery(MrMsgRecord mrMsgRecord);

}
```

# model 文件 
```java
import java.io.Serializable;
import java.util.Date;
import javax.persistence.*;
import lombok.Data;
import io.swagger.annotations.ApiModel;

import io.swagger.annotations.ApiModelProperty;
import tk.mybatis.mapper.annotation.KeySql;

@ApiModel
@Data
@Table(name = "mr_msg_record")
public class MrMsgRecord implements Serializable {
	private static final long serialVersionUID = 1L;
	
	// 这两个注解是为了sqlserver 可以自增、获取自增的 id 值
    @KeySql(useGeneratedKeys = true)
    @Column(insertable=false)
    private Long mrId;

    @ApiModelProperty(value = "创建时间")
    @Column(name = "mr_create_time")
    private Date mrCreateTime;

    @ApiModelProperty(value = "(接收者ID)指向用户表    外键")
    @Column(name = "mr_target_id")
    private String mrTargetId;

    @ApiModelProperty(value = "聊天信息")
    @Column(name = "mr_msg_body")
    private String mrMsgBody;

    @Id // 这个是代表这个字段是主键，多个 @Id 代表多个主键
    @ApiModelProperty(value = "(发送者ID)指向用户表    外键")
    @Column(name = "mr_from_id")
    private String mrFromId;

    @Id // 这个是代表这个字段是主键，多个 @Id 代表多个主键
    @ApiModelProperty(value = "")
    @Column(name = "mr_code")
    private String mrCode;
}

// 注意：没有 @Id 则默认所有字段都是主键
```

# Mapper.xml 文件 
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN" "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.platform.dao.MrMsgRecordMapper">
    <resultMap type="com.platform.entity.MrMsgRecord" id="mrMsgRecordMap">
        <result property="mrId" column="mr_id"/>
        <result property="mrCreateTime" column="mr_create_time"/>
        <result property="mrTargetId" column="mr_target_id"/>
        <result property="mrMsgBody" column="mr_msg_body"/>
        <result property="mrFromId" column="mr_from_id"/>
        <result property="mrCode" column="mr_code"/>
    </resultMap>

    <select id="selectByQuery" resultMap="mrMsgRecordMap">
        select * from mr_msg_record
        <where>
            <if test="mrId != null and mrId != ''">
                and mr_id = #{ mrId }
            </if>
            <if test="mrCreateTime != null ">
                and mr_create_time = #{ mrCreateTime }
            </if>
            <if test="mrTargetId != null and mrTargetId != ''">
                and mr_target_id = #{ mrTargetId }
            </if>
            <if test="mrMsgBody != null and mrMsgBody != ''">
                and mr_msg_body = #{ mrMsgBody }
            </if>
            <if test="mrFromId != null and mrFromId != ''">
                and mr_from_id = #{ mrFromId }
            </if>
            <if test="mrCode != null and mrCode != ''">
                and mr_code = #{ mrCode }
            </if>
        </where>
        order by mr_id desc
    </select>

</mapper>
```

## 其他的方法请百度





