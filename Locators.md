### Id ve Name  ###
```csharp

By.id("inputUsername")
By.name("inputPassword")
By.id("chkboxOne")
```
### CssSelector  ###

```csharp
By.cssSelector("p.error")
By.cssSelector("input[placeholder='Email']")
By.cssSelector("input[type='text']:nth-child(3)")
By.cssSelector(".reset-pwd-btn")
By.cssSelector("#inputUsername")
By.cssSelector("form p")
By.cssSelector("input[type*='pass']")
By.CssSelector(".card-title a")
By.CssSelector("h4 a")

By.CssSelector("label[for*='checkbox2']")// for attribute değeri checkbox2 içereni seçer *:regx içerir anlamında kullanılır 
By.CssSelector(".clearfix b:nth-child(2)")
By.CssSelector("input[onclick*='displayConfirm']")
```
### className ###
```csharp
By.className("signInBtn")
```

driver.findElement().click();

### LinkText ve PartialLinkText ###

```csharp
By.PartialLinkText("Checkout")
By.linkText("Forgot your password?")
```
### XPath ###

```csharp
By.xpath("//input[@placeholder='Name']")
By.xpath("//input[@type='text'][2]")
By.xpath("//form/input[3]")
By.xpath("//div[@class='forgot-pwd-btn-conainer']/button[1]")
By.xpath("//button[contains(@class,'submit')]")
By.XPath("//div[@class='form-group'][5]/label/span/input")
By.XPath("//input[@value='Sign In']")
```
### Tagname ###

```csharp
By.TagName("app-card"))
```
