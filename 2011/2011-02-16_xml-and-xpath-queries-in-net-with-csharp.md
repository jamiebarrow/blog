# 2011-02-16 Xml and XPath queries in .NET with C#"

tags: C#, namespaces, XML, XPath

Querying XML should be easy using XPath. But for some reason I had an issue where for the life of me I was sure the XPath should have been returning something, but was returning nothing. The issue turned out to be because I wasn't specifying namespaces.

The below Unit Tests illustrate the ways that work and don't work (you will need a reference to System.Xml in the project).

```csharp
using System.Xml;
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace XmlTestProject
{
    [TestClass]
    public class XmlTests
    {
        ///
        /// A test to see if we can query using XPath correctly when there is no namespace defined.
        /// This test passes.
        ///
        [TestMethod]
        [TestCategory("Unit")]
        public void CanQueryWhenNoNamespace()
        {
            string xml = @"Jamesj@miebarrow.comjames@work.co.za";

            string emailsXpath = "//email";

            XmlDocument doc = new XmlDocument();
            doc.LoadXml(xml);

            XmlNodeList emails = doc.SelectNodes(emailsXpath);

            Assert.AreEqual(2, emails.Count, "There should be exactly two nodes retrieved");
            XmlNode emailNode = emails.Item(0);
            Assert.AreEqual("email", emailNode.Name, "The first node should be an email element");
            Assert.AreEqual("j@miebarrow.com", emailNode.InnerText, "The inner text of the email element should be the email address");
        }

        ///
        /// A test to see if we can query using XPath correctly when there is a namespace defined,
        /// using the same method as when no namespace is defined.
        /// This test fails.
        ///
        [TestMethod]
        public void CanQueryWhenDefaultNamespace()
        {
            string xml = @"Jamesj@miebarrow.comjames@work.co.za";

            string emailsXpath = "//email";

            XmlDocument doc = new XmlDocument();
            doc.LoadXml(xml);

            XmlNodeList emails = doc.SelectNodes(emailsXpath);

            Assert.AreEqual(2, emails.Count, "There should be exactly two nodes retrieved");
            XmlNode emailNode = emails.Item(0);
            Assert.AreEqual("email", emailNode.Name, "The first node should be an email element");
            Assert.AreEqual("j@miebarrow.com", emailNode.InnerText, "The inner text of the email element should be the email address");
        }

        ///
        /// A test to see if we can query using XPath correctly when there is a namespace defined,
        /// by providing the namespaces to the SelectNodes function, and explicitly using the
        /// namepsace prefix in our XPath expression.
        /// This test passes, and is the correct way to achieve our goal.
        ///
        [TestMethod]
        public void CanQueryWhenDefaultNamespaceAndUsingNamespaceManager()
        {
            string xml = @"Jamesj@miebarrow.comjames@work.co.za";

            string emailsXpath = "//jb:email";

            XmlDocument doc = new XmlDocument();
            doc.LoadXml(xml);

            XmlNamespaceManager namespaceManager = new XmlNamespaceManager(doc.NameTable);
            namespaceManager.AddNamespace("jb", "http://jamiebarrow.com/2011/02/16");

            XmlNodeList emails = doc.SelectNodes(emailsXpath, namespaceManager);

            Assert.AreEqual(2, emails.Count, "There should be exactly two nodes retrieved");
            XmlNode emailNode = emails.Item(0);
            Assert.AreEqual("email", emailNode.Name, "The first node should be an email element");
            Assert.AreEqual("j@miebarrow.com", emailNode.InnerText, "The inner text of the email element should be the email address");
        }

        ///
        /// A test to see what happens when we specify a default namespace, and also a different
        /// namespace, and perform a query using the non-default namespace.
        /// This test passes.
        /// Note that the element we retrieve is fully qualified with a namespace prefix, whereas
        /// in previous examples, the elements were part of the default namespace and had were
        /// not qualified with a prefix.
        ///
        [TestMethod]
        public void CanQueryWhenDefaultNamespaceAndUsingNamespaceManagerWithMixedNamespaces()
        {
            string xml = @"Jamesj@miebarrow.comjames@work.co.zaanother@example.com";

            string emailsXpath = "//test:email";

            XmlDocument doc = new XmlDocument();
            doc.LoadXml(xml);

            XmlNamespaceManager namespaceManager = new XmlNamespaceManager(doc.NameTable);
            namespaceManager.AddNamespace("jb", "http://jamiebarrow.com/2011/02/16");
            namespaceManager.AddNamespace("test", "http://test.org/");

            XmlNodeList emails = doc.SelectNodes(emailsXpath, namespaceManager);

            Assert.AreEqual(1, emails.Count, "There should be exactly two nodes retrieved");
            XmlNode emailNode = emails.Item(0);
            Assert.AreEqual("test:email", emailNode.Name, "The first node should be an email element, qualified by a namespace prefix since we are querying the non-default namespace");
            Assert.AreEqual("another@example.com", emailNode.InnerText, "The inner text of the email element should be the email address");
        }
    }
}
```
