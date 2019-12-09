Using XSLT to handle unsupported XML constructs in Mendix import and export mappings
===

or

Java is not the only way
===

Mendix makes communicating with other systems using webservices very easy. Just 
import the service definition, pick your action and let Mendix generate mappings
and entities for the request and response.

Oh dear. The Value node is the one that contains the data that we want to 
retrieve! This means that we cannot use an import mapping to read the returned 
data. Offered suggestions on how to manage this situation were, to say the least, 
unhelpful:
  * “Don’t use that node” – well yes, but then we would not have the data!
  * “Change the XML schema” – it is a wsdl from a third party system, so I can’t 
    change it!
  * “Do it in Java” – the ultimate last resort, but such a shame not to be able 
    to use the easily configuratble import and export mappings that Mendix worked 
    so hard to provide us with!

Just for completeness, when we want to call the reciprocal action “DataFormSave”, 
we need to be able to export the same structure.

Let’s look at this another way. There are two conflicting requirements:
  1. We need the schema provided by the external service in order to communicate 
     with the service.
  2. We need a different schema to feed into a Mendix mapping.

What if we could separate these requirements and change the schema in between 
these two steps?

Step 1: separating the schemas
---

Normally we would call the import and export mappings from within the web service 
call action.
 
Instead, we are going to apply the mappings outside the web service call action, 
which gives us access to the XML both before and after.
 
Now all we need is a reliable way to transform one xml schema into a different one…

Oh! Hang on! That is exactly what XSLT is for!

Step 2: transforming the xml
---

Except that Mendix doesn’t do much in the way of XML tools. This is definitely a 
case for a custom Java action. I used a pretty simple bit of code using the Saxon 
XSLT library to take an input XML string and an input XSLT stylesheet and output a 
new XML string (you can find it in the App Store). Now that we can transform our 
XML, we can carry on!

Let’s have a look at the schema from the wsdl for a moment:
 
Searching for “DataFormLoadReply” found us the type of the reply element. From 
here we can do another search for the definition of our DataFormItem element.
 
So here we can see our problem element: “Value”. The issue is that the “type” 
attribute is missing, which means that it can actually hold data of any type. 
Mendix doesn’t do an “Any” type. Let’s see if we can come up with something that 
Mendix can handle, by giving it a type and allowing that type to contain a 
discrete element for each of the potential types of data it can contain:
 
Now we need to save this wsdl as a file and import it into Mendix as a separate 
service definition:
 
Now we have two web services: one that we can map and one that we can call.
