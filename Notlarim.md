## Selenium Notlar ##

https://www.swtestacademy.com/xpath-selenium/

### SetUp StartBrowser  ###
```csharp
        [SetUp]
        public void StartBrowser()
        {
            new WebDriverManager.DriverManager().SetUpDriver(new ChromeConfig());

            driver = new ChromeDriver();
            driver.Manage().Timeouts().ImplicitWait =TimeSpan.FromSeconds(5); 

            driver.Manage().Window.Maximize();
            driver.Url = "https://rahulshettyacademy.com/seleniumPractise/#/offers";
        } 
 ```
### LocatorsIdentification ###
```csharp
 [Test]
        public void LocatorsIdentification()
        {
            driver.FindElement(By.Id("username")).SendKeys("rahulshettyacademy");
            driver.FindElement(By.Id("username")).Clear();
            driver.FindElement(By.Id("username")).SendKeys("rahulshetty");
            driver.FindElement(By.Name("password")).SendKeys("12345678");
            //css selector & xpath
            // tagname[attribute='value']
            // driver.FindElement(By.CssSelector("input[value='Sign In']")).Click();

            // xpath yapısı--> //tagName[@attribute='value'] 

            // #id #terms  -- class name --> css .classname

            //CSS class name ---> ".text-info span:nth-child(1) input" 
            // X-Path --->     "//label[@class='text-info']/span/input"
            // #terms
            // driver.FindElement(By.XPath("//div[@class='form-group'][5]/label/span/input")).Click();
            driver.FindElement(By.CssSelector("#terms")).Click();


            driver.FindElement(By.XPath("//input[@value='Sign In']")).Click();

            //Implicit wait tanımlandığı için thread sleep'e gerek kalmadı
            //Thread.Sleep(3000);
            //class="alert alert-danger col-md-12"
            //  String errorMessage=driver.FindElement(By.ClassName("alert-danger")).Text;

            WebDriverWait wait = new WebDriverWait(driver, TimeSpan.FromSeconds(8));
            //Sign in işleminde buton Signin in oluyor. Tekrar sign in butonu ekrana geldiğinde hata mesajı veriyor
            // Aşağıdaki kod ile buton Sign İn olanan kadar bekletiliyor.
            //wait.Until(SeleniumExtras.WaitHelpers.ExpectedConditions.TextToBePresentInElementValue(driver.FindElement(By.Id("signInBtn")), "Sign In"));

            //Aşağıdaki kodlar alert mesajı ekrana gelene kadar bekletiliyor.
            wait.Until(SeleniumExtras.WaitHelpers.ExpectedConditions.ElementIsVisible(By.XPath("//div[@class='alert alert-danger col-md-12']")));
            String errorMessage = driver.FindElement(By.ClassName("alert-danger")).Text;

            TestContext.Progress.WriteLine(errorMessage);

            TestContext.WriteLine(errorMessage);

            driver.FindElement(By.Id("username")).SendKeys(errorMessage);
            IWebElement link = driver.FindElement(By.LinkText("Free Access to InterviewQues/ResumeAssistance/Material"));

            String hrefAttr=link.GetAttribute("href");
            string expectedURL="https://rahulshettyacademy.com/#/documents-request";
            Assert.AreEqual(expectedURL, hrefAttr);
           //validate url of the text 


        }
```
### LocatorsIdentification1 ###
```csharp
[Test]
        public void LocatorsIdentification1()
        {
            driver.FindElement(By.Id("username")).SendKeys("rahulshetty");
            driver.FindElement(By.Name("password")).SendKeys("12345678");
            driver.FindElement(By.XPath("//input[@value='Sign In']")).Click();
            WebDriverWait wait = new WebDriverWait(driver,TimeSpan.FromSeconds(8));
            //Sign in işleminde buton Signin in oluyor. Tekrar sign in butonu ekrana geldiğinde hata mesajı veriyor
            // Aşağıdaki kod ile buton Sign İn olanan kadar bekletiliyor.
            //wait.Until(SeleniumExtras.WaitHelpers.ExpectedConditions.TextToBePresentInElementValue(driver.FindElement(By.Id("signInBtn")), "Sign In"));
           
            //Aşağıdaki kodlar alert mesajı ekrana gelene kadar bekletiliyor.
            wait.Until(SeleniumExtras.WaitHelpers.ExpectedConditions.ElementIsVisible(By.XPath("//div[@class='alert alert-danger col-md-12']")));
            String errorMessage = driver.FindElement(By.XPath("//div[@class='alert alert-danger col-md-12']")).Text;
            driver.FindElement(By.Id("username")).SendKeys(errorMessage);
        }

/scroll frame'e kadar kaydırma yapılmalı
            IWebElement frameScroll = driver.FindElement(By.Id("courses-iframe"));
            IJavaScriptExecutor js = (IJavaScriptExecutor)driver;
            js.ExecuteScript("arguments[0].scrollIntoView(true);",frameScroll);
        

            // id, name, index
            driver.SwitchTo().Frame("courses-iframe");
            driver.FindElement(By.LinkText("All Access Plan")).Click();

            //sayfa yeni yüklendiği için h1 görülene kadar bekle
            WebDriverWait wait = new WebDriverWait(driver, TimeSpan.FromSeconds(8));
            wait.Until(SeleniumExtras.WaitHelpers.ExpectedConditions.ElementIsVisible(By.CssSelector("h1")));
            //frame içerisindeki h1 i getirir
            string text1 = driver.FindElement(By.CssSelector("h1")).Text;
            TestContext.Progress.WriteLine(text1);
            driver.SwitchTo().DefaultContent();
            //ana pencereye geçildiği için ana penceredeki h1 i getirir.
            TestContext.Progress.WriteLine(driver.FindElement(By.CssSelector("h1")).Text);
 ```
### dropdown ###
```csharp           
             [Test]
        public void dropdown()
        {
            IWebElement dropdown = driver.FindElement(By.CssSelector("select.form-control"));
            SelectElement s = new SelectElement(dropdown);
            s.SelectByText("Teacher");
            Thread.Sleep(2000);
            s.SelectByValue("consult");
            Thread.Sleep(2000);
            s.SelectByIndex(0);
        }
```
### radio ###
```csharp
        [Test]
        public void radio()
        {
            IList<IWebElement> rdos = driver.FindElements(By.CssSelector("input[type='radio']"));
            foreach (IWebElement radioButton in rdos)
            {
                if (radioButton.GetAttribute("value").Equals("user"))
                {
                    radioButton.Click(); 
                    
                } 
            }
           
            WebDriverWait wait = new WebDriverWait(driver, TimeSpan.FromSeconds(8));
            wait.Until(SeleniumExtras.WaitHelpers.ExpectedConditions.ElementIsVisible(By.Id("myModal")));
            IWebElement okayBtn = driver.FindElement(By.Id("okayBtn"));
            okayBtn.Click();
            //Burayı anlamadım
            Boolean result = driver.FindElement(By.Id("usertype")).Selected;
            Assert.That(result,Is.True,"usertype seçilemedi");
            Thread.Sleep(2000);
           


        }

    }
```

### test_Alert ###

```csharp
        [Test]
        public void test_Alert()
        {
            string name = "Şahin";
            driver.FindElement(By.CssSelector("#name")).SendKeys("Şahin");
            driver.FindElement(By.CssSelector("input[onclick*='displayConfirm']")).Click();
            string alertText = driver.SwitchTo().Alert().Text;
            driver.SwitchTo().Alert().Accept();//Accept or dismiss(Cancel yani iptal için) çıkan pencerede accpet ile tamam seçilir
                                               // driver.SwitchTo().Alert().Dismiss();

            //name alertText içerisinde mi değil mi test edilir
            StringAssert.Contains(name, alertText, "Name alert'de geçiyor");

        }
```
### EndToEndFlow ###
```csharp       
        [Test]
        public void EndToEndFlow()
        {
            String[] expectedProducts = { "iphone X", "Blackberry" };

            String[] actualProducts = new string[2]; 
            driver.FindElement(By.Id("username")).SendKeys("rahulshettyacademy");
            driver.FindElement(By.Name("password")).SendKeys("learning");
            driver.FindElement(By.XPath("//div[@class='form-group'][5]/label/span/input")).Click();
            driver.FindElement(By.XPath("//input[@value='Sign In']")).Click();

            WebDriverWait wait = new WebDriverWait(driver, TimeSpan.FromSeconds(2));
            wait.Until(SeleniumExtras.WaitHelpers.ExpectedConditions.ElementIsVisible(By.PartialLinkText("Checkout")));

            IList<IWebElement> cards = driver.FindElements(By.TagName("app-card"));
            foreach (IWebElement card in cards)
            {
                string title = card.FindElement(By.CssSelector(".card-title a")).Text;
                TestContext.Progress.WriteLine(title); ;

                if (expectedProducts.Contains(title))
                {
                    card.FindElement(By.CssSelector("button")).Click();
                }
            }

            driver.FindElement(By.PartialLinkText("Checkout")).Click();
            IList<IWebElement> selectedProducts = driver.FindElements(By.CssSelector("h4 a"));
            for (int i = 0; i < selectedProducts.Count; i++)
            {
                actualProducts[i] = selectedProducts[i].Text;

            }
            Assert.AreEqual(expectedProducts, actualProducts, "Sepette Ürün Hatası");
             
            driver.FindElement(By.CssSelector(".btn-success")).Click();
            driver.FindElement(By.Id("country")).SendKeys("tur");

            /*
            wait.Until(SeleniumExtras.WaitHelpers.ExpectedConditions.ElementIsVisible(By.LinkText("Turkey")));
            driver.FindElement(By.LinkText("Turkey")).Click();
            Aşağıdaki Yapı yerine bu bölüm de kullanıbilir.
             */

            wait.Until(SeleniumExtras.WaitHelpers.ExpectedConditions.ElementIsVisible(By.CssSelector(".suggestions a")));
            driver.FindElement(By.CssSelector(".suggestions a")).Click();
            driver.FindElement(By.CssSelector("label[for*='checkbox2']")).Click();
            driver.FindElement(By.CssSelector("[value='Purchase']")).Click();
           string confirmText= driver.FindElement(By.CssSelector(".alert-success")).Text;
            StringAssert.Contains("Success", confirmText);
            
        }
```
### test_AutosuggestiveDropDowns ###
```csharp      
         [Test]
        public void test_AutosuggestiveDropDowns()
        {
            driver.FindElement(By.CssSelector("#autocomplete")).SendKeys("tur");
            Thread.Sleep(3000);
            IList<IWebElement> elements = driver.FindElements(By.CssSelector(".ui-menu-item div"));
            elements.ToList().ForEach(element =>
            {
                if (element.Text.Equals("Turkey"))
                {
                    element.Click();
                }
            });

            //Yukarıdaki yapıyla aynı işi yapar
            //foreach (IWebElement element in elements)
            //{
            //    if (element.Text.Equals("Turkey"))
            //    {
            //        element.Click();
            //    }
            //}
            //Text kutusundaki değeri çalışma zamanına almak için alttaki 2. seçenek kullanılır.

            TestContext.Progress.WriteLine("Çıktı1: "+driver.FindElement(By.CssSelector("#autocomplete")).Text);
            TestContext.Progress.WriteLine("Çıktı2: " + driver.FindElement(By.CssSelector("#autocomplete")).GetAttribute("value"));
        }
```
### test_Actions ###
```csharp       
        [Test]
        public void test_Actions()
        {
            driver.Url = "https://rahulshettyacademy.com/";
            Actions a = new Actions(driver);

            //perform ile istenilen action yapılır.
            a.MoveToElement(driver.FindElement(By.CssSelector("a.dropdown-toggle"))).Perform();
            // driver.FindElement(By.XPath("//ul[@class='dropdown-menu']/li[1]/a")).Click();
            a.MoveToElement(driver.FindElement(By.XPath("//ul[@class='dropdown-menu']/li[1]/a"))).Click().Perform();
        }
```
### test_ActionsAdvance ###
```csharp        
        [Test]
        public void test_ActionsAdvance()
        {
            driver.Url = "https://demoqa.com/droppable";
            Actions a = new Actions(driver);
     
            a.DragAndDrop(driver.FindElement(By.Id("draggable")), driver.FindElement(By.Id("droppable"))).Perform();
        }
    }
```
### SortTables1 ###
```csharp  
      [Test]
        public void SortTables1()
        {
            IList<IWebElement> cbox = driver.FindElements(By.CssSelector("select option"));
            foreach (IWebElement item in cbox)
            {
                if (item.GetAttribute("value").Equals("10"))
                {
                    item.Click();

                }
            }
            Thread.Sleep(3000);
            driver.FindElement(By.XPath("//tr/th[1]/span[1]")).Click();


        }
```
### SortTables2 ###
```csharp        
        [Test]
        public void SortTables2()
        {
            ArrayList a = new ArrayList();
           
            IWebElement dropdown = driver.FindElement(By.Id("page-menu"));
            SelectElement s = new SelectElement(dropdown);
            s.SelectByText("20");
           


            //step-1 get all veggie names into arraylist A
            IList<IWebElement> vegggiNames=driver.FindElements(By.XPath("//tr/td[1]"));
            vegggiNames.ToList().ForEach(x => a.Add(x.Text));
            //step-2 Sort tihs arraylist -A
            a.Sort();
            foreach (var item in a)
            {
                TestContext.Progress.WriteLine(item);
            }
            
            //step-3 go and  click column
            Thread.Sleep(3000);

            //th[aria - label *= 'fruit name']  burada * regular expression'da contains işlemi
            //th[contains(@aria-label,'fruit name')]  yukarıdaki yapının xpath ile gösterimi
            //Aşağıdaki seçim yerine yukarıdaki 2 seçenek de kullanılabilir.

            driver.FindElement(By.XPath("//tr/th[1]/span[1]")).Click();
            //step-4 Get all veggie namse into arraylist B
            ArrayList b = new ArrayList();
            IList<IWebElement> vegggiNamesSorted = driver.FindElements(By.XPath("//tr/td[1]"));
            vegggiNamesSorted.ToList().ForEach(x => b.Add(x.Text));
            //step-5 arraylist A to B = equal

            TestContext.Progress.WriteLine(a.Equals(b)); ;

            Assert.AreEqual(a, b,"Sıralama Hatası");
        }
    }
```

### WindowHandle ###
```csharp  
 [Test]
        public void WindowHandle()
        {
           //Aşağıdaki kod mevcut window'un ıd sini verir
            string parentWindowId = driver.CurrentWindowHandle;
            driver.FindElement(By.ClassName("blinkingText")).Click();
           
            Assert.AreEqual(2, driver.WindowHandles.Count,"Window Count Hatası");
            //Aşağıdaki kod 2. Windowa geçiş yapar
            string childWindowName = driver.WindowHandles[1];
            driver.SwitchTo().Window(childWindowName);
            string realName = "RAHULSHETTY2105";
            string name1 = driver.FindElement(By.CssSelector(".clearfix b:nth-child(2)")).Text;
           
            driver.SwitchTo().Window(parentWindowId);
            driver.FindElement(By.Id("username")).SendKeys(name1);
            Assert.AreEqual(realName, name1, "Name eşleşme Hatası");
        }
        
```
