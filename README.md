# Selenium
using System;
using System.Text;
using System.Text.RegularExpressions;
using System.Threading;
using NUnit.Framework;
using OpenQA.Selenium;
using OpenQA.Selenium.Firefox;
using OpenQA.Selenium.Support.UI;

namespace SeleniumTests
{
    [TestFixture]
    public class Jd_InputWrongNumber_ExpectedOutputCorrectNumber
    {
        private IWebDriver driver;
        private StringBuilder verificationErrors;
        private string baseURL;
        private bool acceptNextAlert = true;

        [SetUp]
        public void SetupTest()
        {
            driver = new FirefoxDriver();
            baseURL = "https://www.katalon.com/";
            verificationErrors = new StringBuilder();
        }

        [TearDown]
        public void TeardownTest()
        {
            try
            {
                driver.Quit();
            }
            catch (Exception)
            {
                // Ignore errors if unable to close the browser
            }
            Assert.AreEqual("", verificationErrors.ToString());
        }

        [Test]
        public void TheJd_InputWrongNumber_ExpectedOutputCorrectNumberTest()
        {
            driver.Navigate().GoToUrl("http://127.0.0.1/webassignment/New.php");
            driver.FindElement(By.Name("firstname")).Clear();
            driver.FindElement(By.Name("firstname")).SendKeys("Neema Joseph");
            driver.FindElement(By.Name("address")).Clear();
            driver.FindElement(By.Name("address")).SendKeys("199 allen street");
            driver.FindElement(By.Name("city")).Clear();
            driver.FindElement(By.Name("city")).SendKeys("waterloo");
            driver.FindElement(By.Name("number")).Clear();
            driver.FindElement(By.Name("number")).SendKeys("1234567890");
            driver.FindElement(By.Name("email")).Clear();
            driver.FindElement(By.Name("email")).SendKeys("neema.jose@gmail.com");
            driver.FindElement(By.Name("Vehiclemake")).Clear();
            driver.FindElement(By.Name("Vehiclemake")).SendKeys("Mercedes Benz");
            driver.FindElement(By.Name("Model")).Clear();
            driver.FindElement(By.Name("Model")).SendKeys("C class");
            driver.FindElement(By.Name("Year")).Clear();
            driver.FindElement(By.Name("Year")).SendKeys("2000");
            driver.FindElement(By.XPath("(.//*[normalize-space(text()) and normalize-space(.)='Year'])[1]/following::input[2]")).Click();
            driver.FindElement(By.Name("number")).Click();
            driver.FindElement(By.Name("number")).Clear();
            driver.FindElement(By.Name("number")).SendKeys("123-123-1234");
            driver.FindElement(By.XPath("(.//*[normalize-space(text()) and normalize-space(.)='Year'])[1]/following::input[2]")).Click();
            Assert.AreEqual("123-123-1234", driver.FindElement(By.XPath("(.//*[normalize-space(text()) and normalize-space(.)='Phone :'])[1]/following::td[1]")).Text);
        }

        [Test]
        public void TheJd_InputNovalue_ExpectedOutputFilledValuesTest()
        {
            driver.Navigate().GoToUrl("http://127.0.0.1/webassignment/New.php");
            driver.FindElement(By.XPath("(.//*[normalize-space(text()) and normalize-space(.)='Year'])[1]/following::input[2]")).Click();
            driver.FindElement(By.Name("firstname")).Clear();
            driver.FindElement(By.Name("firstname")).SendKeys("Neema Joseph");
            driver.FindElement(By.Name("address")).Clear();
            driver.FindElement(By.Name("address")).SendKeys("199 allen street");
            driver.FindElement(By.Name("city")).Clear();
            driver.FindElement(By.Name("city")).SendKeys("waterloo");
            driver.FindElement(By.Name("number")).Clear();
            driver.FindElement(By.Name("number")).SendKeys("123-123-1234");
            driver.FindElement(By.Name("email")).Clear();
            driver.FindElement(By.Name("email")).SendKeys("neema.jose@gmail.com");
            driver.FindElement(By.Name("Vehiclemake")).Clear();
            driver.FindElement(By.Name("Vehiclemake")).SendKeys("Mercedes Benz");
            driver.FindElement(By.Name("Model")).Clear();
            driver.FindElement(By.Name("Model")).SendKeys("C class");
            driver.FindElement(By.Name("Year")).Clear();
            driver.FindElement(By.Name("Year")).SendKeys("2000");
            driver.FindElement(By.XPath("(.//*[normalize-space(text()) and normalize-space(.)='Year'])[1]/following::input[2]")).Click();
            Assert.AreEqual("123-123-1234", driver.FindElement(By.XPath("(.//*[normalize-space(text()) and normalize-space(.)='Phone :'])[1]/following::td[1]")).Text);
        }

        [Test]
        public void TheJd_InputJdLink_ExpectedOutputJdpageTest()
        {
            driver.Navigate().GoToUrl("http://127.0.0.1/webassignment/New.php");
            driver.FindElement(By.Name("firstname")).Click();
            driver.FindElement(By.Name("firstname")).Clear();
            driver.FindElement(By.Name("firstname")).SendKeys("Neema Joseph");
            driver.FindElement(By.Name("address")).Clear();
            driver.FindElement(By.Name("address")).SendKeys("199 allen");
            driver.FindElement(By.Name("city")).Clear();
            driver.FindElement(By.Name("city")).SendKeys("waterloo");
            driver.FindElement(By.Name("number")).Clear();
            driver.FindElement(By.Name("number")).SendKeys("123-456-7890");
            driver.FindElement(By.Name("email")).Clear();
            driver.FindElement(By.Name("email")).SendKeys("neema.jose@gmail.com");
            driver.FindElement(By.Name("Vehiclemake")).Clear();
            driver.FindElement(By.Name("Vehiclemake")).SendKeys("Ford");
            driver.FindElement(By.Name("Model")).Clear();
            driver.FindElement(By.Name("Model")).SendKeys("Mustang");
            driver.FindElement(By.Name("Year")).Clear();
            driver.FindElement(By.Name("Year")).SendKeys("2018");
            driver.FindElement(By.XPath("(.//*[normalize-space(text()) and normalize-space(.)='Year'])[1]/following::input[2]")).Click();
            driver.FindElement(By.LinkText("https://www.jdpower.com/Cars/2018/Ford/Mustang")).Click();
            Assert.AreEqual("Select a 2018 Ford Mustang trim level (6)", driver.FindElement(By.XPath("(.//*[normalize-space(text()) and normalize-space(.)='See less'])[1]/following::h2[1]")).Text);
        }

        [Test]
        public void TheJd_InputNoDataInEmailIdANdCity_ExpectedOutputCorrectEmailAndCityTest()
        {
            driver.Navigate().GoToUrl("http://127.0.0.1/webassignment/New.php");
            driver.FindElement(By.Name("firstname")).Clear();
            driver.FindElement(By.Name("firstname")).SendKeys("Neema Joseph");
            driver.FindElement(By.Name("address")).Clear();
            driver.FindElement(By.Name("address")).SendKeys("199 allen");
            driver.FindElement(By.Name("number")).Clear();
            driver.FindElement(By.Name("number")).SendKeys("123-123-1234");
            driver.FindElement(By.Name("Vehiclemake")).Clear();
            driver.FindElement(By.Name("Vehiclemake")).SendKeys("Ford");
            driver.FindElement(By.Name("Model")).Clear();
            driver.FindElement(By.Name("Model")).SendKeys("Mustang");
            driver.FindElement(By.Name("Year")).Clear();
            driver.FindElement(By.Name("Year")).SendKeys("2000");
            driver.FindElement(By.XPath("(.//*[normalize-space(text()) and normalize-space(.)='Year'])[1]/following::input[2]")).Click();
            driver.FindElement(By.Name("city")).Clear();
            driver.FindElement(By.Name("city")).SendKeys("waterloo");
            driver.FindElement(By.Name("email")).Clear();
            driver.FindElement(By.Name("email")).SendKeys("neema.jose@gmail.com");
            driver.FindElement(By.XPath("(.//*[normalize-space(text()) and normalize-space(.)='Year'])[1]/following::input[2]")).Click();
            Assert.AreEqual("neema.jose@gmail.com", driver.FindElement(By.XPath("(.//*[normalize-space(text()) and normalize-space(.)='Email :'])[1]/following::td[1]")).Text);
        }

        [Test]
        public void TheJd_InputWrongYear_ExpectedOutput500ErrorTest()
        {
            driver.Navigate().GoToUrl("http://127.0.0.1/webassignment/New.php");
            driver.FindElement(By.Name("firstname")).Clear();
            driver.FindElement(By.Name("firstname")).SendKeys("Neema Joseph");
            driver.FindElement(By.Name("address")).Clear();
            driver.FindElement(By.Name("address")).SendKeys("199 allen");
            driver.FindElement(By.Name("city")).Clear();
            driver.FindElement(By.Name("city")).SendKeys("waterloo");
            driver.FindElement(By.Name("number")).Clear();
            driver.FindElement(By.Name("number")).SendKeys("123-123-1234");
            driver.FindElement(By.Name("email")).Clear();
            driver.FindElement(By.Name("email")).SendKeys("neema.jose@gmail.com");
            driver.FindElement(By.Name("Vehiclemake")).Clear();
            driver.FindElement(By.Name("Vehiclemake")).SendKeys("Ford");
            driver.FindElement(By.Name("Model")).Clear();
            driver.FindElement(By.Name("Model")).SendKeys("Mustang");
            driver.FindElement(By.Name("Year")).Clear();
            driver.FindElement(By.Name("Year")).SendKeys("1990");
            driver.FindElement(By.XPath("(.//*[normalize-space(text()) and normalize-space(.)='Year'])[1]/following::input[2]")).Click();
            driver.FindElement(By.LinkText("https://www.jdpower.com/Cars/1990/Ford/Mustang")).Click();
            Assert.AreEqual("500 - INTERNAL SERVER ERROR", driver.FindElement(By.XPath("/html/body/div[3]/section/div/main/div[1]/div[1]/h1")).Text);
        }

        private bool IsElementPresent(By by)
        {
            try
            {
                driver.FindElement(by);
                return true;
            }
            catch (NoSuchElementException)
            {
                return false;
            }
        }

        private bool IsAlertPresent()
        {
            try
            {
                driver.SwitchTo().Alert();
                return true;
            }
            catch (NoAlertPresentException)
            {
                return false;
            }
        }

        private string CloseAlertAndGetItsText()
        {
            try
            {
                IAlert alert = driver.SwitchTo().Alert();
                string alertText = alert.Text;
                if (acceptNextAlert)
                {
                    alert.Accept();
                }
                else
                {
                    alert.Dismiss();
                }
                return alertText;
            }
            finally
            {
                acceptNextAlert = true;
            }
        }
    }
}
