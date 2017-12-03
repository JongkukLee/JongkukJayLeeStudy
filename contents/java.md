---
layout: default
---
# Java
---

## SERVLET ##
SEQ37: 
url-mapping 
1. describe with annotation in the servlet file
@WebServlet(“/initP”)
@WebServlet(urlPatterns=[“/initP”], initParam={@WebInitParam(name=”id”, value=”AAA”)})
2. web.xml: servlet mapping, context-path: server.xml

protected void doPost/doGet(HttpServletReuest request, HttpServletResponse response) throws ServletException, IOException  

response.setContentType(“text/html”):
PrintWriter writer = response.write();
writer.println(/*html source here*/);
writer.close();

SEQ38
eclips: auto-completion shift + enter, web-project

init(): start time at once, doGet(): during life time, service():call it if no doPost and doGet, doPost(): during life time, destroy(): when server stop, at once ; @overried, @PostConstruct, @PreDetory

SEQ39
getParameter(name), getParameterValues(name): when there are multiple values, getParameterNames()

protected void doPost(HttpServletReuest request, HttpServletResponse response) throws ServletException, IOException 
String id = request.getParamet(“ID”);


SEQ40
1. ServletConfig: initial parameter in specific servlet, first way, describe with “<init-param>” in web.mxl and approach with ServletConfig, second way, describe with annotation (@WebInitParam) in Servlet file
@WebServlet(urlPatterns=[“/initP”], initParam={@WebInitParam(name=”id”, value=”AAA”)}), String id = getInitParameter(“id”);
2. ServletContext: share data, describe context parameter with “<context-param>” in web.xml file, String id = getServletContext().getInitParameter(“id”);
3. ServletContextListener: monitor the life cycle of the apps, implement a listener class, describe it in web.xml





## JSP ##

JSP Tags: 
Directive: <%@ %> - the attribute of page 
Comment: <%-- --%>
Declaration: <%! %> - declarate variables, methods
Expression: <%= %> - display results
Scriptlet: <% %> - input Java code
Action: <jsp:action></jsp:action> - connect to java bean

The different of Servlet and Jsp

|     |Servlet|Jsp|
|-----|-----|-----|
|Contrast: |In Java Code base, html code is inserted through PrintWriter |In html Code base, java code is inserted with tag '<% %>'|
|Comparision: | |JSP is converted to Servlet code once it is requested |

Action Principle :
![Image]({{ site.globalurl }}/contents/img_java/jsp1.jpg)

Build-in Object: when jsp is converted, the build-in objects are automatically created by the jsp-container. 
1. IO object: request, reponse, out
2. Servlet object: page, config
3. Session object: session
4. Exception object: exception










### Custom Tags ###

[oracle.com](https://docs.oracle.com/javaee/5/tutorial/doc/bnalj.html)
[TutorialsPoint](https://www.tutorialspoint.com/jsp/jsp_custom_tags.htm)








