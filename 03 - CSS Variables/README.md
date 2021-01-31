# 03 - Update CSS Variables with JS
## 1. CSS custom properties (CSS variables)  
  
Like variables in other languages, we can also use variables/custom properties in CSS.  

**Set the value**  

The property name is case sensitive and should start with double dashes `--`. These custom properties also inherit. E.g.  
```
/* global custom properties, apply to all elements in the document */
:root { 
  --spacing: 10px;
  --blur: 10px;
  --base: #ffd877;
}

/* local properties in class .class-a*/
.class-a {
  --bg-color: azure;
  --BG-color: gold;
}
```  

**Access the value**  
To access the value of a custom property, we use `var()` function. E.g.  
```
img{
  padding: var(--spacing);
  filter: blur(var(--blur));
  background-color: var(--base, #ffd877);  /* if --base is undefined, the default value is #ffd877*/
}
```
  
## 2. Update CSS variables with JS  
Here, we use `setProperty()` method to set the value of a CSS custom property. `setProperty()` is a method of `CSSStyleDeclaration` object.   
 
```
document.documentElement.style.setProperty(`--${this.name}`, this.value + suffix);
```
  
`document.documentElement` will get the root element of the document, i.e. `<html>` element. Then, `setProperty()` will update the property values on inline style. We can see the changes in the inline style of `<html>` element:  

<img src='README-pics/update-global-css-var.gif' height='300px'>  
  

You can also set the **local** custom properties by   

```
element.style.setProperty('--property-name', 'value');
```
<img src='README-pics/set-local-css-var.gif' height='300px'>  
  
On the other hand, you can get the variable value from inline style through:  
```
element.style.getPropertyValue('--property-name');
```