# Section 4: Reading HTML form data with JSP

## HTML Forms Overview
* Review HTML Forms 
* Building HTML Forms 
* Reading Form Data with JSP

#### HTML file: form request

```HTML
First name: <input type="text" name="ﬁrstName" /> 
Last name: <input type="text" name="lastName" />
```
#### JSP file: form respond
```Java
<%= request.getParameter(“ﬁrstName”) %> 
<%= request.getParameter(“lastName”) %>
```

* Alternate syntax: `${param.formFieldName}`
* 

```Java
The student is conﬁrmed: ${param.ﬁrstName} ${param.lastName}
```

