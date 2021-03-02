# AOP入口类注册

研究AOP是如何实现动态代理的。

Spring通过 `@EnableAspectJAutoProxy` 注解开启AOP支持。

通过`@Import`注解导入`AspectJAutoProxyRegistrar.class`

![image-20210302130846408](pic/image-20210302130846408.png)

在`AspectJAutoProxyRegistrar`类中进行AOP入口类的注册并设置对应属性。

![image-20210302131238933](pic/image-20210302131238933.png)

`AopConfigUtils.registerAspectJAnnotationAutoProxyCreatorIfNecessary()`方法中注册`AnnotationAwareAspectJAutoProxyCreator.class`

![image-20210302131758792](pic/image-20210302131758792.png)

`AnnotationAwareAspectJAutoProxyCreator`AOP入口类中优先级是最高的。

![image-20210302132006161](pic/image-20210302132006161.png)

![image-20210302131947200](pic/image-20210302131947200.png)

到这里AOP的入口类就注册完成了。

回到`AspectJAutoProxyRegistrar`这个类中，什么时候调用到`registerBeanDefinitions()`方法的呢？

在`ConfigurationClassPostProcessor`中对AOP `@Import`注解进行解析，`ConfigurationClassPostProcessor`是一个`BeanFactoryPostProcessor`，而`BeanFactoryPostProcessor`在bean收集完成之后进行实例化调用。

![image-20210302132948682](pic/image-20210302132948682.png)

所以AOP入口类实际是在`BeanPostProcessor`接口调用时注册的。

# 代理对象生成

AOP启用时注册了`AspectJAutoProxyRegistrar`这个入口类，所以AOP代理对象的生成就是在这个类中生成的。

![image-20210302163008733](pic/image-20210302163008733.png)

在Bean实例化完成后，会调用之前已经实例化的`BeanPostProcessor.postProcessAfterInitialization()`方法。这里就会调用到`AspectJAutoProxyRegistrar`类的相关方法。

![image-20210302163053244](pic/image-20210302163053244.png)

`wrapIfNecessary()`方法生成代理类。

![image-20210302163343955](pic/image-20210302163343955.png)

发现有作用在该Bean上的Advisor，就会创建一个Proxy。

![image-20210302164317399](pic/image-20210302164317399.png)

返回后，动态代理类就生成了。

# AOP Proxy对象执行

动态代理类生成了之后，实际是如何执行的呢？

以JDK动态代理类为例，在调用代理对象时，会调用`JdkDynamicAopProxy.invoke()`方法，

![image-20210302164944350](pic/image-20210302164944350.png)



![image-20210302165324912](pic/image-20210302165324912.png)