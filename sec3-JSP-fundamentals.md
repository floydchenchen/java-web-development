# Section 3: JSP Fundamentals
## JSP Hello World
### What is a JSP file?
* An HTML page with some Java code sprinkled in… 
* Include dynamic content from Java code

### Where is the JSP processed?
* JSP is processed on the server 
* Results of Java code included in HTML returned to browser

### Where to place JSP file?
* The JSP ﬁle goes in your WebContent folder 
* Must have .jsp extension

## JSP Scripting Elements

| Elements | Syntax |
| --- | --- |
| JSP Expression | <%= some Java expression %> |
| JSP Scriptlet | <% some Java code: 1 to many lines %>|
| JSP Declaration | <%! variable or method declaration %> |

## JSP Expressions

* Compute an expression 
* Result is included in HTML returned to browser

`The time on the server is <%= new java.util.Date() %>`

## JSP Scriptlets
* Insert 1 to many lines of Java code 
* To include content in the page use: out.println(…)

```Java
<h3>Hello World of Java</h3>

<% for (int i=1; i <= 5; i++) { 
    out.println("<br/>I really luv2code: " + i); 
} %>
```

### best practice
* Minimize the amount of scriptlet code in a JSP
* Avoid dumping thousands of lines of code in a JSP
* Refactor this into a separate Java class … make use of MVC

## JSP Declarations
* Declare a method in the JSP page 
* Call the method in the same JSP page

```Java
<%!

String makeItLower(String data) { 
    return data.toLowerCase(); 
} %>

Lower case "Hello World": <%= makeItLower("Hello World") %>
```
## Call Java Class from JSP
![](https://raw.githubusercontent.com/floydchenchen/pictures/master/Screen%20Shot%202018-04-23%20at%202.50.13%20PM.png)

## JSP Built-In Server Objects
List of commonly used Built-in JSP objects

| Object | Description |
| --- | --- |
| request | Contains HTTP request headers and form data |
| response | Provides HTTP support for sending response |
| out | JspWriter for including content in HTML page |
| session | Unique session for each user of the web application |
| application | Shared data for all users of the web application |

## JSP - Including Files

```Java
<jsp:include page="my-header.html" />

<jsp:include page="my-footer.jsp" />
```

