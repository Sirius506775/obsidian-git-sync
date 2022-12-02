
Spring boot API 서버에서 http 요청 시 Cors 설정이 안되어 있다면 

**allowMethods 설정을 살펴보아야한다. 
따라서 아래와 같이 허용할 설정해 주면 해결할 수 있는데 allowMethod를 추가할 경우 DEFAULT 설정이 사라지기 때문에 **GET**,**HEAD**,**POST** 또한 포함해 주어야 합니다.

```java
@Override
public void addCorsMappings(CorsRegistry registry) {
  registry.addMapping("/**")
  	.allowedOrigins("http://localhost:8081")
    .allowedMethods(
    	HttpMethod.GET.name(),
    	HttpMethod.HEAD.name(),
    	HttpMethod.POST.name(),
    	HttpMethod.PUT.name(),
    	HttpMethod.DELETE.name());
}
```
```