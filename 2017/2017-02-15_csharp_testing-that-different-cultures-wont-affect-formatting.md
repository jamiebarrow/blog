# 2017-02-15 C# - Testing that different cultures won't affect formatting

tags: c#, CultureInfo, unit testing

Ever worked on a system where you write code and test it and it all works perfect, but then maybe a unit test starts failing on a build server, or maybe a report looks wrong to the consumers of the report, all because it formatted a number to `"12345,67"` instead of `"12345.67"`?

This tip will help you.

First, lets assume we have this code:


```csharp
public class ReportFormatter
{
  public string Format(decimal value)
  {
    return value.ToString();
  }
}
```

And a nice little unit test for it:


```csharp
[TestClass]
public sealed class ReportFormatterTest
{
  [TestMethod]
  public void Format()
  {
    var sut = new ReportFormatter();
    
    var result = sut.Format(12345.67M);
    
    Assert.AreEqual("12345.67", result);
  }
}
```

This works perfectly fine. Lets even imagine that all our machines all have the same setup, and all are set to use the same regional settings. Great, nothing should ever break.

Until maybe Microsoft releases a patch to Windows that changes our regional settings to be "correct" - in fact, [South Africa should be using a comma as a separator](https://www.sadev.co.za/content/how-correctly-format-currency-south-africa)... even though none of us use this standard :D

So then it breaks our code, and our business rules that disagree with it.

Well, the good news is we can change the regional settings of the running thread, by changing its CultureInfo details. Here is a little utility class to do so:


```csharp
public class TemporaryCultureSwitch : IDisposable
{
  private readonly CultureInfo _originalCulture;
  private readonly CultureInfo _originalUICulture;
  
  public TemporaryCultureSwitch(CultureInfo cultureInfo)
  {
    _originalCulture = Thread.CurrentThread.CurrentCulture;
    _originalUICulture = Thread.CurrentThread.CurrentUICulture;
    
    Thread.CurrentThread.CurrentCulture = cultureInfo;
    Thread.CurrentThread.CurrentUICulture = cultureInfo;
  }
  
  public TemporaryCultureSwitch(string cultureName) : this(new CultureInfo(cultureName)) { }
  
  public void Dispose()
  {
    Thread.CurrentThread.CurrentCulture = _originalCulture;
    Thread.CurrentThread.CurrentUICulture = _originalUICulture;
  }
}
```

We can now update our test to be a bit more specific:


```csharp
[TestMethod]
public void FormatShouldNotBeAffectedByCultureChanges()
{
  var culture = new CultureInfo("en-ZA");
  culture.NumberFormat.NumberDecimalSeparator = ",";
  using (new TemporaryCultureSwitch(culture))
  {
    var sut = new ReportFormatter();
    
    var result = sut.Format(12345.67M);
    
    Assert.AreEqual("12345.67", result);
  }
}
```

Now we have a test that will fail consistently! Time to fix the code. One way of doing this is realizing that there is an overload of Decimal.ToString that takes in a CultureInfo object. We actually can use the InvariantCulture as below:


```csharp
public string Format(decimal value)
{
  return value.ToString(CultureInfo.InvariantCulture);
}

```

The test passes and we now know for sure that regional settings won't affect our code.

