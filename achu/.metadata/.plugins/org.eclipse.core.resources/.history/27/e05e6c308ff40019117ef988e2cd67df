package com.hcl.client;

import java.util.List;

import javax.servlet.http.HttpServletRequest;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.http.HttpRequest;
import org.springframework.http.ResponseEntity;
import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.ModelAttribute;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.servlet.ModelAndView;

@RestController
public class UserClientController {
	@Autowired
	UserServiceClient userServiceClient;
	
	@Autowired
	ApplyLoanServiceClient applyLoanServiceClient;
	
	@RequestMapping("/")
	public ModelAndView home(ModelAndView model){
		User user = new User();
		model.addObject("user", user);
		model.setViewName("login");
		return model;
	}
	@RequestMapping("/home")
	public ModelAndView  loginAccount(@ModelAttribute Login user) {
		String passWord=userServiceClient.getUserByName(user.getUserName()).getPassWord();
		int id=userServiceClient.getUserByName(user.getUserName()).getId();
		if(user.getPassWord().equals(passWord)) {
			return new ModelAndView("redirect:/homePage1");
		} else {
			return new ModelAndView("redirect:/");
		}
	}
	@RequestMapping(value="/homePage1",  method = RequestMethod.GET)
	public ModelAndView  home1(ModelAndView model) {
		
		model.setViewName("dashboard");
		return model;
	}
	@RequestMapping(value = "/saveApplication", method = RequestMethod.POST)
	public ModelAndView saveApplication(@ModelAttribute ApplyLoan application,ModelAndView model) {
		String st,st1="";
		int civicScore=95;
		boolean bool;
		if (application.getUserId()>0) { 
			bool=userServiceClient.knockOut(application.getCivicScore(), civicScore);
			if(bool==true) {
			 st=applyLoanServiceClient.applyLoan(application);
			 st1="Congrats, you are elegible for loan";
			} else {
				st1="Sorry, you are not eligible";
			}
		} 

		
		model.addObject("msg",st1);
		model.setViewName("message");
		return model;
		
	}
	@RequestMapping(value="/ApplyLoan",  method = RequestMethod.GET)
	public ModelAndView  goToApplyLoan(ModelAndView model) {
		ApplyLoan al=new ApplyLoan();
		
		model.addObject("loanApp",al);
		model.setViewName("applyLoan");
		return model;
	}
	@RequestMapping(value = "/register", method = RequestMethod.GET)
	public ModelAndView registerUser(ModelAndView model) {
		
		User user=new User();
		model.addObject("user1",user);
		model.setViewName("register");
		return model;
		
	}
	@RequestMapping(value = "/saveRegister", method = RequestMethod.POST)
	public ModelAndView saveRegister(@ModelAttribute User user1,ModelAndView model) {
		
		String str="";
		
			
			str=userServiceClient.registerUser(user1);
			
		
		
		model.addObject("msg",str);
		model.setViewName("message");
		return model;
		
	}
	@RequestMapping(value = "/calculateMortgage", method = RequestMethod.GET)
	public ModelAndView claculateMortgage(ModelAndView model) {
		
		
		model.setViewName("mortageCalc");
		return model;
		
	}
	@RequestMapping(value = "/moratageoffer", method = RequestMethod.GET)
	public ModelAndView fetchOffer(ModelAndView model) {
	
	ApplyLoan a=new ApplyLoan();
	int loan=a.getLoanAmount();
	model.addObject("loanAmount",loan);
	model.setViewName("MortgageOffer");
	return model;
	}
}
	
	

