# jdk.httpClient.HttpClient 로깅 방법

## VM Options

```shell
java -jar application.jar -Djdk.httpclient.HttpClient.log=requests,errors,headers
```

## Examples

```java
@Service
public class PostClient {

    private final RestClient restClient;

    public PostClient(RestClient.Builder builder) {
        this.restClient = builder
                .baseUrl("https://jsonplaceholder.typicode.com")
                .build();
    }

    public String findAll() {
        return restClient.get()
                .uri("/posts")
                .retrieve().body(String.class);
    }
}
```
