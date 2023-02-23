# feignclient
feign client example
  
  
                        **Currency-conversion -> Currency-Exchange -> Database**
                        
-**Step 1**  : add dependecies for openfeign
```
<!-- openfeign dependency -->
		<dependency>
			<groupId>org.springframework.cloud</groupId>
			<artifactId>spring-cloud-starter-openfeign</artifactId>
		</dependency>
```		
  
-***Step 2***: go to applicaton main class ```@EnableFeignClients```
  
-***Step 3***: Create proxy interface for those want to call
```
@FeignClient(name = "currency-exchange", url = "localhost:8000")
public interface CurrencyExchangeProxy {

    @GetMapping("currency-exchange/from/{from}/to/{to}")
    public CurrencyConversion getCurrencyExchange(@PathVariable String from, @PathVariable String to);

}
```
  
-***Step 4***: 
@autowired 
CurrencyExchangeProxy currencyExchangeProxy;


currencyExchangeProxy.getCurrencyExchange(from, to);

--------------------------------------------------------------------------------------
URL

http://localhost:8100/currency-conversion/from/USD/to/INR/quantity/10
http://localhost:8100/currency-conversion-feign/from/USD/to/INR/quantity/10
		                        
