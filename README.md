# jdk.httpClient.HttpClient 로깅 방법

## VM Options

```shell
java -jar application.jar -Djdk.httpclient.HttpClient.log=requests,errors,headers
```

## Examples

```java

@Service
public class PostService {

    private final RestClient restClient;

    public PostService(RestClient.Builder builder) {
        var requestFactory = new JdkClientHttpRequestFactory();
        requestFactory.setReadTimeout(10_000);

        this.restClient = builder
                .baseUrl("https://jsonplaceholder.typicode.com")
                .requestFactory(requestFactory)
                .build();
    }

    public String findAll() {
        return restClient.get()
                .uri("/posts")
                .retrieve().body(String.class);
    }
}
```
