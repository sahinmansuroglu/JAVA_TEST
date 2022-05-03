> projedeki tüm testleri çalıştırır.

dotnet test CSharpSelenFrameworkNet5.csproj

> Smoke kategorisindeki testleri çalıştırır

dotnet test CSharpSelenFrameworkNet5.csproj --filter TestCategory=Smoke

> Regression kategorisindeki testleri çalıştırır

dotnet test CSharpSelenFrameworkNet5.csproj --filter TestCategory=Regression

> Browser name'i terminalden alma

 dotnet test --% --filter TestCategory=Regression -- TestRunParameters.Parameter(name=\"browserName\", value=\"Chrome\")
 
 > Jenkins de parametre oluşturup gönderirken bu şekilde çalıştı
 dotnet test --filter TestCategory=%category% -- TestRunParameters.Parameter(name=\"browserName\", value=\""%browserName%"\")
