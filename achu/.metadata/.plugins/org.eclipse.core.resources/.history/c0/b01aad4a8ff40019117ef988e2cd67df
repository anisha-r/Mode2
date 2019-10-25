package com.hcl.client;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.cloud.client.discovery.EnableDiscoveryClient;
import org.springframework.cloud.client.loadbalancer.LoadBalanced;
import org.springframework.context.annotation.Bean;
import org.springframework.web.client.RestTemplate;
import org.springframework.web.servlet.config.annotation.WebMvcConfigurer;



@SpringBootApplication
@EnableDiscoveryClient
public class WebClientApplication implements WebMvcConfigurer {
	
	public static final String USER_SERVICE_URL = "http://BANK-USERSERVICE";
	
	public static final String ACCOUNT_SERVICE_URL = "http://BANK-ACCOUNTSERVICE";


	public static void main(String[] args) {
		SpringApplication.run(WebClientApplication.class, args);
	}
	@Bean
	@LoadBalanced
	public RestTemplate restTemplate() {
		return new RestTemplate();
	}
	@Bean
	public UserServiceClient userServiceClient(){
		return new UserServiceClientImpl( USER_SERVICE_URL);
	}
	@Bean
	public ApplyLoanServiceClient accountServiceClient(){
		return new ApplyLoanServiceClientImpl( ACCOUNT_SERVICE_URL);
	}


}
