## Отчёт о проверке Credit Card Number Validator

#### 26.08.2020-26.08.2020 было проведено функциональное тестирование программы Credit Card Number Validator
#### На тестирование затрачено 0,5 ч.

### В результате тестирования выявлены следующие дефекты:
Программа считает валидными только 16-ти значные номера банковских карт

### В процессе тестирования использовались следующие артефакты:
* IntelliJ IDEA
 * Код оставшийся от предыдущего программиста
  ```Java
public class Main {
    public static void main(String[] args) {
      // TODO: подставлять номер карты нужно сюда между двойными кавычками, без пробелов
      String number = "5351719427810741";
      System.out.println(String.format("Result is %s", isValidCardNumber(number) ? "OK" : "FAIL"));
    }
  
    public static boolean isValidCardNumber(String number) {
      if (number == null) {
        return false;
      }
  
      if (number.length() != 16) {
        return false;
      }
  
      long result = 0;
      for (int i = 0; i < number.length(); i++) {
        int digit;
        try {
          digit = Integer.parseInt(number.charAt(i) + "");
        } catch (NumberFormatException e) {
          return false;
        }
  
        if (i % 2 == 0) {
          digit *= 2;
          if (digit > 9) {
            digit -= 9;
          }
        }
        result += digit;
      }
  
      return (result != 0) && (result % 10 == 0);
    }
  }
  ```
#### В качестве тестовых данных использовались данные сервиса, который генерирует валидные намера карт [freeformatter.com](https://www.freeformatter.com/credit-card-number-generator-validator.html)

![image](https://user-images.githubusercontent.com/67522974/91319185-c1d83600-e7c4-11ea-910f-5f5ed0bfdb01.png)

### Тестирование производилось в следующем окружении:
* Windows 10 Professional 64х
* Версия Java "11.0.8"
* Google Chrome Версия 84.0.4147.135