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

publci class exam07 {
  public static void main(String args[]){
    Car myCar1 = new Car(); // 인스턴스
    
    System.out.println("생성된 차의 대수(정적 필드) ==> " + Car.carCount); 
    System.out.println("생성된 차의 대수(정적 메소드) ==> " + Car.currentCarCount());
    System.out.println("차의 최고 제한 속도 ==> " + Car.MAXSPEED);
  }
}
```
