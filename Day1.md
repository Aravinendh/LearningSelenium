# Selenium Learning - Day 1

## 📌 Overview

This session covers:

- Basic Selenium setup using Java
- Launching a browser using ChromeDriver
- Locating web elements
- Performing actions (sendKeys, click)
- Using TestNG annotations
- Validating results using assertions

---

## 🧪 Test Class: `SeleniumTest`

```java
package part1;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.testng.Assert;
import org.testng.annotations.AfterClass;
import org.testng.annotations.BeforeClass;
import org.testng.annotations.Test;

public class SeleniumTest {

    WebDriver driver;

    @BeforeClass
    public void setUp() {
        driver = new ChromeDriver();
        driver.manage().window().maximize();
        driver.get("https://opensource-demo.orangehrmlive.com/web/index.php/auth/login");
    }

    @AfterClass
    public void tearDown() {
        // driver.quit();
    }

    @Test
    public void loggingIn() throws InterruptedException {

        Thread.sleep(2000);

        WebElement username = driver.findElement(By.name("username"));
        username.sendKeys("Admin");

        Thread.sleep(3000);

        var password = driver.findElement(By.name("password"));
        password.sendKeys("admin123");

        Thread.sleep(3000);

        driver.findElement(By.tagName("button")).click();

        Thread.sleep(3000);

        String actualResult = driver.findElement(By.tagName("h6")).getText();
        String expectedResult = "Dashboard";

        Assert.assertEquals(actualResult, expectedResult);
        // Assert.assertNotEquals(actualResult, expectedResult);
    }
}
```

---

## ⚙️ Key Concepts Learned

### 1. WebDriver

- Interface used to control the browser
- `ChromeDriver` is a concrete implementation for Chrome

---

### 2. TestNG Annotations

| Annotation     | Purpose                                   |
|----------------|-------------------------------------------|
| `@BeforeClass` | Runs before all test methods (setup)      |
| `@AfterClass`  | Runs after all test methods (cleanup)     |
| `@Test`        | Marks a test method                      |

---

### 3. Browser Actions

```java
driver = new ChromeDriver();          // Launch browser
driver.manage().window().maximize();  // Maximize window
driver.get("URL");                    // Open website
```

---

### 4. Locating Elements

```java
driver.findElement(By.name("username"));
driver.findElement(By.tagName("button"));
```

- `By.name()` → Locate using name attribute  
- `By.tagName()` → Locate using HTML tag  

---

### 5. Performing Actions

```java
username.sendKeys("Admin");   // Enter text
button.click();               // Click element
```

---

### 6. Wait Handling (Temporary)

```java
Thread.sleep(2000);
```

- Pauses execution for given milliseconds  
- Not recommended for real projects (use Explicit Wait later)

---

### 7. Assertions (Validation)

```java
Assert.assertEquals(actualResult, expectedResult);
```

- Verifies if actual output matches expected output  
- Test passes if both values are equal

---

## 🔄 Test Flow

1. Open browser
2. Navigate to login page
3. Enter username
4. Enter password
5. Click login
6. Validate dashboard is displayed

---

## ⚠️ Notes

- `Thread.sleep()` is used only for learning/demo
- `driver.quit()` is commented → browser stays open after test
- Used simple locators (`name`, `tagName`)

---

## ✅ Outcome

- Successfully automated login functionality
- Verified login using assertion
- Understood basic Selenium + TestNG workflow

---

## 🚀 Next Step (Suggested)

- Learn **XPath & CSS Selectors**
- Replace `Thread.sleep()` with **WebDriverWait**
- Understand **Page Object Model (POM)**

---

