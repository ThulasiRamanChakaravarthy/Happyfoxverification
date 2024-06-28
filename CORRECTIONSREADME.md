Common changes need to be implemented:

Change need to use dynamic wait instead of sleep.
use logger.info instead of System.out.println.
Method and variable conversation always need to in camelCase 



Comments on AdminPortalTest1 and AdminPortalTest2:

1.Method and variable conversation always need to in camelCase 
#String methodName = new Object(){}.getClass().getEnclosingMethod().getName(); same for className.
Replace these to the places where it used in the script.

2. Using throwable in the chatch block will catch all type of exception ( like outOfMemoryError) instead use Exception e to catch the specific exception.
3. import org.seleniumhq.jetty9.util.log.LoggerLog is specified for jetty not for the general applications so we can use log4j instead of it also import log4j dependencies and import import org.apache.logging.log4j.LogManager, import org.apache.logging.log4j.Logger;.
4. Using e.printStackTrace(); in the catch which is not able to configured to log for diffirent file,remoteservers etc.. use logger.error for errors and logger.info instead of system.println and use  private static final Logger logger = LogManager.getLogger(classname.class)for using logger methods like error,info etc.. which provides more versatile logs.



adminportaltest1st page: 

 remove sleep and use dynamic wait
@FindBy(xpath = "//button[@class='hf-mod-create']")---- line 50-change the xpath the provided one does not makes any meaningful class details.

@FindBy(xpath = "//span[@class='hf-top-bar_title_text hf-font-light']") line 22change the xpath the provided one does not makes any meaningful class details.

String Status = "//div[contains(text(),'"+xpath+"')]//following::td[3]"; line 122 need to read the table dynamically
@FindBy(xpath = "/html[1]/body[1]/div[3]/div[1]/section[1]/section[1]/div[1]/div[1]/section[1]/div[1]/div[1]/div[2]/div[1]/div[2]/div[1]/table[1]/tbody[1]/tr[9]/td[2]") line 136 try to fetch relative xpath this instead of hardcoding absolute.


@FindBy(xpath = "/html[1]/body[1]/div[3]/div[1]/header[1]/div[2]/nav[1]/div[7]/div[1]/div[1]")- same as line 136

String priority = "//span[contains(text(),'"+xpath+"')]//following::td[3]";line 177 ---need to read the table dynamically
before clicking the element make sure that element is visible first.


supportportalpage.java -

@FindBy(xpath = "//div[@class='cke_wysiwyg_div cke_reset cke_enable_context_menu cke_editable cke_editable_themed cke_contents_ltr cke_show_borders']")  - line 35 change the xpath the provided one does not makes any meaningful class details.

adminportaltest2st page: @FindBy(xpath = "//span[@class='hf-top-bar_title_text hf-font-light']") line 18--- space in the xpath may cause an issue check with it.

@FindBy(xpath = "//a[@data-test-id='ticket-side-pane-contact-name']//following::div[1]/div[1]/span[1]") --line 52 Need to be change the hard coded one.

 @FindBy(xpath = "//div[contains(text(),'status')]//following::div[1]") ---> line 61 Need to be change the hard coded one.
 
@FindBy(xpath = "//div[contains(text(),'status')]//following::div[1]//following::span[1]/div/div/div/div[2]") --line 71Need to be change the hard coded one.

@FindBy(xpath = "//input[@placeholder='Search more Canned Actions']") --- line 100 space in the xpath may cause  an issue check with it.

Login page.java--

Use @FindBy annotations missing.
 if (!driver.getCurrentUrl().equals("https://www.happyfox.com/home")) -- line 41 URL not supposed to be hardcoded.

Basetest.java--

System.setProperty("webdriver.chrome.driver","C:\\Users\\test\\Desktop\\D drive\\automation\\Chrome driver\\chromedriver.exe");-- line 15 not supposed to be hard coded.
driver.close();-- line 22 Unesseary inclution.
