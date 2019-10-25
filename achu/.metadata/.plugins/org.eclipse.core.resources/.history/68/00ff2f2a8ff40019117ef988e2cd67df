package com.hcl.client;

import java.util.Arrays;
import java.util.List;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.http.ResponseEntity;
import org.springframework.web.client.RestTemplate;

public class ApplyLoanServiceClientImpl implements ApplyLoanServiceClient {
	@Autowired
	protected RestTemplate restTemplate;
	
	protected String serviceUrl;
	
	public ApplyLoanServiceClientImpl(String serviceUrl) {
		this.serviceUrl = serviceUrl.startsWith("http") ? serviceUrl
				: "http://" + serviceUrl;
	}


	@Override
	public String applyLoan(ApplyLoan al) {
		ResponseEntity<String> st=restTemplate.postForEntity(serviceUrl+"/loan/apply", al, String.class);
		return st.getBody();
	}

	
	
}
