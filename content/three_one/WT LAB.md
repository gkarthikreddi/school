## Lists
```html
<html>
	<head>
		<title>Lists</title>
	</head>
	<body>
		<h2>Ordered List</h2>
		<ol>
			<li>Apple</li>
			<li>Banana</li>
			<li>Orange</li>
			<li>grapes</li>
		</ol>
		<h2>Unordered List</h2>
		<ul>
			<li>Japan</li>
			<li>China</li>
			<li>Thailand</li>
			<li>Turkey</li>
		</ul>
	</body>
</html>
```
## Embedded Images
```html
<html>
	<head>
		<title>Frames</title>
	</head>
	<body>
		<img src="url_to_your_image.jpg" alt="Description of the image">
	</body>
</html>
```
## Frames
```html
<html>
	<head>
		<title>Frames</title>
	</head>
	<body>
		<frameset rows="50%, *">
			<frame src="one.html">
			<frame src="two.html">
		</frameset>
	</body>
</html>
```
## XML
```xml
# A)
<!DOCTYPE student 
[
<!ELEMENT  student (name, marks)>
<!ELEMENT  name (#PCDATA)>
<!ELEMENT marks (#PCDATA)>
]>
<student>
<name>ravi</name>
<marks>56 </marks>
</student>

# B)
?xml version="1.0"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"
targetNamespace="http://www.vbithyd.ac.in"
xmlns="http://www.vbithd.ac.in"
elementFormDefault="qualified">

<xs:element name="employee">
<xs:complexType>
<xs:sequence>
<xs:element name="firstname" type="xs:string"/>
<xs:element name="lastname" type="xs:string"/>
<xs:element name="email" type="xs:string"/>
</xs:sequence>
</xs:complexType>
</xs:element>

</xs:schema>
Let's see the xml file using XML schema or XSD file.
employee.xml
<?xml version="1.0"?>
<employee
xmlns="http://vbithyd.ac.in"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://www.vbithyd.ac.inemployee.xsd">

<firstname>raviraj</firstname>
<lastname>Naidu</lastname>
<email>vimal@vbithyd.ac.in</email>
</employee>
```
## Table
```html
<html>
	<head>
		<title>Table</title>
<style>
table, th, td {
	border: 1px solid black;
}
</style>
	</head>
	<body>
		<center>
		<table>
			<tr>
				<th>Country</th>
				<th>Capital</th>
				<th>Sport</th>
			</tr>
			<th>India</th>
			<th>Delhi</th>
			<th rowspan="2">Cricket</th>
			</tr>
			</tr>
			<th>Pakisthan</th>
			<th>Karachi</th>
			</tr>
			</tr>
			<th colspan="3">This is Colspan</th>
			</tr>
		</table>
		</center>
	</body>
</html>
```
## Session Tracking
```java
#A) HTTP Session 
import javax.servlet.http.HttpServlet.*;
import java.io.IOException;

public class HttpSessionExample extends HttpServlet {
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        HttpSession session = request.getSession();
        session.setAttribute("username", "JohnDoe");
        String username = (String) session.getAttribute("username");
        response.getWriter().println("HttpSession Example - Welcome, " + username);
    }
}

#2) Cookies
import javax.servlet.http.Cookie;
import javax.servlet.http.HttpServlet;
import java.io.IOException;

public class CookiesExample extends HttpServlet {
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        Cookie usernameCookie = new Cookie("username", "JaneDoe");
        usernameCookie.setMaxAge(3600); // 1 hour
        response.addCookie(usernameCookie);
        response.getWriter().println("Cookies Example - Welcome, JaneDoe");
    }
}

#3) Hidden Form Controls
import javax.servlet.http.HttpServlet;
import java.io.IOException;

public class HiddenFormExample extends HttpServlet {
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        response.setContentType("text/html");
        response.getWriter().println("<html><body>");
        response.getWriter().println("<form action='/YourServletMapping/HiddenFormExample' method='post'>");
        response.getWriter().println("<input type='hidden' name='username' value='MarkSmith'>");
        response.getWriter().println("<input type='submit' value='Submit'>");
        response.getWriter().println("</form>");
        response.getWriter().println("</body></html>");
    }

    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        String username = request.getParameter("username");
        response.getWriter().println("Hidden Form Example - Welcome, " + username);
    }
}
```
## PHP Script
```php
<html>
<head>
    <title>Reads data from one file and write into another file in PHP</title>
</head>
<body>
<?php
    // filename to open
    $fname = "file1.txt";
    // to open file for reading
    $fptr = fopen($fname, "r");
    // to read content of the file
    $content=fread($fptr,filesize($fname));
    // to open for writing
    $fptw = fopen("file2.txt", "w");
    // to write content into another file
    fwrite($fptw,$content);
    echo "<strong>The content copied in file2 is:</strong> <br>". $content;
    //close files 
    fclose($fptr);
    fclose($fptw);
?>
</body>
</html>
```
## Servlet
```java
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Exception Handling in JSP</title>
</head>
<body>

<%
    try {
        int result = 10 / 0;
        out.println("Result: " + result); 
    } catch (Exception e) {
        out.println("<p style='color: red;'>An exception occurred: " + e.getMessage() + "</p>");
    }
%>

</body>
</html>
```