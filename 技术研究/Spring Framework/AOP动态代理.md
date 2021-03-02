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



