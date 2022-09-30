# android

## JAVA

``` java 
public class Car {  // 클래스
  String color;      // 필드
  int speed = 0;     
  
  static int carCount = 0; // 정적 필드 클래스 자체에서 사용하는 변수
  final static int MAXSPEED = 200; // 상수 필드 정적 필드에 초기값을 입력하고 final을 앞에 붙임
  
  static int currentCarCount() {  // 정적 메소드
    return carCount;
  }
  
  Car(String color, int speed) {  // 생성자
    this.color = color;
    this.speed = speed;
  }
  
  Car(int speed) {
    this.speed = speed;   // 클래스 내의 메소드 이름이 같아도 파라미터의 개수나, 데이터형만 다르게 선언을 메소드 오버로딩
  }
  
  int getSpeed() {  // 메소드
    return speed;
  }
}

public class Automobile extends Car { // 클래스 상속
  int seatNum;
  
  int getSeatNum(){
    return seatNum;
  }
  
  void upSpeed(int value){    // 오버라이딩 - 기존 것을 변경한 것.
    if (speed + value >= 300)
      speed = 300;
    else 
      speed = speed + (int) value;
  }
}

publci class exam07 {
  public static void main(String args[]){
    Car myCar1 = new Car(); // 인스턴스
    
    System.out.println("생성된 차의 대수(정적 필드) ==> " + Car.carCount); 
    System.out.println("생성된 차의 대수(정적 메소드) ==> " + Car.currentCarCount());
    System.out.println("차의 최고 제한 속도 ==> " + Car.MAXSPEED);
    
    
  }
}
```

``` java
// 추상 클래스 와 추상 메소드 예제
abstract class Animal{  // 추상 클래스 선언 - 인스턴스화를 금지하는 클래스
  String name;
  abstract void move(); // 추상 메소드 선언 - 본체가 없는 메소드
}

class Tiger extends Animal{
  int age;
  void move() {
    System.out.println("네발로 이동한다.");
  }
}

class Eagle extends Animal{
  String home;
  void move(){
    System.out.println("날개로 이동한다.");
  }
}

public exam10 {
  public static void main(String args[]){
    Tiger tiger1 = new Tiger();
    Eagle eagle1 = new Eagle();
    
    tiger1.move();
    eagle1.move();
    
    // 다형성 예제 - 자신의 서브 클래스에서 생성한 인스턴스도 클래스 변수에 대입할 수 있는 것
    Animal animal;
    
    animal = new Tiger();
    animal.move();
    
    animal = new Eagle();
    animal.move();
  }
}
```

``` java
// 인터페이스 
// class 키워드 대신 interface 키워드를 사용해서 정의
// 내부에는 추상 메소드를 선언
// 클래스에서 인터페이스를 받아서 완성할 때 implements 키워드 사용

// 다중 상속 
// Java는 다중 상속을 지원하지 않음. 대신 인터페이스를 사용하여 비슷하게 작성 가능함

interface iAnimal {
  abstract void eat();
}

static class iCat implements iAnimal {  // interface를 상속받을 때는 implements로 상속
  public void eat() {
    System.out.println("생선을 좋아한다.");
  }
}

static class iTiger extends Animal implements iAnimal {
  void move() {
    System.out.println("네발로 이동한다.");
  }
  
  public void eat() {
    System.out.println("멧돼지를 잡아먹는다.");
  }
}

interface clickListener {
  public void print();
}

public class exam12 {
  public static void main(String args[]){
    iCat cat = new iCat
    cat.eat();
    
    iTiger tiger = new iTiger();
    tiger.move();
    tiger.eat();
    
    // 익명 내부 클래스 - 한 번만 사용하고 버려지는 클래스에 사용
    clickListener listener = (new clickListener() {
      public void print(){
        System.out.println("클릭 리스너입니다.");
      }
    }
    listener.print();
  }
}
```

``` java
// 제네릭스 - 데이터 형식의 안전성을 보장하는 데 사용

ArrayList<String> strList = new ArrayList<String>();
strList.add("첫 번째");
strList.add("두 번째");
strList.add(3);

// 데이터 형식 변환
int a = Integer.parseInt("100");
double b = Double.parseDouble("100.123");

// 문자열 비교
String str = "안녕하세요";
if (str.equals((String)"안녕하세요")) {
// 문자열이 같으면 이곳을 수행
}


```
