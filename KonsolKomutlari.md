> projedeki tüm testleri çalıştırır.

dotnet test CSharpSelenFrameworkNet5.csproj

> Smoke kategorisindeki testleri çalıştırır

dotnet test CSharpSelenFrameworkNet5.csproj --filter TestCategory=Smoke

> Regression kategorisindeki testleri çalıştırır

dotnet test CSharpSelenFrameworkNet5.csproj --filter TestCategory=Regression
