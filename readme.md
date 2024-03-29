# producing-web-service
This will build a SOAP-based web service which can provide country data.
Reference:
https://spring.io/guides/gs/producing-web-service/

# How to run
`./mvnw spring-boot:run`

or 
`./mvnw clean package`
and then run the JAR file
`java -jar target/producing-web-service-0.0.1-SNAPSHOT.jar`

# How to test
Now that the application is running, you can test it. 
- verify it is working by visiting http://localhost:8080/ws/countries.wsdl in local browser

- Create a file request.xml containing the following SOAP request:

`<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/"
				  xmlns:gs="http://spring.io/guides/gs-producing-web-service">
   <soapenv:Header/>
   <soapenv:Body>
      <gs:getCountryRequest>
         <gs:name>Spain</gs:name>
      </gs:getCountryRequest>
   </soapenv:Body>
</soapenv:Envelope>`

- test the soap interface with command line 

`$ curl --header "content-type: text/xml" -d @request.xml http://localhost:8080/ws `

- As a result you should see this response:

`<?xml version="1.0"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
  <SOAP-ENV:Header/>
  <SOAP-ENV:Body>
    <ns2:getCountryResponse xmlns:ns2="http://spring.io/guides/gs-producing-web-service">
      <ns2:country>
        <ns2:name>Spain</ns2:name>
        <ns2:population>46704314</ns2:population>
        <ns2:capital>Madrid</ns2:capital>
        <ns2:currency>EUR</ns2:currency>
      </ns2:country>
    </ns2:getCountryResponse>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>`

