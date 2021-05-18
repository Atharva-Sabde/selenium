- Resources:

    [https://www.youtube.com/watch?v=rZv5duo8mjc&list=PLL34mf651faPB-LyEP0-a7Avp_RHO0Lsm&index=3](https://www.youtube.com/watch?v=rZv5duo8mjc&list=PLL34mf651faPB-LyEP0-a7Avp_RHO0Lsm&index=3)

Selenium is a web automation framework.

Other web automation frameworks do not support dynamic websites.
![image](https://user-images.githubusercontent.com/67774570/118701626-905f3900-b831-11eb-85e4-47bb4f8fd77b.png)
![image](https://user-images.githubusercontent.com/67774570/118701610-8b01ee80-b831-11eb-8ad8-602b6722ab04.png)


```java
//#run java
 
import io.github.bonigarcia.wdm.WebDriverManager;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.chrome.ChromeOptions;
 
import java.util.Arrays;
import java.util.List;
import java.util.Scanner;
 
import static java.lang.Thread.sleep;
 
public class Yo {
    public static void main(String[]args)
    {
 
 
        List<String> links = Arrays.asList("https://www.linkedin.com/posts/sidd-oo_100daysofcode-devsnestday21-devsnest6monthschallenge-activity-6789459261542973440-x7FX/",
                "https://www.linkedin.com/posts/ross-nelson-32493684_devsnest6monthschallenge-devsnestday21-slowandsteady-activity-6788661474186338304-Dx0z");
        WebDriverManager.chromedriver().setup();
        ChromeOptions options = new ChromeOptions();
        options.addArguments("user-data-dir={}\\driver_data".format(System.getProperty("user.dir")));
        WebDriver driver = new ChromeDriver(options=options);
        driver.get("https://linkedin.com");
        while(!new Scanner(System.in).next().equals("1")){
            System.out.println("press 1 when signed in: ");
        }
        for(String link : links){
            try{
                System.out.println("processing link");;
                driver.get(link);
                sleep(2000);
                WebElement el = driver.findElement(By.className("react-button__trigger"));
                if("false".equals(el.getAttribute("aria-pressed"))){
                    System.out.println("liking");
                    el.click();
                    System.out.println("liked");
                    sleep(1);
                }
                else {
                    System.out.println("alread processed link " + link);
                }
            } catch (Exception e) {
                e.printStackTrace();
            }
        }
    }
 
}
 
 
-----------------------------
		<dependency>
            <groupId>io.github.bonigarcia</groupId>
            <artifactId>webdrivermanager</artifactId>
            <version>4.4.3</version>
            <scope>test</scope>
        </dependency>
        <!-- https://mvnrepository.com/artifact/org.seleniumhq.selenium/selenium-java -->
        <dependency>
            <groupId>org.seleniumhq.selenium</groupId>
            <artifactId>selenium-java</artifactId>
            <version>3.141.59</version>
        </dependency>
```



![image](https://user-images.githubusercontent.com/67774570/118701746-b2f15200-b831-11eb-94da-ba0e2d507599.png)
