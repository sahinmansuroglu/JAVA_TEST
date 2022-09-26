### Get product list and print product name using  and foreach  and stream

```java
 public static  void main(String [] args) throws InterruptedException {
        WebDriverManager.chromedriver().setup();
        WebDriver driver=new ChromeDriver();
        driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));
        driver.get("https://rahulshettyacademy.com/client");
        driver.findElement(By.cssSelector("#userEmail")).sendKeys("test12@test.com");
        driver.findElement(By.cssSelector("#userPassword")).sendKeys("Test1234");
        driver.findElement(By.cssSelector("input#login")).click();

        List<WebElement> products= driver.findElements(By.cssSelector(".col-lg-4.col-md-6.col-sm-10.offset-md-0.offset-sm-1.mb-3.ng-star-inserted"));
        for (WebElement element : products  ) {
            System.out.println(element.findElement(By.cssSelector("h5")).getText());
        }
        
        products.forEach(x->{
            System.out.println(x.findElement(By.cssSelector("h5")).getText());
        });
        Thread.sleep(5000);
        Thread.sleep(5000);
}
```

### Get product by filter
