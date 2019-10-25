package com.hcl.client;

import java.util.Arrays;
import java.util.List;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.http.ResponseEntity;
import org.springframework.web.client.RestTemplate;



public class UserServiceClientImpl implements UserServiceClient {
	
	@Autowired
	protected RestTemplate restTemplate;
	
	protected String serviceUrl;
	
	public UserServiceClientImpl(String serviceUrl) {
		this.serviceUrl = serviceUrl.startsWith("http") ? serviceUrl
				: "http://" + serviceUrl;
	}
	

	@Override
	public User getUserByName(String name) {
		User user=restTemplate.getForObject(serviceUrl+"/user/getUser/{name}", User.class,name);
		return user;
	}


	@Override
	public boolean knockOut(int civScore ,int standardCivScore) {
		boolean bool=false;
		if(civScore>=standardCivScore) {
			bool=true;
		} 
		return bool;
	}


	@Override
	public String registerUser(User user) {
		ResponseEntity<String> st=restTemplate.postForEntity(serviceUrl+"/user/registerUser", user, String.class);
		return st.getBody();
		
	}
	
}

	


