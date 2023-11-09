
I have created a java based web application involving " Content Management System " of 'DEMO BANK' concept in which I have made 5 Java Server Pages(JSP) that user will be interacting in front end part , 5 session pages which is linked with 2 Servlets.The detailed explaination is given below.

##THE LOGIN PAGE ##:From here the user will login into bank account after login only the user can be directed to home page.

*) The Home page JSP: It is consisting links of various registration forms i.e; Bank Account registration form, bank Authorization form,Credit Request Form, Direct Deposit Authorization Form, Loan Application form etc, on clicking the user will be redirecting to it. 
*)We are having the logout button through which the logout user can logout from the account.





###  BANK REGISTRATION FORM  ###



"FRONTEND PART":
* After filling all the required fields (mandatory)in the given form, when the user clicks on 'save registration' the user will be redirected to 'registersession.jsp'. If any of the details are missing then the prompt will say" plss fill therequired form fields" else details can't be saved.

* "BACKEND FUNCTIONALITY":FOR VALIDATION
* The code is written under try statement so that any exceptions that occur get caught in try block which which can be further handled in catch block.

*  The  input type of 'save registration' is given as 'submit' and the name is specfied as 'action' , this name value is retrieved in    "Newservlet.java"  using request.getParameter() method , this value is compared with 'save registration' , if the value comes out to be  save registration, then all the fields of the Bank Account Registartion will be retrieved in the NewServelet.java, using request.getParameter() method and those values will be passed in the 'register session.jsp'.
  
*   Before passing the values in the session, firstly we need to create the Session , for creating session I have used 'HTTPSession session= request.getSession()' in the body of the servlet  and for creating object of session we require HttpSession class ,for this the HttpSession class is imported from java package using import statement 'import javax.servlet.http.HttpServlet' for enabling the actions to be performed using session.
  
*   Now the values can  pass into the session so for passing values into the session using 'HttpSession' object. After this the value can be set into the session using setAttribute method 'session.setAttribute("random value","retrived value for specific field let say Name of the account holder");'. In the registersession.jsp firstly the line of code 'session =request.getSession(false); will retrieve the current httpSession associated with "HttpServletRequest" object named "request".
  
*    Then, the session value is retrieved using session= request.getAttribute("random value"); after getting all the values from the sesson , they are displayed on 'Register.jsp ' webpage. After the values are displayed in the session page.

*    Then, below a button named     "submit registration"     is given through which the data can be submited into the database successfully. For getting values in database i have used another servlet named "NewServlet1.java" , the database connection is made by firstly  loading the JDBC Driver named "ojdbc" by using import satament import java.sql.DriverManager before using this we need sql class so that we can import DriverManager class from that by using import java.sql.*; and after that registering it by using statement "Class.ForName("com.mysql.jdbc.Driver");".
*    
*  After loading and registering  the driver "Oracle Java Database Connectivity" ,the connection to the relational database named "bank_management_system" is done, by writing the statement "Connection con=DriverManager.getConnection("JDBC URL","USERNAME","PASSWORD"); " For writing this it will show a compilating error in Connection type named "Connection" because I have not defined it in class and for removing this error i have to import the Connection class from java package by using import statement import java.sql.Connection; still it shows an error because i have not imported sql class from java package and after importing the sql class by using import statement import java.sql.*; the error goes off.
   
* After this, the code is written inside the try catch block for high efficiency (by using request.getPararmeter the button vaklue is retrieved from frontend(registersession.jsp) the clicked button functionlity is checked if the click is a valid click(the value should match which the value of the registersession) then the values will be inserted in the MySQl database, for insertion the insert query is used i.e; String query="Insert into Table_name(columnname1,columnname2,...columnname n) values('"+value1+"','"+value2+"','"+value3+"'); For executing this query a  and for altering any changes to database, I have used PreparedStatement feature of JDBC by using import statment import java.sql.PreparedStatement; for working with sql queries.
* Then, execute statemnet is written for executing the query successfully.Finally the data gets inserted successfully and a message is printed on the server.


##Authorizaton form##: 
*Front end part: All the html fields with their input type such as text,email,telephone number,password is given.Required funtionality is given as every field is manadatory to write.

*BACKEND PART: After filling the html fields the user as the user clicks on the Save bankauthorization button the user will be redirected to the 'bankauthsession.jsp' webpage.
* In NewServlet the values of the html fields is retrieved by using equest.getParamter() method and then the button value is compared if that comes out to be 'save bankauthorize' button then it will proceed for saving the details to the session again  i have created a new session so that previous session values get removed  by using HttpSession session = request.getSession(true);//using this true it will clear previous session values. After creating the values will be passed to session using session.setAttribute("new value",the previous value");
* After that using response.sendRedirect(url); will redirect the user to authorizesession page.
* in the sessionjsp again the values will be retrieved using session=request.getSession(false)//false so that new session wont get created.
* the same way values are printed and finally there a button named submit authorizeform through which the form values gets submitted into the database using insert query.

* The same way the Credit request, direct deposit authorization and loan application form works out.








