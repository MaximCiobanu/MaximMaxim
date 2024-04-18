package ui;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

public class BookSearch {
    public static void main(String[] args) {
        // Specificăm locația driverului Chrome
        System.setProperty("webdriver.chrome.driver", "C:\\path\\to\\chromedriver.exe");

        // Inițializăm un obiect WebDriver
        WebDriver driver = new ChromeDriver();

        // Navigăm către pagina de căutare a cărților
        driver.get("http://example.com/booksearch");

        // Exemplu de Absolute XPath pentru primul element din lista de cărți
        WebElement firstBookAbsolute = driver.findElement(By.xpath("/html/body/div/div[2]/ul/li[1]"));

        // Exemplu de Relative XPath pentru titlul primei cărți din listă
        WebElement firstBookTitleRelative = driver.findElement(By.xpath("//ul[@class='book-list']/li[1]//h2"));

        // Exemplu de starts-with pentru a selecta toate cărțile cu autori care încep cu "John"
        WebElement johnAuthors = driver.findElement(By.xpath("//ul[@class='book-list']/li[starts-with(div[@class='author'], 'John')]"));

        // Exemplu de contains pentru a selecta toate cărțile care conțin în titlu cuvântul "Java"
        WebElement javaBooks = driver.findElement(By.xpath("//ul[@class='book-list']/li[contains(h2, 'Java')]"));

        // Exemplu de text() pentru a selecta toate cărțile care au autorul "Jane Doe"
        WebElement janeDoeBooks = driver.findElement(By.xpath("//ul[@class='book-list']/li[div[@class='author']/text()='Jane Doe']"));

        // Exemplu de and pentru a selecta cărțile cu titlul "Java Programming" și autorul "John Smith"
        WebElement javaProgrammingByJohnSmith = driver.findElement(By.xpath("//ul[@class='book-list']/li[h2='Java Programming' and div[@class='author']='John Smith']"));

        // Exemplu de or pentru a selecta cărțile cu titlul "Java Programming" sau "Python Programming"
        WebElement javaOrPythonProgramming = driver.findElement(By.xpath("//ul[@class='book-list']/li[h2='Java Programming' or h2='Python Programming']"));

        // Închidem browser-ul
        driver.quit();
    }
}
