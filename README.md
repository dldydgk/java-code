# java-code
Java 코드의 클래스 활용

## 1.  클래스 사용
``` java
class Account1 {
    public static double valueOfSupply; //공급가액
    public static double vatRate = 0.1; //부가세
    public static double getVat() { 
        return valueOfSupply * vatRate; //공급가액 * 부가세
    }
    public static double getTotal() {
        return valueOfSupply + getVat();//공급가액 (공급가액 * 부가세)
    }
}
```
### 1단계 코드
``` java
public class Accounting {
    public static void main(String[] args) {
        Account at = new Account();
        at.valueOfSupply = 10000;
        System.out.println(at.valueOfSupply);
        at.valueOfSupply = 20000;
        System.out.println(at.valueOfSupply);
        System.out.println("------------------");
        at.valueOfSupply = 10000;
        System.out.println(at.getVat());
        at.valueOfSupply = 20000;
        System.out.println(at.getVat());
        System.out.println("------------------");
        at.valueOfSupply = 10000;
        System.out.println(at.getTotal());
        at.valueOfSupply = 20000;
        System.out.println(at.getTotal());

    }
}
class Account {
    public static double valueOfSupply;
    public static double vatRate = 0.1;
    public static double getVat() {
        return valueOfSupply * vatRate;
    }
    public static double getTotal() {
        return valueOfSupply + getVat();
    }
}
```
1. 이 코드는 공급가액과 공급가액 * 부가세, 공급대가를 출력할 때마다 valueOfSupply의 값을 계속 바꿔서 출력한
다.
2. 출력하고자 하는 공급가액의 수가 늘어날 때마다 코드의 길이가 급격하게 늘어난다.

#### 2단계 코드
``` java
public class Accounting1 {
    public static void main(String[] args) {
        Account2 at1 = new Account1();
        Account2 at2 = new Account1();
        at1.valueOfSupply = 10000;
        at2.valueOfSupply = 20000;
        System.out.println(at1.valueOfSupply);
        System.out.println(at2.valueOfSupply);
        System.out.print("\n");
        System.out.println(at1.getVat());
        System.out.println(at2.getVat());
        System.out.print("\n");
        System.out.println(at1.getTotal());
        System.out.println(at2.getTotal());

    }
}
class Account1 {
    public  double valueOfSupply;
    public static double vatRate = 0.1;
    public double getVat() {
        return valueOfSupply * vatRate;
    }
    public double getTotal() {
        return valueOfSupply + getVat();
    }
}
```
1. 두 개의 인스턴스 at1 과 at2를생성하였다
2. at1의 valueOfSupply 는 10000으로 at2의 valueOfSupply 는 20000으로 초기화 시킨다.
3. System.out.println(at1.valueOfSupply)는 at1 인스턴스에 들어있는 10000을 출력하고 System.out.println(at2.valueOfSu pply)는 at2 인스턴스에 들어있는 20000을 출력한다.
4. 공급가액 개수가 늘어나도 새로운 인스턴스를 생성하여 그 인스턴스에 있는 valueOfSupply 변수에 공급가액을 저장하여 출력하고자 하는 공급가액이 달라져도 그 공급가액이 저장된 인스턴스를 사용하여 valueOfSupply 변수를 바꾸지 않아도 출력할 수 있다 

### 3단계 코드
``` java
public class Accounting3 {
    public static void main(String[] args) {
        Account3 at1 = new Account3(10000);
        Account3 at2 = new Account3(20000);
        System.out.println(at1.valueOfSupply);
        System.out.println(at2.valueOfSupply);
	System.out.print("\n");
        System.out.println(at1.getVat());
        System.out.println(at2.getVat());
        System.out.print("\n");
        System.out.println(at1.getTotal());
        System.out.println(at2.getTotal());

    }
}
class Account3 {
    public double valueOfSupply;
    public static double vatRate = 0.1;
    public Account3(double valueOfSupply){
        this.valueOfSupply = valueOfSupply;
    }
    public double getVat() {
        return valueOfSupply * vatRate;
    }
    public double getTotal() {
        return valueOfSupply + getVat();
    }
}
```
1. 이 코드는 class에 생성자 메소드를 만들어서 인스턴스를 생성할 때 인수를 받아 class의 valueOfSupply에 바로 초기화 시킨다.
2. this.valueOfSupply는 클래스의 필드에 있는 valueOfSupply를 뜻하고 valueOfSupply는 생성자 메소드에 있는 매개변수를 의미한다.
3. 이 코드가 가장 보기 편하고 효율적인 코드다
 

### 최종 출력값
![image](https://github.com/dldydgk/java-code/assets/126844590/b7608fb0-53e7-4e18-85f5-b03a40ccf177)




