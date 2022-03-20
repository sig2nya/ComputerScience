```java
import java.util.regex.Pattern;
public class Regex{
  public static void main(String args[]){
    String pattern = "^[0-9]*$"
    String var = "123456789";
    
    boolean check = Pattern.matches(pattern, var);
    System.out.println(check);
  }
}
```
