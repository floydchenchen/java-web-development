# Section 5: State Management With JSP

## Session Tracking with JSP
* Session Tracking Demo 
* Session - Coding Steps 
* Full JSP Session Example

### JSP session object
* JSP session is created once for user’s browser session. **Unique for this user**.
* Commonly used when you need to **keep track of the user’s actions**. 
![](https://raw.githubusercontent.com/floydchenchen/pictures/master/Screen%20Shot%202018-04-23%20at%204.27.08%20PM.png)

### Add data to session object

#### Signatures
```Java
session.setAttribute(String name, Object value)
Object session.getAttribute(String name)
```

#### code example

```Java
List<String> items = new ArrayList<>(); 
session.setAttribute(“myToDoList”, items);

List<String> myStuff = (List<String>) session.getAttribute(“myToDoList”);
```

#### Other Useful Methods

| isNew(): boolean | Returns true if the session is new |
| --- | --- |
| getId() : String | Returns the session id |
| invalidate() : void | Invalidates this session and unbinds any object associated with it |
| setMaxInactiveInterval(long mills) : void | Sets the idle time for a session to expire. The value is supplied in milliseconds |


code example

```Java
<!-- Step 2: Add new item to "To Do" list -->
<%
	// get the TO DO items from the session
	List<String> items = (List<String>) session.getAttribute("myToDoList");

	// if the TO DO items doesn't exist, then create a new one
	if (items == null) {
		items = new ArrayList<String>();
		session.setAttribute("myToDoList", items);
	}
	
	// see if there is form data to add
	String theItem = request.getParameter("theItem");
	if (theItem != null && theItem != "") {
		items.add(theItem);
	}
%>
```

## Cookies

### What is the Purpose of Cookies?
* Personalize a web site for a user
* Keep track of user preferences
* What is a Cookie?
    * Text data exchanged between web browser and server
* Cookie content
    * Name / value pair
* How Are Cookies Passed?
    * Browser will only send cookies that match the server’s domain name

### Cookie API - Package
* Cookie class deﬁned in package: javax.servlet.http
* Package imported for free in all JSP pages

#### Cookie Constructor
```Java
Cookie(String name, String value)
```

##### Sending Cookies to Browser
```Java
<% String favLang = request.getParameter("favoriteLanguage");

// create cookie 
Cookie theCookie = new Cookie("myApp.favoriteLanguage", favLang);

// set life span ... total number of seconds 
theCookie.setMaxAge(60*60*24*365);

// send cookie to browser 
response.addCookie(theCookie); %>
```

##### Reading Cookies from the Browser

```Java
<!-- read the favorite programming language cookie --> 
<% String favLang = "Java";

Cookie[] theCookies = request.getCookies();

if (theCookies != null) { 
    for (Cookie tempCookie : theCookies) {
        if ("myApp.favoriteLanguage".equals(tempCookie.getName())) { 
            favLang = tempCookie.getValue(); 
            break; 
        }
    }
} %>
```


