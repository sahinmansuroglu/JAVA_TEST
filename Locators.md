### Id ve Name  ###
```csharp

By.id("inputUsername")
By.name("inputPassword")
By.id("chkboxOne")
```
### CssSelector  ###

```csharp
By.CssSelector("#terms")
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
By.CssSelector("select.form-control")
By.CssSelector("input[type='radio']")
By.CssSelector("[value='Purchase']")
By.CssSelector(".ui-menu-item div")
  //th[aria - label *= 'fruit name']  burada * regular expression'da contains işlemi
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
(//div[@class='mainflip'])[2]
By.xpath("//input[@placeholder='Name']")
By.xpath("//input[@type='text'][2]")
By.xpath("//form/input[3]")
By.xpath("//div[@class='forgot-pwd-btn-conainer']/button[1]")
By.xpath("//button[contains(@class,'submit')]")
By.XPath("//div[@class='form-group'][5]/label/span/input")
By.XPath("//input[@value='Sign In']")
By.XPath("//div[@class='alert alert-danger col-md-12']")
By.XPath("//ul[@class='dropdown-menu']/li[1]/a")
By.XPath("//tr/th[1]/span[1]")
By.XPath("//tr/td[1]")
By.XPath("//tr/th[1]/span[1]")
 //th[aria - label *= 'fruit name']  burada * regular expression'da contains işlemi
//th[contains(@aria-label,'fruit name')]  yukarıdaki yapının xpath ile gösterimi
```
### Tagname ###

```csharp
By.TagName("app-card"))
```
