# primefaces-cheat-sheets

This repository is only for snipped code from DeepSeek and other websites about primefaces:

```
PrimeFaces.ajax.Request.handle({
    oncomplete: function(xhr, status, args) {
        console.log("Full response:", xhr.responseText);
    }
});
```

# to have fun

first of all you need to add some extra code

```
PrimeFaces.ajax.Request.handle({
    oncomplete: function(xhr, status, args) {
        console.log("Full response:", xhr.responseText);
    }
});
```

# Performance:

1. Limit processed components with process

2. Use partial updates with update

3. Set async: false only when absolutely necessary

- hello

this worked **fine** form me!

# remoteCommand- pass parameter from javascript to java

**remoteCommand**:

- name: javascript file name
- action: java action which runs after calling javascipt file

description: parameters can pass with a list of name value objects as below.

```
(*.xhtml)
<p:remoteCommand name="ajaxFunc"
                 action="#{sampleFile.handleAjaxRequest()}" />

<p:commandButton value="test remoteCommand"
                 process="@this"
                 onclick="ajaxFunc([{name:'myParam', value:'myValue'}])"/>

(*.java)
public void handleAjaxRequest(){
    Map<String, String> params= FacesContext
                  .getCurrentInstance()
                  .getExternalContext()
                  .getRequestParameterMap();

    System.out.println(params.get("myParam"));
}

```
