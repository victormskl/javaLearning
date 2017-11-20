# javaLearning

Servlet - http://devcolibri.com/4284

Logging - http://devcolibri.com/3413

Spring изнутри (работа с бинами, конфигурация и тд) - https://habrahabr.ru/post/222579

Spring AOP (get arg with some annotation):
@Before("execution(public * *(.., @SomeAnnotation (*), ..))")
public void checkRequiredRequestBody(JoinPoint joinPoint) {
    MethodSignature methodSig = (MethodSignature) joinPoint.getSignature();
    Annotation[][] annotations = methodSig.getMethod().getParameterAnnotations();
    Object[] args = joinPoint.getArgs();

    for (int i = 0; i < args.length; i++) {
        for (Annotation annotation : annotations[i]) {
            if (SomeAnnotation.class.isInstance(annotation)) {
                //... preprocessing
            }
        }
    }
}
