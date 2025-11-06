## What the **WebServiceListener** does  
  
* **Receives SOAP Web Service calls** – It turns a Frank! *Receiver* into a SOAP endpoint.  
* **Auto‑generates a WSDL** – Every adapter that contains one or more `WebServiceListener`s gets a WSDL file created by the framework.  
* You can view the WSDLs in the Frank! Console → *Webservices* → *Available WSDLs*.  
* The WSDL shows how to call the service – the service URL is inside the `<soap:address>` element (namespace `[http://schemas.xmlsoap.org/wsdl/soap/`).](http://schemas.xmlsoap.org/wsdl/soap/`\). "http://schemas.xmlsoap.org/wsdl/soap/%60).")  
* **Extracts request details into the session** – For each SOAP request the listener stores:  
* **MIME headers** → `session.get("mimeHeaders")` (XML)  
* **Attachments** → `session.get("attachments")` (XML)  
* **SOAP protocol** (e.g. 1.1 or 1.2) → `session.get("soapProtocol")`  
* **SOAPAction** header → `session.get("SOAPAction")`  
* **Supports multipart XML** – If you want to expose a multipart “XML‑only” version of the request, set the `multipartXmlSessionKey` attribute.  
* **No required attributes** – It can be dropped into a receiver without additional configuration, but you can optionally set `address` and `multipartXmlSessionKey`.  
  
---  
  
## How to use it  
  
1. **Add the listener to a receiver**  
```xml  
<receiver>  
<!-- other components … -->  
<WebServiceListener />  
</receiver>  
```  
  
2. **(Optional) Configure the endpoint URL**  
If you want a different URL than the one derived from the adapter’s mapping, add the *address* attribute:  
```xml  
<WebServiceListener address="[http://myhost:8080/myService"](http://myhost:8080/myService%22 "http://myhost:8080/myservice%22") multipartXmlSessionKey="multipartRequest"/>  
```  
  
3. **(Optional) Set the forward strategy** – after the listener processes a request you can decide what to do next:  
* `RETHROW` – send the error downstream  
* `FORMAT_AND_RETURN` – return a formatted response  
  
```xml  
<WebServiceListener address="..." forwards="RETHROW,FORMAT_AND_RETURN"/>  
```  
  
4. **Use the session data in downstream components**  
Inside your processing chain you can now read the automatically stored values:  
```java  
String mime = session.getString("mimeHeaders");  
String attachmentsXml = session.getString("attachments");  
String protocol = session.getString("soapProtocol");  
String action = session.getString("SOAPAction");  
```  
  
5. **Generate and test the WSDL**  
* In the **Frank! Console**, go to **Webservices → Available WSDLs**.  
* Download the WSDL or import it in your SOAP client to test.  
  
6. **Example of a full adapter**  
```xml  
<adapter name="OrderService">  
<receiver>  
<WebServiceListener address="[http://localhost:8181/orders"/>](http://localhost:8181/orders%22/> "http://localhost:8181/orders%22/%3e")  
<ApiListener /> <!-- processes the SOAP body -->  
</receiver>  
</adapter>  
```  
  
In this example the service URL will be [http://localhost:8181/orders`.](http://localhost:8181/orders`. "http://localhost:8181/orders%60.")
Any SOAP request coming in will have its headers, attachments and other metadata automatically set in the session so the following listener can focus on business logic.  8
  
---  
  
### Quick reference: session keys set by the listener  
  
| Session key | Description |  
|-------------|-------------|  
| `mimeHeaders` | XML with MIME headers |  
| `attachments` | XML describing any attachments |  
| `soapProtocol` | String (`soap11`, `soap12`, …) |  
| `SOAPAction` | SOAP action header value |  
  
That’s it – with a single `WebServiceListener` you expose a SOAP web service, let Frank! handle all protocol details, and give downstream logic access to the raw HTTP/SOAP metadata.