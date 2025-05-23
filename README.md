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

# Throttling

- throttleFirst
- throttleLast: sample
- throttleWithTimeout: debounce

```
Observable<Long> src = Observable.interval(100, TimeUnit.MILLISECONDS)
                .subscribeOn(Schedulers.io()).throttleLast(1000, TimeUnit.MILLISECONDS);

        src.subscribe(System.out::println);
```

# Buffer

buffer returns **list**

```
Observable.interval(100, TimeUnit.MILLISECONDS)
        .buffer(5)
        .subscribe(v-> System.out.println(v));
```

- output

```
[0, 1, 2, 3, 4]
[5, 6, 7, 8, 9]
[10, 11, 12, 13, 14]
[15, 16, 17, 18, 19]
[20, 21, 22, 23, 24]
[25, 26, 27, 28, 29]
[30, 31, 32, 33, 34]
...
```

# Window

buffer returns **list** but window returns **Observable**

```
Observable.interval(100, TimeUnit.MILLISECONDS)
                .window(10)
                .subscribe(v-> {
                    System.out.println();
                    v.subscribe(System.out::print);
                });
```

- output

```
0123456789
10111213141516171819
20212223242526272829
30313233343536373839
40414243444546474849
```
