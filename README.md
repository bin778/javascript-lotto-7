# 프리코스 3주차 과제 - 로또

> 우아한테크코스 7기 프리코스 3주차 과제 - 로또를 구현한 저장소입니다.

## 요구 사항

### 기능 요구 사항

- 로또 번호의 숫자 범위는 1~45 사이이다.
- 당첨 번호 추첨 시 중복되지 않는 숫자 6개와 보너스 번호 1개를 뽑는다.
- 당첨은 1등부터 5등까지 있다. 당첨 기준과 금액은 다음과 같다.
  - 1등: 6개 번호 일치 / 2,000,000,000원
  - 2등: 5개 번호 + 보너스 번호 일치 / 30,000,000원
  - 3등: 5개 번호 일치 / 1,500,000원
  - 4등: 4개 번호 일치 / 50,000원
  - 5등: 3개 번호 일치 / 5,000원
- 로또 1장의 가격은 1000원이며, 로또 구입 금액을 입력하면 구입 금액에 해당하는 만큼 로또를 발행한다.
- 로또 구입 금액을 입력하면 당첨 번호와 보너스 번호를 입력받는다.
- 사용자가 구매한 로또 번호와 당첨 번호를 비교하여 당첨 내역 및 수익률을 출력하고 로또 게임을 종료한다.
- 사용자가 잘못된 값을 입력할 경우 "[ERROR]"로 시작하는 메시지와 함께 Error를 발생시키고 해당 메시지를 출력한 다음 해당 지점부터 다시 입력을 받는다.

### 입출력 요구 사항

- 로또 구입 금액을 입력 받는다. 구입 금액은 1,000원 단위로 입력 받으며 1,000원으로 나누어 떨어지지 않는 경우 예외 처리한다.

```
14000
```

- 당첨 번호를 입력 받는다. 번호는 쉼표(,)를 기준으로 구분한다.

```
1,2,3,4,5,6
```

- 발행한 로또 수량 및 번호를 출력한다. 이때 로또 번호는 오름차순으로 정렬하여 보여준다.

```
8개를 구매했습니다.
[8, 21, 23, 41, 42, 43]
[3, 5, 11, 16, 32, 38]
[7, 11, 16, 35, 36, 44]
[1, 8, 11, 31, 41, 42]
[13, 14, 16, 38, 42, 45]
[7, 11, 30, 40, 42, 43]
[2, 13, 22, 32, 38, 45]
[1, 3, 5, 14, 22, 45]
```

- 당첨 내역을 출력한다.

```
3개 일치 (5,000원) - 1개
4개 일치 (50,000원) - 0개
5개 일치 (1,500,000원) - 0개
5개 일치, 보너스 볼 일치 (30,000,000원) - 0개
6개 일치 (2,000,000,000원) - 0개
```

- 수익률은 소수점 둘째 자리에서 반올림한다. (ex. 100.0%, 51.5%, 1,000,000.0%)

```
총 수익률은 62.5%입니다.
```

- 예외 상황 시 에러 문구를 출력해야 한다. 단, 에러 문구는 "[ERROR]"로 시작해야 한다.

```
[ERROR] 로또 번호는 1부터 45 사이의 숫자여야 합니다.
```

### 실행 결과 예시

```
구입금액을 입력해 주세요.
8000

8개를 구매했습니다.
[8, 21, 23, 41, 42, 43]
[3, 5, 11, 16, 32, 38]
[7, 11, 16, 35, 36, 44]
[1, 8, 11, 31, 41, 42]
[13, 14, 16, 38, 42, 45]
[7, 11, 30, 40, 42, 43]
[2, 13, 22, 32, 38, 45]
[1, 3, 5, 14, 22, 45]

당첨 번호를 입력해 주세요.
1,2,3,4,5,6

보너스 번호를 입력해 주세요.
7

당첨 통계
---
3개 일치 (5,000원) - 1개
4개 일치 (50,000원) - 0개
5개 일치 (1,500,000원) - 0개
5개 일치, 보너스 볼 일치 (30,000,000원) - 0개
6개 일치 (2,000,000,000원) - 0개
총 수익률은 62.5%입니다.
```

### 프로그래밍 요구 사항 1

- Node.js 20.17.0 버전에서 실행 가능하다.
- package.json 파일은 변경할 수 없으며, 제공된 라이브러리와 스타일 라이브러리 이외의 외부 라이브러리는 사용하지 않는다.
- 프로그램 종료 시 process.exit()를 호출하지 않는다.
- 프로그래밍 요구 사항에서 달리 명시하지 않는 한 파일, 패키지 등의 이름을 바꾸거나 이동하지 않는다.
- 자바스크립트 코드 컨벤션([JavaScript Style Guide](https://github.com/woowacourse/woowacourse-docs/tree/main/styleguide/javascript))을 지키면서 프로그래밍한다.
- Console.readLineAsync()와 Console.print()를 활용하여 입력 및 출력해야 한다.
- Random 값 추출은 Random.pickNumberInRange()를 활용한다.

```
MissionUtils.Random.pickUniqueNumbersInRange(1, 45, 6);
```

### 프로그래밍 요구 사항 2

- 들여쓰기 깊이는 3이 넘지 않도록 구현한다. 2까지만 허용한다.
  - 예를 들어 while문 안에 if문이 있으면 들여쓰기는 2이다.
  - 들여쓰기를 줄이는 가장 좋은 방법은 메서드를 분리하는 것이다.
- 삼항 연산자를 쓰지 않는다.
- Jest를 이용하여 구현한 기능에 대한 단위 테스트를 작성한다. 단, UI(System.out, System.in, Scanner) 로직은 제외한다.
  - 위 테스트 작성이 익숙하지 않다면 LottoTest.js를 참고한다.

### 프로그래밍 요구 사항 3

- 함수(또는 메서드)의 길이가 15라인을 넘어가지 않도록 하고, 함수는 한 가지 일만 하도록 한다.
- else 사용을 지양한다.
- 때로는 if/else, when문을 사용하는 것이 더 깔끔해 보일 수 있다. 어느 경우에 쓰는 것이 적절할지 스스로 고민해 본다.
- 힌트: if 조건절에서 값을 return하는 방식으로 구현하면 else를 사용하지 않아도 된다.

### Lotto 클래스

- 제공된 Lotto 클래스를 사용하여 구현해야 한다.
- Lotto에 numbers 이외의 필드(인스턴스 변수)를 추가할 수 없다.
- numbers의 접근 제어자인 #은 변경할 수 없다.
- Lotto의 패키지를 변경할 수 있다.

```
class Lotto {
  #numbers;

  constructor(numbers) {
    this.#validate(numbers);
    this.#numbers = numbers;
  }

  #validate(numbers) {
    if (numbers.length !== 6) {
      throw new Error("[ERROR] 로또 번호는 6개여야 합니다.");
    }
  }

  // TODO: 추가 기능 구현
}
```

## 구상 및 계획

### 구현

- 사용자에게 구입할 금액을 입력받는다.
- 로또 1장당 가격은 1000원이며, 입력한 금액의 1000원을 나눈 개수만큼 로또가 발행된다.
  - 금액이 1000원으로 나누어 떨어지지 않는 경우 예외 처리한다.
- 발행한 로또 수량 만큼 중복되지 않는 번호 6개를 출력한다.
  - 이때 로또 번호는 오름차순으로 정렬하여 출력한다.
- 당첨 번호와 보너스 번호를 각각 입력받는다.
  - 로또 번호의 숫자 범위는 1~45 사이이다.
  - 보너스 번호 또한 로또 번호와 중복되지 않아야 한다.
- 당첨 내역 안내판을 출력한다.
- 사용자와 발행한 로또 번호와 당첨 번호를 비교하여 수익률을 출력하고 게임을 종료한다.
  - 수익률은 소수점 둘째 자리에서 반올림한다.

### 구조

- [ERROR] 메시지는 사용자에게 의미를 확실하게 전달하도록 한다.
- 에러는 Object.freeze()를 이용하여 객체로 고정하여 따로 분리한다.
- 에러가 발생할 경우 바로 종료하지 않고 해당 지점부터 다시 입력을 받는다.
- 다른 JS파일을 만들어 메서드로 기능을 분리한다.
- 가능하면 MVC 패턴 및 객체지향을 준수하여 구현한다.
- 메서드가 동일한 기능이 있을 경우 중복하지 않고 재사용한다.

### 예외 처리

- 로또 구입 금액 입력
  - 숫자 이외의 값을 입력한 경우
  - 1000으로 나누어 떨어지지 않는 경우
- 당첨 번호 입력
  - 당첨 번호에 중복된 값이 있는 경우
  - 6개를 입력하지 않는 경우 ex) 1,2,3,4,5
  - 누락된 값이 있을 경우 ex) 1,2,3,,5,6
  - 당첨 번호가 숫자 이외의 값인 경우 ex) 1,2,3,a,b,c
  - 1~45 이외의 값을 입력한 경우
- 보너스 번호 입력
  - 숫자 이외의 값을 입력한 경우
  - 당첨 번호와 중복된 값일 경우
  - 1~45 이외의 값을 입력한 경우
- 동일한 예외 처리가 있을 경우 중복하지 않고 재사용한다.
