package tests;

import org.json.simple.JSONObject;
import org.testng.annotations.Test;

import io.restassured.http.ContentType;

import static io.restassured.RestAssured.*; //for directly using RestAssured class methods
import static org.hamcrest.Matchers.*;

import java.util.HashMap;
import java.util.Map;




public class TestGetandPost {
	
	//@Test
	public void testGet() {
		given()
			.get("https://reqres.in/api/users?page=2")
		.then()
			.statusCode(200) //assert GET response statusCode
			.body("data[5].first_name", equalTo("Rachel")) //assert if the GET response body has a certain item
			.body("data.first_name", hasItems("Rachel","George")); //assert if the GET response body has a set of items in the response JSON
	}
	
	//For testing post request, we need the output in json format, for that we need JSONObject class 
	//, this class is available under a Goggle library named 'JSON SIMPLE'
	// which we need to add as maven dependency. Then we can use JSONObject class & its methods
	//also, We need to make the use of Map data structure Map<KeyDatatype,ValueDataType> mapObj=new Hashmap<KeyDataType,ValueDataType>>();
	
	//@Test
	public void testPost() {
		
		//Method1- Java Core approach to play around with Key.Value type data
		Map<String,Object> mapObj=new HashMap<String,Object>();
		mapObj.put("name", "Sakshi");
		mapObj.put("Age", "29");
		System.out.println(mapObj);
		JSONObject JSONresponse=new JSONObject(mapObj);
		System.out.println(JSONresponse);
		
		//Method2-Actual Code to Automate a POST Request using RestAssured
		
		baseURI="https://reqres.in/api"; //since we have done static import of class so we can directly use baseURL as a class variable
		JSONObject requestBody=new JSONObject();
		requestBody.put("name", "Anie");
		requestBody.put("job", "SDET-2");
		System.out.println("\nMy request body is\n"+requestBody);
		//Automate POST given()--> requestbody, when()--->provide action ie http method, then()-->provide the required assertion
		given()
			.body(requestBody.toJSONString()) //if we do not use toJSONString() then it wont parse .
		.when()
			.post("/users")
		.then()
			.statusCode(201);
		
	
	}
	@Test
	public void testPostComplex() {
		baseURI="https://reqres.in/api";
		JSONObject requestBody=new JSONObject();
		requestBody.put("name", "Rahul");
		requestBody.put("job","Developer");
		System.out.println("/n Testing advance automation of post request\n"+requestBody);
	    
		//automate- here we provide under given()-> headers, contentType,requestBody & log().all() function to print the entire response body in json
		given()
			.header("Content-Type","application/json")
			.contentType(ContentType.JSON)
			.accept(ContentType.JSON)
			.body(requestBody.toJSONString())
		.when()
			.post("/users")
		.then()
			.statusCode(201)
			.log().all(); //to log the whole response Json in the console
	}

}
