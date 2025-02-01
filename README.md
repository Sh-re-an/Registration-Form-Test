# Registration-Form-Test
Maven dependency code - 
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>org.example</groupId>
    <artifactId>second-test</artifactId>
    <version>1.0-SNAPSHOT</version>
    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <configuration>
                    <source>11</source>
                    <target>11</target>
                </configuration>
            </plugin>
        </plugins>
    </build>


    <dependencies>
        <dependency>
            <groupId>org.seleniumhq.selenium</groupId>
            <artifactId>selenium-java</artifactId>
            <version>4.9.1</version>
        </dependency>


        <!-- https://mvnrepository.com/artifact/org.testng/testng -->
        <dependency>
            <groupId>org.testng</groupId>
            <artifactId>testng</artifactId>
            <version>7.5.1</version>
            <scope>test</scope>
        </dependency>


    </dependencies>

</project>



Login Page Test code-
import org.openqa.selenium.WebElement;
import org.openqa.selenium.By;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;
import org.openqa.selenium.support.ui.Select;
import org.testng.Assert;


public class LoginPageTest {

      public WebDriver driver;

      @Test(priority = 1)
    public void RegisterWithValidCredentials() {
            //Opening Chrome Browser instance
         System.setProperty("webdriver.chrome.driver", "C:\\Users\\DELL\\Downloads\\chromedriver-win32\\chromedriver-win32\\chromedriver.exe");
          driver = new ChromeDriver();
         driver.get("https://rahulnxttrends.ccbp.tech/");

         //Finding username input element.
        WebElement namefield = driver.findElement(By.name("name"));
        namefield.sendKeys("rahul");

        //Finding email input element.
        WebElement emailField = driver.findElement(By.name("email"));
        emailField.sendKeys("rahul@example.com");

        //Finding password element.
        WebElement passwordEl = driver.findElement(By.name("password"));
        passwordEl.sendKeys("rahul@2021");

        //Finding male radio button.
        WebElement genderField = driver.findElement(By.id("male"));
        genderField.click();

        //Find the country dropdown element.
        WebElement countryDropdown = driver.findElement(By.tagName("Select"));
        Select countrySelect = new Select(countryDropdown);

        //Select an option by visible text.
        countrySelect.selectByVisibleText("India");

        //Select the checkbox.
        WebElement termsAndConditions = driver.findElement(By.id("terms"));
        termsAndConditions.click();

        //Submit the registration form.
        WebElement registerButton = driver.findElement(By.id("submitBtn"));
        registerButton.submit();
        //Navigate to Login Page.
        WebElement loginPageEl = driver.findElement(By.linkText("Log in"));
        loginPageEl.click();

        String loginPageUrl = "https://rahulnxttrends.ccbp.tech/login";

        //Get current URL.
        String currentUrl = driver.getCurrentUrl();

        //Verify the navigation to login page.
        if (currentUrl.equals(loginPageUrl)) {
            System.out.println("Navigated to login page");
        }
        else {
            System.out.println("Failed to open login page");
        }


    }

    @Test(priority = 2)
    public void RegisterWithInvalidCredentials() {
        //Opening Chrome Browser instance
        System.setProperty("webdriver.chrome.driver", "C:\\Users\\DELL\\Downloads\\chromedriver-win32\\chromedriver-win32\\chromedriver.exe");
         driver = new ChromeDriver();
        driver.get("https://rahulnxttrends.ccbp.tech/");

        //Finding username input element.
        WebElement namefield = driver.findElement(By.name("name"));
        namefield.sendKeys("rahul4587");

        //Finding email input element.
        WebElement emailField = driver.findElement(By.name("email"));
        emailField.sendKeys("rahulexample");

        //Finding password element.
        WebElement passwordEl = driver.findElement(By.name("password"));
        passwordEl.sendKeys("rahul2021");

        //Finding male radio button.
        WebElement genderField = driver.findElement(By.id("femaley"));
        genderField.click();

        //Find the country dropdown element.
        WebElement countryDropdown = driver.findElement(By.tagName("Select"));
        Select countrySelect = new Select(countryDropdown);

        //Select an option by visible text.
        countrySelect.selectByVisibleText("Thailandsa");

        //Select the checkbox.
        WebElement termsAndConditions = driver.findElement(By.id("terms"));
        termsAndConditions.click();

        //Submit the registration form.
        WebElement registerButton = driver.findElement(By.id("submitBtn"));
        registerButton.submit();
        //Navigate to Login Page.
        WebElement loginPageEl = driver.findElement(By.linkText("Log in"));
        loginPageEl.click();

        String loginPageUrl = "https://rahulnxtrendz.ccbp.tech/login";

        //Get current URL.
        String currentUrl = driver.getCurrentUrl();

        //Verify the navigation to login page.
        if (currentUrl.equals(loginPageUrl)) {
            System.out.println("Navigated to login page");
        } else {
            System.out.println("Failed to open login page");
        }


    }
        @AfterMethod
        public void tearDown() {
        // Quit the login page.
            driver.quit();

    }


}





TestNG.XML FILE - This is for ensuring parallel testing
<!DOCTYPE suite SYSTEM "https://testng.org/testng-1.0.dtd">
<suite name= "NxtTrendsTestSuite" parallel="classes" thread-count="1">
    <test name="LoginPageTest1">
        <classes>
            <class name="LoginPage.LoginPageTest"/>
        </classes>
    </test>
</suite>


