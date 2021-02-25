Spring源码下载以及编译流程记录

# 1. 下载源码

```SHELL
git clone --branch v5.2.8.RELEASE https://gitee.com/Z201/spring-framework.git
```

# 2. 修改`setting.gradle`文件

在`setting.gradle`文件中增加阿里云仓库

```groovy
repositories {
    gradlePluginPortal()
		
    maven { url 'https://maven.aliyun.com/repository/public' }
    
	maven { url 'https://repo.spring.io/plugins-release' }
}
```

# 3. 修改 `gradle.properties`文件

`gradle.properties`文件修改如下

```
version=5.2.8.RELEASE
org.gradle.jvmargs=-Xmx2048M
org.gradle.caching=true
org.gradle.parallel=true
org.gradle.configureondemand=true
org.gradle.daemon=true
```

# 4. 修改`build.gradle`文件

增加阿里云仓库

```json
repositories {
    mavenCentral()
    
    maven { url 'https://maven.aliyun.com/nexus/content/groups/public/' }
	maven { url 'https://maven.aliyun.com/nexus/content/repositories/jcenter'}

	maven { url "https://repo.spring.io/libs-spring-framework-build" }
}
```

# 5. 编译`spring-oxm`模块

在工程主目录下使用如下命令编译：

```shell
./gradlew :spring-oxm:compileTestJava
```

> 下载依赖时出现异常：暂未解决
>
> Could not HEAD 'https://repo.spring.io/plugins-release/io/spring/gradle-enterprise-conventions/io.spring.gradle-enterprise-conventions.gradle.plugin/0.0.2/io.spring.gradle-enterprise-conventions.gradle.plugin-0.0.2.jar'. Received status code 401 from server: Unauthorized

# 6. IDEA导入Spring源码

# 7. Idea安装`Kotlin`插件

# 8. 安装并配置`Gradle`





