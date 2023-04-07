# Clean Code PHP - 한글판

## 목차

  1. [들어가며](#들어가며)
  2. [변수](#변수)
     * [의미있고 발음하기 쉬운 변수명을 사용하세요](#의미있고-발음하기-쉬운-변수명을-사용하세요)
     * [같은 타입의 변수에는 동일한 어휘를 사용하세요](#같은-타입의-변수에는-동일한-어휘를-사용하세요)
     * [찾기 쉬운 이름을 사용하세요 (part 1)](#찾기-쉬운-이름을-사용하세요-part-1)
     * [찾기 쉬운 이름을 사용하세요 (part 2)](#찾기-쉬운-이름을-사용하세요-part-2)
     * [설명적인 변수를 사용하세요](#설명적인-변수를-사용하세요)
     * [너무 깊은 중첩은 피하고 초기에 return 하세요 (part 1)](#너무-깊은-중첩은-피하고-초기에-return-하세요-part-1)
     * [너무 깊은 중첩은 피하고 초기에 return 하세요 (part 2)](#너무-깊은-중첩은-피하고-초기에-return-하세요-part-2)
     * [머릿속으로 짐작하게 하지 마세요](#머릿속으로-짐작하게-하지-마세요)
     * [불필요한 문맥을 덧붙이지 마세요](#불필요한-문맥을-덧붙이지-마세요)
     * [단락이나 조건문 대신 기본 인수를 사용하세요](#단락이나-조건문-대신-기본-인수를-사용하세요)
  3. [비교 연산자](#비교-연산자)
     * [동일 비교 연산자를 사용하세요](#동일-비교-연산자를-사용하세요)
  4. [함수](#함수)
     * [함수 인수 (2개 이하가 이상적)](#함수-인수-2개-이하가-이상적)
     * [함수는 한가지만 해야합니다](#함수는-한가지만-해야합니다)
     * [함수명은 어떤 일을 하는지 나타내야 합니다](#함수명은-어떤-일을-하는지-나타내야-합니다)
     * [함수는 추상화 레벨이 단 하나여야 합니다](#함수는-추상화-레벨이-단-하나여야-합니다)
     * [플래그를 함수의 매개변수로 사용하지 마세요](#플래그를-함수의-매개변수로-사용하지-마세요)
     * [부작용을 피하세요](#부작용을-피하세요)
     * [전역 함수를 사용하지 마세요](#전역-함수를-사용하지-마세요)
     * [싱글턴 패턴을 사용하지 마세요](#싱글턴-패턴을-사용하지-마세요)
     * [조건문은 캡슐화하세요](#조건문은-캡슐화하세요)
     * [부정 조건문을 피하세요](#부정-조건문을-피하세요)
     * [조건문을 피하세요](#조건문을-피하세요)
     * [타입 체킹을 피하세요 (part 1)](#타입-체킹을-피하세요-part-1)
     * [타입 체킹을 피하세요 (part 2)](#타입-체킹을-피하세요-part-2)
     * [불필요한 코드는 제거하세요](#불필요한-코드는-제거하세요)
  5. [객체와 자료구조](#객체와-자료구조)
     * [객체 캡슐화를 사용하세요](#객체-캡슐화를-사용하세요)
     * [객체가 private/protected 멤버를 갖게 하세요](#객체가-privateprotected-멤버를-갖게-하세요)
  6. [클래스](#클래스)
     * [상속보다는 컴포지션을 사용하세요](#상속보다는-컴포지션을-사용하세요)
     * [유창한 인터페이스를 피하세요](#유창한-인터페이스를-피하세요)
  7. [SOLID](#solid)
     * [단일 책임 원칙 (SRP)](#단일-책임-원칙-srp)
     * [개방/폐쇄 원칙 (OCP)](#개방폐쇄-원칙-ocp)
     * [리스코브 치환 원칙 (LSP)](#리스코브-치환-원칙-lsp)
     * [인터페이스 분리 원칙 (ISP)](#인터페이스-분리-원칙-isp)
     * [의존성 역전 원칙 (DIP)](#의존성-역전-원칙-dip)
  8. [반복하지 마세요 (DRY)](#반복하지-마세요-dry)
  9. [번역](#번역)

## 들어가며


Robert C. Martin의 책, 소프트웨어 엔지니어링의 교과서라고 불리는 [*Clean Code*](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882) PHP 버전입니다.
이 문서는 스타일 가이드가 아닙니다. PHP로 읽기 쉽고 재사용 가능하며, 리팩토링이 쉬운 소프트웨어를 만들어내기 위한 안내서입니다.

문서의 모든 원칙을 엄격하게 지켜야 할 필요는 없습니다. 그리고 어떤 것들은 일반적으로 합의되지 못할 것입니다.
이 문서는 안내서일 뿐이고 그 이상이 될 순 없지만, 수년간 *Clean Code*의 저자들로부터 축적된 경험을 문서화 한 것입니다.

[clean-code-javascript](https://github.com/ryanmcdermott/clean-code-javascript)에 영감을 받아 작성되었습니다.

여전히 PHP 5를 사용하는 개발자가 많겠지만, 문서의 예제 대부분은 PHP 7.1 이상의 버전에서만 작동합니다.

## 변수

### 의미있고 발음하기 쉬운 변수명을 사용하세요

**나쁜 예:**

```php
$ymdstr = $moment->format('y-m-d');
```

**좋은 예:**

```php
$currentDate = $moment->format('y-m-d');
```

**[⬆ 위로 가기](#목차)**

### 같은 타입의 변수에는 동일한 어휘를 사용하세요

**나쁜 예:**

```php
getUserInfo();
getUserData();
getUserRecord();
getUserProfile();
```

**좋은 예:**

```php
getUser();
```

**[⬆ 위로 가기](#목차)**

### 찾기 쉬운 이름을 사용하세요 (part 1)

작성해야 할 코드보다 읽어야 할 코드가 더 많습니다. 우리가 작성해야 할 코드를 읽기 쉽고 찾기 쉽게 만드는 것은 중요합니다.
프로그램을 이해하기 쉽도록 변수명을 의미 있게 짓지 *않는*다면, 코드를 읽는 사람을 곤란하게 만드는 것입니다.
변수명을 찾기 쉽게 만드세요.


**나쁜 예:**

```php
// 도대체 448이 뭔 뜻이래요?
$result = $serializer->serialize($data, 448);
```

**좋은 예:**

```php
$json = $serializer->serialize($data, JSON_UNESCAPED_SLASHES | JSON_PRETTY_PRINT | JSON_UNESCAPED_UNICODE);
```

### 찾기 쉬운 이름을 사용하세요 (part 2)

**나쁜 예:**

```php
// 4는 무슨 의미인가요?
if ($user->access & 4) {
    // ...
}
```

**좋은 예:**

```php
class User
{
    const ACCESS_READ = 1;
    const ACCESS_CREATE = 2;
    const ACCESS_UPDATE = 4;
    const ACCESS_DELETE = 8;
}

if ($user->access & User::ACCESS_UPDATE) {
    // 수정하세요...
}
```

**[⬆ 위로 가기](#목차)**

### 설명적인 변수를 사용하세요

**나쁜 예:**

```php
$address = 'One Infinite Loop, Cupertino 95014';
$cityZipCodeRegex = '/^[^,]+,\s*(.+?)\s*(\d{5})$/';
preg_match($cityZipCodeRegex, $address, $matches);

saveCityZipCode($matches[1], $matches[2]);
```

**나쁘진 않은 예:**

조금 낫군요. 하지만, 여전히 regex에 아주 많이 의존하고 있습니다.

```php
$address = 'One Infinite Loop, Cupertino 95014';
$cityZipCodeRegex = '/^[^,]+,\s*(.+?)\s*(\d{5})$/';
preg_match($cityZipCodeRegex, $address, $matches);

[, $city, $zipCode] = $matches;
saveCityZipCode($city, $zipCode);
```

**좋은 예:**

naming subpattern을 사용해서 regex의 의존성을 줄입시다.

```php
$address = 'One Infinite Loop, Cupertino 95014';
$cityZipCodeRegex = '/^[^,]+,\s*(?<city>.+?)\s*(?<zipCode>\d{5})$/';
preg_match($cityZipCodeRegex, $address, $matches);

saveCityZipCode($matches['city'], $matches['zipCode']);
```

**[⬆ 위로 가기](#목차)**

### 너무 깊은 중첩은 피하고 초기에 return 하세요 (part 1)

너무 많은 if else 문은 코드를 따라가기 어렵게 만들 수 있습니다. 명료한 것이 암시하는 것보다 나아요.


**나쁜 예:**

```php
function isShopOpen($day): bool
{
    if ($day) {
        if (is_string($day)) {
            $day = strtolower($day);
            if ($day === 'friday') {
                return true;
            } elseif ($day === 'saturday') {
                return true;
            } elseif ($day === 'sunday') {
                return true;
            } else {
                return false;
            }
        } else {
            return false;
        }
    } else {
        return false;
    }
}
```

**좋은 예:**

```php
function isShopOpen(string $day): bool
{
    if (empty($day)) {
        return false;
    }

    $openingDays = [
        'friday', 'saturday', 'sunday'
    ];

    return in_array(strtolower($day), $openingDays, true);
}
```

**[⬆ 위로 가기](#목차)**

### 너무 깊은 중첩은 피하고 초기에 return 하세요 (part 2)

**나쁜 예:**

```php
function fibonacci(int $n)
{
    if ($n < 50) {
        if ($n !== 0) {
            if ($n !== 1) {
                return fibonacci($n - 1) + fibonacci($n - 2);
            } else {
                return 1;
            }
        } else {
            return 0;
        }
    } else {
        return 'Not supported';
    }
}
```

**좋은 예:**

```php
function fibonacci(int $n): int
{
    if ($n === 0 || $n === 1) {
        return $n;
    }

    if ($n > 50) {
        throw new \Exception('Not supported');
    }

    return fibonacci($n - 1) + fibonacci($n - 2);
}
```

**[⬆ 위로 가기](#목차)**

### 머릿속으로 짐작하게 하지 마세요

우리의 코드를 읽는 사람이 변수가 어떤 의미인지 해석하게 하지 마세요.
명료한 것이 암시하는 것보다 좋아요.

**나쁜 예:**

```php
$l = ['Austin', 'New York', 'San Francisco'];

for ($i = 0; $i < count($l); $i++) {
    $li = $l[$i];
    doStuff();
    doSomeOtherStuff();
    // ...
    // ...
    // ...
    // 잠깐 $li가 뭐였죠?
    dispatch($li);
}
```

**좋은 예:**

```php
$locations = ['Austin', 'New York', 'San Francisco'];

foreach ($locations as $location) {
    doStuff();
    doSomeOtherStuff();
    // ...
    // ...
    // ...
    dispatch($location);
}
```

**[⬆ 위로 가기](#목차)**

### 불필요한 문맥을 덧붙이지 마세요

클래스/객체 명이 이미 말해주고 있다면, 변수명에 굳이 번복하지 마세요.

**나쁜 예:**

```php
class Car
{
    public $carMake;
    public $carModel;
    public $carColor;

    //...
}
```

**좋은 예:**

```php
class Car
{
    public $make;
    public $model;
    public $color;

    //...
}
```

**[⬆ 위로 가기](#목차)**

### 단락이나 조건문 대신 기본 인수를 사용하세요

**좋진 않은 예:**

아래 예제는 `$breweryName`이 `NULL`이 될 수 있으므로 좋지 않아요.

```php
function createMicrobrewery($breweryName = 'Hipster Brew Co.'): void
{
    // ...
}
```

**나쁘진 않은 예:**

위의 예제보다 훨씬 이해하기 쉬워졌습니다. 하지만 변수의 값을 제어하는 게 낫겠습니다.

```php
function createMicrobrewery($name = null): void
{
    $breweryName = $name ?: 'Hipster Brew Co.';
    // ...
}
```

**좋은 예:**

[type hinting](http://php.net/manual/en/functions.arguments.php#functions.arguments.type-declaration)을 사용해서 `$breweryName`이 `NULL`이 될 수 없음을 확신할 수 있습니다.

```php
function createMicrobrewery(string $breweryName = 'Hipster Brew Co.'): void
{
    // ...
}
```

**[⬆ 위로 가기](#목차)**

## 비교 연산자

**[⬆ 위로 가기](#목차)**

### [동일 비교 연산자](http://php.net/manual/en/language.operators.comparison.php)를 사용하세요

**좋진 않은 예:**

```php
$a = '42';
$b = 42;
단순한 비교 연산자를 사용하면 string이 int로 변환 될 것입니다.

if( $a != $b ) {
   //이 표현식은 항상 건너 뛸 것입니다.
}

```
$a != $b는 false를 리턴하지만 사실은 true가 맞아요!
string '42'는 int 42와 다릅니다.

**좋은 예:**
동일 비교 연산자를 사용하면 자료형과 값을 비교합니다.
```php
if( $a !== $b ) {
    //이 표현식은 확인되었습니다.
}

```
$a !== $b는 true를 return 합니다.

**[⬆ 위로 가기](#목차)**


## 함수

### 함수 인수 (2개 이하가 이상적)

함수 매개변수의 개수를 제한하는 것은 엄청나게 중요합니다. 함수를 테스트하는 것을 더 쉽게 만들어 주기 때문이죠. 3개 이상의 매개변수는 테스트 조합을 폭발하게 합니다. 매개변수마다 서로 다른 수많은 케이스를 테스트해야 하기 때문입니다.

매개변수가 없는 것(0개)이 가장 이상적입니다. 1개에서 2개 정도는 괜찮습니다. 3개는 피해야 합니다. 매개변수가 3개를 넘어가면 통합되어야 합니다. 일반적으로, 매개변수가 2개 이상이라면 그 함수는 너무 많은 역할을 하는 것입니다. 그런 경우가 아니라면, 상위 레벨의 객체는 대부분 하나의 매개변수로 충분할 것입니다.

**나쁜 예:**

```php
function createMenu(string $title, string $body, string $buttonText, bool $cancellable): void
{
    // ...
}
```

**좋은 예:**

```php
class MenuConfig
{
    public $title;
    public $body;
    public $buttonText;
    public $cancellable = false;
}

$config = new MenuConfig();
$config->title = 'Foo';
$config->body = 'Bar';
$config->buttonText = 'Baz';
$config->cancellable = true;

function createMenu(MenuConfig $config): void
{
    // ...
}
```

**[⬆ 위로 가기](#목차)**

### 함수는 한가지만 해야합니다

소프트웨어 엔지니어링에서 가장 중요한 규칙입니다. 함수가 1개 이상의 역할을 하게 되면, 작성, 테스트, 추론하기가 어려워집니다. 함수를 단 하나의 행동으로 떼어낼 수 있다면, 코드는 쉽게 리팩토링 될 수 있으며 훨씬 더 깔끔하게 읽힐 것입니다. 이 문서에서 나머지는 다 갖다 버리고 이것만 지키신대도 웬만한 개발자보다 앞서게 될 것입니다.

**나쁜 예:**
```php
function emailClients(array $clients): void
{
    foreach ($clients as $client) {
        $clientRecord = $db->find($client);
        if ($clientRecord->isActive()) {
            email($client);
        }
    }
}
```

**좋은 예:**

```php
function emailClients(array $clients): void
{
    $activeClients = activeClients($clients);
    array_walk($activeClients, 'email');
}

function activeClients(array $clients): array
{
    return array_filter($clients, 'isClientActive');
}

function isClientActive(int $client): bool
{
    $clientRecord = $db->find($client);

    return $clientRecord->isActive();
}
```

**[⬆ 위로 가기](#목차)**

### 함수명은 어떤 일을 하는지 나타내야 합니다.

**나쁜 예:**

```php
class Email
{
    //...

    public function handle(): void
    {
        mail($this->to, $this->subject, $this->body);
    }
}

$message = new Email(...);
// 이게 뭘까요? 메세지를 위한 핸들? 지금 우리가 파일을 작성할건가요?
$message->handle();
```

**좋은 예:**

```php
class Email
{
    //...

    public function send(): void
    {
        mail($this->to, $this->subject, $this->body);
    }
}

$message = new Email(...);
// 분명하고 명백하군요
$message->send();
```

**[⬆ 위로 가기](#목차)**

### 함수는 추상화 레벨이 단 하나여야 합니다

추상화 레벨이 하나 이상이라면, 보통 우리의 함수는 너무 많은 일을 하고 있는 것입니다. 함수를 분리하면 재사용성을 높일 수 있고 테스트가 용이해집니다.

**나쁜 예:**

```php
function parseBetterJSAlternative(string $code): void
{
    $regexes = [
        // ...
    ];

    $statements = explode(' ', $code);
    $tokens = [];
    foreach ($regexes as $regex) {
        foreach ($statements as $statement) {
            // ...
        }
    }

    $ast = [];
    foreach ($tokens as $token) {
        // lex...
    }

    foreach ($ast as $node) {
        // parse...
    }
}
```

**여전히 나쁜 예:**

기능의 일부를 옮겼지만, `parseBetterJSAlternative()` 함수는 여전히 너무 복잡하고 테스트할 수 없습니다.

```php
function tokenize(string $code): array
{
    $regexes = [
        // ...
    ];

    $statements = explode(' ', $code);
    $tokens = [];
    foreach ($regexes as $regex) {
        foreach ($statements as $statement) {
            $tokens[] = /* ... */;
        }
    }

    return $tokens;
}

function lexer(array $tokens): array
{
    $ast = [];
    foreach ($tokens as $token) {
        $ast[] = /* ... */;
    }

    return $ast;
}

function parseBetterJSAlternative(string $code): void
{
    $tokens = tokenize($code);
    $ast = lexer($tokens);
    foreach ($ast as $node) {
        // parse...
    }
}
```

**좋은 예:**

가장 좋은 해결책은 `parseBetterJSAlternative()` 함수의 의존성을 제거하는 것 입니다.

```php
class Tokenizer
{
    public function tokenize(string $code): array
    {
        $regexes = [
            // ...
        ];

        $statements = explode(' ', $code);
        $tokens = [];
        foreach ($regexes as $regex) {
            foreach ($statements as $statement) {
                $tokens[] = /* ... */;
            }
        }

        return $tokens;
    }
}

class Lexer
{
    public function lexify(array $tokens): array
    {
        $ast = [];
        foreach ($tokens as $token) {
            $ast[] = /* ... */;
        }

        return $ast;
    }
}

class BetterJSAlternative
{
    private $tokenizer;
    private $lexer;

    public function __construct(Tokenizer $tokenizer, Lexer $lexer)
    {
        $this->tokenizer = $tokenizer;
        $this->lexer = $lexer;
    }

    public function parse(string $code): void
    {
        $tokens = $this->tokenizer->tokenize($code);
        $ast = $this->lexer->lexify($tokens);
        foreach ($ast as $node) {
            // parse...
        }
    }
}
```

**[⬆ 위로 가기](#목차)**

### 플래그를 함수의 매개변수로 사용하지 마세요

플래그를 사용하는 것은 함수가 한가지 이상의 일을 할 것이라 말하는 셈입니다. 함수는 한 가지 일을 해야 합니다.
만약 Boolean 값에 따라 서로 다른 코드를 사용해야 한다면 함수를 분리하세요.

**나쁜 예:**

```php
function createFile(string $name, bool $temp = false): void
{
    if ($temp) {
        touch('./temp/'.$name);
    } else {
        touch($name);
    }
}
```

**좋은 예:**

```php
function createFile(string $name): void
{
    touch($name);
}

function createTempFile(string $name): void
{
    touch('./temp/'.$name);
}
```

**[⬆ 위로 가기](#목차)**

### 부작용을 피하세요

함수는 다른 값을 가져와서 반환하는 것 외에 다른 기능을 수행하는 경우 부작용을 낳습니다.
부작용은 파일에 쓰는 것일 수도 있고, 몇몇 전역 변수의 값을 수정하는 것, 실수로 모든 돈을 낯선 사람에게 보내는 것이 될 수 있습니다.

때때로 프로그램에서 부작용을 가질 필요가 있습니다. 앞의 예와 같이, 한 파일에 쓸 필요가 있을 수 있습니다.
우리가 하고 싶은 것은 이 일을 하는 곳을 모으는 것입니다. 특정 파일에 쓰기 위한 여러 개의 함수와 클래스를 갖지 마세요.
그 역할을 하는 하나의 서비스만 가지세요. 하나, 단 하나만요.

요점은 일반적인 함정을 피하라는 것입니다. 구조가 없는 객체 간에 상태를 공유하는 것이나, 어떤 것으로도 쓰일 수 있는 변동성 데이터를 사용하는 것, 부작용이 발생할 수 있는 곳을 모으지 않는 것 같은 함정에서요.
만약 우리가 함정을 피할 수 있다면, 다른 대부분의 프로그래머보다 더 행복해질 거예요.

**나쁜 예:**

```php
// 다음 함수에서 참조하는 전역 변수
// 이 이름을 사용하는 다른 함수가 있다면, 이제 배열이 되었을거고 함수가 작동하지 않을 수 있습니다.
$name = 'Ryan McDermott';

function splitIntoFirstAndLastName(): void
{
    global $name;

    $name = explode(' ', $name);
}

splitIntoFirstAndLastName();

var_dump($name); // ['Ryan', 'McDermott'];
```

**좋은 예:**

```php
function splitIntoFirstAndLastName(string $name): array
{
    return explode(' ', $name);
}

$name = 'Ryan McDermott';
$newName = splitIntoFirstAndLastName($name);

var_dump($name); // 'Ryan McDermott';
var_dump($newName); // ['Ryan', 'McDermott'];
```

**[⬆ 위로 가기](#목차)**

### 전역 함수를 사용하지 마세요

전역을 오염시키는 것은 여러 언어에서 나쁜 관행입니다. 왜냐하면 다른 라이브러리와 충돌 할 수 있고 API 사용자는 상용에서 예외를 받을 때까지 종잡을 수 없기 때문이죠.
예를 들어볼까요? 만약 설정 배열을 갖고싶다면 어떨까요? `config()`같은 전역 함수를 작성할 수 있지만, 같은 작업을 시도하려는 다른 라이브러리와 충돌 할 수 있습니다.

**나쁜 예:**

```php
function config(): array
{
    return  [
        'foo' => 'bar',
    ]
}
```

**좋은 예:**

```php
class Configuration
{
    private $configuration = [];

    public function __construct(array $configuration)
    {
        $this->configuration = $configuration;
    }

    public function get(string $key): ?string
    {
        return isset($this->configuration[$key]) ? $this->configuration[$key] : null;
    }
}
```

설정을 불러오고 `Configuration` 클래스의 인스턴스를 생성하세요.

```php
$configuration = new Configuration([
    'foo' => 'bar',
]);
```
이제 우리는 애플리케이션에서 `Configuration`의 인스턴스를 반드시 사용해야 합니다.

**[⬆ 위로 가기](#목차)**

### 싱글턴 패턴을 사용하지 마세요

싱글턴은 [안티 패턴](https://en.wikipedia.org/wiki/Singleton_pattern) 입니다.

Brian Button이 쉽게 풀어쓴 바로는
 1. 싱글턴은 일반적으로 **전역 인스턴스** 로 사용되는데, 왜 그게 그렇게 나쁠까요? 그 이유는 애플리케이션의 **의존성** 을 인터페이스를 통해 노출하는 대신 코드에 **숨기기** 때문입니다. 넘기는 것을 피하기 위해 무언가를 전역으로 만드는 것은 [코드 스멜](https://en.wikipedia.org/wiki/Code_smell)입니다.
 2. **스스로의 생성과 생명주기를 제어** 한다는 사실에 의해서 [단일 책임 원칙](#단일-책임-원칙-srp)를 어깁니다.
 3. 본질적으로 코드를 단단하게 [결합](https://en.wikipedia.org/wiki/Coupling_%28computer_programming%29)시키는 원인이 됩니다. 이로인해 많은 경우에서 **테스트가 어려워지게** 만듭니다.
 4. 애플리케이션의 생명주기 동안 상태를 유지합니다. 유닛 테스트에서는 크게 문제가 되지 않지만 **테스트가 요구되는 상황으로 끝날 수 있어** 또 다른 타격이 발생할 수 있습니다. 그 이유는 무엇일까요? 각각의 유닛 테스트는 다른 유닛 테스트와 독립적이어야 하기 때문입니다.

[Misko Hevery](http://misko.hevery.com/about/)가 [문제의 근원](http://misko.hevery.com/2008/08/25/root-cause-of-singletons/)에 대해 작성한 매우 좋은 생각도 있습니다.

**나쁜 예:**

```php
class DBConnection
{
    private static $instance;

    private function __construct(string $dsn)
    {
        // ...
    }

    public static function getInstance(): DBConnection
    {
        if (self::$instance === null) {
            self::$instance = new self();
        }

        return self::$instance;
    }

    // ...
}

$singleton = DBConnection::getInstance();
```

**좋은 예:**

```php
class DBConnection
{
    public function __construct(string $dsn)
    {
        // ...
    }

     // ...
}
```

`DBConnection` 클래스의 인스턴스를 생성하고 [DSN](http://php.net/manual/en/pdo.construct.php#refsect1-pdo.construct-parameters)을 설정합니다.

```php
$connection = new DBConnection($dsn);
```
이제 우리는 어플리케이션에서 `DBConnection`의 인스턴스를 사용해야 합니다.

**[⬆ 위로 가기](#목차)**

### 조건문은 캡슐화하세요

**나쁜 예:**

```php
if ($article->state === 'published') {
    // ...
}
```

**좋은 예:**

```php
if ($article->isPublished()) {
    // ...
}
```

**[⬆ 위로 가기](#목차)**

### 부정 조건문을 피하세요

**나쁜 예:**

```php
function isDOMNodeNotPresent(\DOMNode $node): bool
{
    // ...
}

if (!isDOMNodeNotPresent($node))
{
    // ...
}
```

**좋은 예:**

```php
function isDOMNodePresent(\DOMNode $node): bool
{
    // ...
}

if (isDOMNodePresent($node)) {
    // ...
}
```

**[⬆ 위로 가기](#목차)**

### 조건문을 피하세요

이건 불가능한 일처럼 보일 겁니다. 이 말을 처음 들은 대부분의 사람들은 묻습니다. "어떻게 `if` 문 없이 뭔가를 할 수 있죠?"
그에 대한 답은 다형성입니다. 많은 케이스에서 같은 일을 완수하기 위해 우리는 다형성을 사용할 수 있습니다.
두 번째 질문은 일반적으로 이럴 거예요. "음, 좋습니다. 하지만 왜 제가 그렇게 해야 하죠?"
그에 대한 대답은 우리가 이전에 배운 클린코드 개념 때문입니다. '함수는 한 가지만 해야 합니다.'
`if` 문을 가진 함수와 클래스를 가지게 될 때, 우리는 우리의 함수가 한가지 이상을 한다고 사람들에게 말하는 셈입니다.
기억하세요. 딱 한 가지만 하세요.

**나쁜 예:**

```php
class Airplane
{
    // ...

    public function getCruisingAltitude(): int
    {
        switch ($this->type) {
            case '777':
                return $this->getMaxAltitude() - $this->getPassengerCount();
            case 'Air Force One':
                return $this->getMaxAltitude();
            case 'Cessna':
                return $this->getMaxAltitude() - $this->getFuelExpenditure();
        }
    }
}
```

**좋은 예:**

```php
interface Airplane
{
    // ...

    public function getCruisingAltitude(): int;
}

class Boeing777 implements Airplane
{
    // ...

    public function getCruisingAltitude(): int
    {
        return $this->getMaxAltitude() - $this->getPassengerCount();
    }
}

class AirForceOne implements Airplane
{
    // ...

    public function getCruisingAltitude(): int
    {
        return $this->getMaxAltitude();
    }
}

class Cessna implements Airplane
{
    // ...

    public function getCruisingAltitude(): int
    {
        return $this->getMaxAltitude() - $this->getFuelExpenditure();
    }
}
```

**[⬆ 위로 가기](#목차)**

### 타입 체킹을 피하세요 (part 1)

PHP는 타입이 없습니다. 즉, 우리의 함수가 어떠한 타입의 인수도 가질 수 있다는 걸 뜻합니다.
때때로 우리는 이러한 자유에 물리기도 합니다. 그래서 우리의 함수 내에서 타입 체킹을 하는 것에 구미가 당기게 되곤 합니다.
이렇게 하는 것을 피하는 많은 방법이 있습니다. 고려할 첫 번째는 일관된 API입니다.

**나쁜 예:**

```php
function travelToTexas($vehicle): void
{
    if ($vehicle instanceof Bicycle) {
        $vehicle->pedalTo(new Location('texas'));
    } elseif ($vehicle instanceof Car) {
        $vehicle->driveTo(new Location('texas'));
    }
}
```

**좋은 예:**

```php
function travelToTexas(Traveler $vehicle): void
{
    $vehicle->travelTo(new Location('texas'));
}
```

**[⬆ 위로 가기](#목차)**

### 타입 체킹을 피하세요 (part 2)

만약 PHP 7 이상의 버전으로 string, integers, 그리고 array 같은 기본 자료형을 가지고 일하고 있고, 다형성을 사용할 순 없지만
여전히 타입을 체크해야할 필요성을 느낀다면 [타입 선언](http://php.net/manual/en/functions.arguments.php#functions.arguments.type-declaration)이나 strict 모드를 고려해야 합니다.
이것은 표준 PHP 문법에 정적 타입을 제공합니다.
직접 타입을 체크할 때의 문제는, 너무 많은 추가적인 장황함을 필요로 해서 잃어버린 가독성을 보상해줄 수 없는 가짜 "안전한 타입"을 만들어 낸다는 것입니다.
PHP는 깔끔하게 두고, 좋은 테스트를 작성하고, 좋은 코드 리뷰를 가지세요. 그게 싫다면, PHP strict 타입 선언이나 strict 모드로 모든 작업을 수행하세요.

**나쁜 예:**

```php
function combine($val1, $val2): int
{
    if (!is_numeric($val1) || !is_numeric($val2)) {
        throw new \Exception('숫자 타입이어야 합니다.');
    }

    return $val1 + $val2;
}
```

**좋은 예:**

```php
function combine(int $val1, int $val2): int
{
    return $val1 + $val2;
}
```

**[⬆ 위로 가기](#목차)**

### 불필요한 코드는 제거하세요

불필요한 코드는 중복된 코드만큼이나 나쁩니다. 코드에 남겨야 할 이유가 전혀 없습니다. 호출이 안되고 있다면 없애버리세요!
만약 여전히 필요하대도 버전 기록에 안전하게 남아있을 것입니다.

**나쁜 예:**

```php
function oldRequestModule(string $url): void
{
    // ...
}

function newRequestModule(string $url): void
{
    // ...
}

$request = newRequestModule($requestUrl);
inventoryTracker('apples', $request, 'www.inventory-awesome.io');
```

**좋은 예:**

```php
function requestModule(string $url): void
{
    // ...
}

$request = requestModule($requestUrl);
inventoryTracker('apples', $request, 'www.inventory-awesome.io');
```

**[⬆ 위로 가기](#목차)**


## 객체와 자료구조

### 객체 캡슐화를 사용하세요

PHP에서는 메소드에 `public`, `protected`,`private`을 설정할 수 있습니다.
이를 통해 객체의 프로퍼티 수정을 제어할 수 있습니다.

* 객체 프로퍼티를 얻는 것 이상의 일을 하고 싶다면, 코드단에 있는 모든 접근자를 찾아보고 바꿀 필요가 없습니다.
* `set`을 할때 검증(밸리데이션)을 간단하게 추가합니다.
* 내부 표현을 캡슐화합니다.
* 가져오고 설정할 때 로깅 및 오류 처리를 추가하기 쉽습니다.
* 클래스를 상속 받아서, 기본 기능을 오버라이드 할 수 있습니다.
* 서버에서 가져온다고 할 때, 객체의 프로퍼티를 느리게 로드할 수 있습니다.

또한, 이는 [개방/폐쇄 원칙 (OCP)](#개방폐쇄-원칙-ocp) 원칙의 일부입니다.

**나쁜 예:**

```php
class BankAccount
{
    public $balance = 1000;
}

$bankAccount = new BankAccount();

// 신발을 삼
$bankAccount->balance -= 100;
```

**좋은 예:**

```php
class BankAccount
{
    private $balance;

    public function __construct(int $balance = 1000)
    {
      $this->balance = $balance;
    }

    public function withdraw(int $amount): void
    {
        if ($amount > $this->balance) {
            throw new \Exception('Amount greater than available balance.');
        }

        $this->balance -= $amount;
    }

    public function deposit(int $amount): void
    {
        $this->balance += $amount;
    }

    public function getBalance(): int
    {
        return $this->balance;
    }
}

$bankAccount = new BankAccount();

// 신발을 삼
$bankAccount->withdraw($shoesPrice);

// 잔액을 받아옴
$balance = $bankAccount->getBalance();
```

**[⬆ 위로 가기](#목차)**

### 객체가 private/protected 멤버를 갖게 하세요

* `public`메소드와 프로퍼티는 변경에 가장 취약합니다. 그 이유는 어떤 외부 코드가 쉽게 의존할 수 있고, 어떤 코드가 의존하고 있는지 제어할 수 없기 때문입니다.
**클래스의 수정은 클래스의 모든 사용자에게 위험합니다.**
* `protected` 제어자는 `public` 만큼이나 위험합니다. 자식 클래스 범위내에서 사용할 수 있기 때문입니다. 이는 public과 protected의 차이점은 접근 매커니즘에만 있다는 것을 의미하나, 캡슐화 보증은 동일하게 유지됩니다. **클래스의 수정은 모든 하위 클래스에 위험합니다.**
* `private` 제어자는 코드가 **단일 클래스의 경계에서만 수정하는 것이 위험함** 을 보증합니다(변경하는 것이 안전하며 [젠가 효과](http://www.urbandictionary.com/define.php?term=Jengaphobia&defid=2494196)를 갖지 않을 것 입니다.).

그러므로 `private` 을 기본으로 사용하고 외부 클래스에 대한 접근 권한을 제공해야 할 때 `public/protected`를 사용하세요.

더 많은 정보를 원하면 이 주제에 대해서 [Fabien Potencier](https://github.com/fabpot)가 작성한 [블로그 포스트](http://fabien.potencier.org/pragmatism-over-theory-protected-vs-private.html)를 읽어볼 수 있습니다.

**나쁜 예:**

```php
class Employee
{
    public $name;

    public function __construct(string $name)
    {
        $this->name = $name;
    }
}

$employee = new Employee('John Doe');
echo 'Employee name: '.$employee->name; // 직원명: John Doe
```

**좋은 예:**

```php
class Employee
{
    private $name;

    public function __construct(string $name)
    {
        $this->name = $name;
    }

    public function getName(): string
    {
        return $this->name;
    }
}

$employee = new Employee('John Doe');
echo 'Employee name: '.$employee->getName(); // 직원명: John Doe
```

**[⬆ 위로 가기](#목차)**

## 클래스

### 상속보다는 컴포지션을 사용하세요

GoF(the Gang of Four)의 [*디자인 패턴*](https://en.wikipedia.org/wiki/Design_Patterns)에서 잘 알려진 바와 같이,
가능하다면 상속보다는 컴포지션을 선호해야 합니다.
상속을 사용하는 데는 여러 가지 좋은 이유가 있으며 컴포지션을 사용하는 데도 여러 가지 좋은 이유가 있습니다.

이 좌우명의 요지는 만약 우리가 본능적으로 상속을 생각한다면, 컴포지션이 우리의 문제를 더 잘 설계할 수 있을지 생각해보려 노력하라는 것입니다.
어떤 경우에는 그렇거든요.

아마도 이렇게 생각하고 있을지도 모릅니다, "그럼 언제 상속을 사용해야 하지?" 눈앞에 닥친 문제에 따라 다릅니다만, 아래 목록은 상속이 컴포지션보다 더 잘 맞는 경우입니다.

1. 상속이 "has-a" 관계가 아닌 "is-a"관계를 나타냅니다. (사용자->사용자 세부정보 vs 인간->동물)
2. 기본 클래스의 코드를 재사용할 수 있습니다. (인간은 모든 동물처럼 움직일 수 있습니다.)
3. 기본 클래스를 변경하여 파생 클래스에 대한 전역 변경을 원하는 경우 (모든 동물의 움직일 때의 칼로리 소모량 변경)

**나쁜 예:**

```php
class Employee
{
    private $name;
    private $email;

    public function __construct(string $name, string $email)
    {
        $this->name = $name;
        $this->email = $email;
    }

    // ...
}

// 직원(Employee)들이 세금 데이터를 "가지고" 있기 때문에 좋지 않습니다.
// EmployeeTaxData는 직원(Employee) 타입이 아닙니다.

class EmployeeTaxData extends Employee
{
    private $ssn;
    private $salary;

    public function __construct(string $name, string $email, string $ssn, string $salary)
    {
        parent::__construct($name, $email);

        $this->ssn = $ssn;
        $this->salary = $salary;
    }

    // ...
}
```

**좋은 예:**

```php
class EmployeeTaxData
{
    private $ssn;
    private $salary;

    public function __construct(string $ssn, string $salary)
    {
        $this->ssn = $ssn;
        $this->salary = $salary;
    }

    // ...
}

class Employee
{
    private $name;
    private $email;
    private $taxData;

    public function __construct(string $name, string $email)
    {
        $this->name = $name;
        $this->email = $email;
    }

    public function setTaxData(string $ssn, string $salary)
    {
        $this->taxData = new EmployeeTaxData($ssn, $salary);
    }

    // ...
}
```

**[⬆ 위로 가기](#목차)**

### 유창한 인터페이스를 피하세요

[유창한 인터페이스](https://en.wikipedia.org/wiki/Fluent_interface)는 [Method chaining](https://en.wikipedia.org/wiki/Method_chaining)을 사용해 소스 코드의 가독성을 증진시키기 위한 객체지향 API입니다.

어떤 맥락이 있을 수 있지만, 패턴들이 코드의 장황함을 줄여주는, 주로 빌더 객체들은(예를 들어 [PHPUnit Mock Builder](https://phpunit.de/manual/current/en/test-doubles.html) 나 [Doctrine Query Builder](http://docs.doctrine-project.org/projects/doctrine-dbal/en/latest/reference/query-builder.html)) 조금 더 자주 비용을 동반하곤 합니다.

1. [캡슐화](https://en.wikipedia.org/wiki/Encapsulation_%28object-oriented_programming%29)를 어깁니다.
2. [데코레이터 패턴](https://en.wikipedia.org/wiki/Decorator_pattern)을 어깁니다.
3. 테스트 슈트에서 [mock](https://en.wikipedia.org/wiki/Mock_object)이 어려워집니다.
4. commit의 변경사항을 읽기 어렵게 만듭니다.

더 많은 정보는 [Marco Pivetta](https://github.com/Ocramius)가 이 주제에 대해 작성한 [blog post](https://ocramius.github.io/blog/fluent-interfaces-are-evil/) 에서 전체를 읽어 볼 수 있습니다.

**나쁜 예:**

```php
class Car
{
    private $make = 'Honda';
    private $model = 'Accord';
    private $color = 'white';

    public function setMake(string $make): self
    {
        $this->make = $make;

        // NOTE: 체인에 대한 반환
        return $this;
    }

    public function setModel(string $model): self
    {
        $this->model = $model;

        // NOTE: 체인에 대한 반환
        return $this;
    }

    public function setColor(string $color): self
    {
        $this->color = $color;

        // NOTE: 체인에 대한 반환
        return $this;
    }

    public function dump(): void
    {
        var_dump($this->make, $this->model, $this->color);
    }
}

$car = (new Car())
  ->setColor('pink')
  ->setMake('Ford')
  ->setModel('F-150')
  ->dump();
```

**좋은 예:**

```php
class Car
{
    private $make = 'Honda';
    private $model = 'Accord';
    private $color = 'white';

    public function setMake(string $make): void
    {
        $this->make = $make;
    }

    public function setModel(string $model): void
    {
        $this->model = $model;
    }

    public function setColor(string $color): void
    {
        $this->color = $color;
    }

    public function dump(): void
    {
        var_dump($this->make, $this->model, $this->color);
    }
}

$car = new Car();
$car->setColor('pink');
$car->setMake('Ford');
$car->setModel('F-150');
$car->dump();
```

**[⬆ 위로 가기](#목차)**

## SOLID

**SOLID** 는 Robert Martin이 명명한 5가지 원칙의 앞 글자로 객체지향 프로그래밍과 디자인을 뜻하는 5가지 기본 원칙을 뜻합니다. Michael Feathers가 고안한 니모닉 약어를 사용하였습니다.

 * [S: 단일 책임 원칙 (SRP)](#단일-책임-원칙-srp)
 * [O: 개방/폐쇄 원칙 (OCP)](#개방폐쇄-원칙-ocp)
 * [L: 리스코브 치환 원칙 (LSP)](#리스코브-치환-원칙-lsp)
 * [I: 인터페이스 분리 원칙 (ISP)](#인터페이스-분리-원칙-isp)
 * [D: 의존성 역전 원칙 (DIP)](#의존성-역전-원칙-dip)

### 단일 책임 원칙 (SRP)

클린 코드에서 명시되어 있듯이, "클래스를 변경하는데 한가지 이상의 이유가 있어서는 안 됩니다."
한 클래스를 많은 기능을 꽉 채우는 것은 유혹적입니다. 마치 기내에 딱 하나의 여행용 가방을 가져갈 수 있을 때처럼요.
이것의 문제는 클래스가 개념적으로 일관되지 않게되며 클래스를 변경할 여러 이유를 만들 것이라는 겁니다.
클래스를 변경해야 할 필요가 있을 때 드는 시간을 최소화시키는 것은 중요합니다. 그 이유는
만약, 너무 많은 기능이 한 클래스에 있고 그중 한 부분을 수정해야 한다면 코드 안에 의존하고 있는 다른 모듈에 어떤 영향을 미치는지 파악하기 어렵기 때문입니다.

**나쁜 예:**

```php
class UserSettings
{
    private $user;

    public function __construct(User $user)
    {
        $this->user = $user;
    }

    public function changeSettings(array $settings): void
    {
        if ($this->verifyCredentials()) {
            // ...
        }
    }

    private function verifyCredentials(): bool
    {
        // ...
    }
}
```

**좋은 예:**

```php
class UserAuth
{
    private $user;

    public function __construct(User $user)
    {
        $this->user = $user;
    }

    public function verifyCredentials(): bool
    {
        // ...
    }
}

class UserSettings
{
    private $user;
    private $auth;

    public function __construct(User $user)
    {
        $this->user = $user;
        $this->auth = new UserAuth($user);
    }

    public function changeSettings(array $settings): void
    {
        if ($this->auth->verifyCredentials()) {
            // ...
        }
    }
}
```

**[⬆ 위로 가기](#목차)**

### 개방/폐쇄 원칙 (OCP)

Bertrand Meyer가 말하기를, "소프트웨어 개체(클래스, 모듈, 함수 등)는 확장에 대해서는 개방되어야 하며, 변경에서는 폐쇄되어 있어야 합니다."
이것은 무엇을 의미할까요? 이 원칙은 기본적으로 사용자가 기존 코드를 변경하지 않고 새로운 기능을 추가할 수 있도록 허용해야 한다는 것을 뜻합니다.

**나쁜 예:**

```php
abstract class Adapter
{
    protected $name;

    public function getName(): string
    {
        return $this->name;
    }
}

class AjaxAdapter extends Adapter
{
    public function __construct()
    {
        parent::__construct();

        $this->name = 'ajaxAdapter';
    }
}

class NodeAdapter extends Adapter
{
    public function __construct()
    {
        parent::__construct();

        $this->name = 'nodeAdapter';
    }
}

class HttpRequester
{
    private $adapter;

    public function __construct(Adapter $adapter)
    {
        $this->adapter = $adapter;
    }

    public function fetch(string $url): Promise
    {
        $adapterName = $this->adapter->getName();

        if ($adapterName === 'ajaxAdapter') {
            return $this->makeAjaxCall($url);
        } elseif ($adapterName === 'httpNodeAdapter') {
            return $this->makeHttpCall($url);
        }
    }

    private function makeAjaxCall(string $url): Promise
    {
        // request하고 promise를 return함
    }

    private function makeHttpCall(string $url): Promise
    {
        // request하고 promise를 return함
    }
}
```

**좋은 예:**

```php
interface Adapter
{
    public function request(string $url): Promise;
}

class AjaxAdapter implements Adapter
{
    public function request(string $url): Promise
    {
        // request하고 promise를 return함
    }
}

class NodeAdapter implements Adapter
{
    public function request(string $url): Promise
    {
        // request하고 promise를 return함
    }
}

class HttpRequester
{
    private $adapter;

    public function __construct(Adapter $adapter)
    {
        $this->adapter = $adapter;
    }

    public function fetch(string $url): Promise
    {
        return $this->adapter->request($url);
    }
}
```

**[⬆ 위로 가기](#목차)**

### 리스코브 치환 원칙 (LSP)

단순한 개념을 지칭하는 무시무시해 보이는 용어입니다. 공식적으로는 다음과 같이 정의되어있습니다.
"만약 S가 T의 서브 타입이라면, T 타입의 객체는 프로그램의 바람직한 특성(정합성, 수행된 작업 등)을 하나도 바꾸지 않으면서 S 타입의 객체로 교체될 수 있습니다. (즉, S 타입의 객체는 T 타입의 객체를 대체할 수 있습니다)"
더 무시무시한 정의였네요.

이에 대한 가장 좋은 설명은 다음과 같습니다.
만약 우리가 부모 클래스와 자식 클래스를 가지고 있다면, 부정확한 결과를 얻지 않으면서 기본 클래스와 자식 클래스를 서로 교환하여 사용할 수 있다는 것입니다.
여전히 혼란스러울 수 있으니, 전형적인 정사각형-직사각형 예제를 들어봅시다.
수학적으로 정사각형은 사각형입니다. 그러나, 상속을 통한 'is-a' 관계로 설계하면 빠르게 문제에 휘말리게 됩니다.

**나쁜 예:**

```php
class Rectangle
{
    protected $width = 0;
    protected $height = 0;

    public function render(int $area): void
    {
        // ...
    }

    public function setWidth(int $width): void
    {
        $this->width = $width;
    }

    public function setHeight(int $height): void
    {
        $this->height = $height;
    }

    public function getArea(): int
    {
        return $this->width * $this->height;
    }
}

class Square extends Rectangle
{
    public function setWidth(int $width): void
    {
        $this->width = $this->height = $width;
    }

    public function setHeight(int $height): void
    {
        $this->width = $this->height = $height;
    }
}

/**
 * @param Rectangle[] $rectangles
 */
function renderLargeRectangles(array $rectangles): void
{
    foreach ($rectangles as $rectangle) {
        $rectangle->setWidth(4);
        $rectangle->setHeight(5);
        $area = $rectangle->getArea(); // 땡: 20이어야 하는 데, 정사각형에 25를 return할 것입니다.
        $rectangle->render($area);
    }
}

$rectangles = [new Rectangle(), new Rectangle(), new Square()];
renderLargeRectangles($rectangles);
```

**좋은 예:**

```php
abstract class Shape
{
    abstract public function getArea(): int;

    public function render(int $area): void
    {
        // ...
    }
}

class Rectangle extends Shape
{
    private $width;
    private $height;

    public function __construct(int $width, int $height)
    {
        $this->width = $width;
        $this->height = $height;
    }

    public function getArea(): int
    {
        return $this->width * $this->height;
    }
}

class Square extends Shape
{
    private $length;

    public function __construct(int $length)
    {
        $this->length = $length;
    }

    public function getArea(): int
    {
        return pow($this->length, 2);
    }
}

/**
 * @param Rectangle[] $rectangles
 */
function renderLargeRectangles(array $rectangles): void
{
    foreach ($rectangles as $rectangle) {
        $area = $rectangle->getArea();
        $rectangle->render($area);
    }
}

$shapes = [new Rectangle(4, 5), new Rectangle(4, 5), new Square(5)];
renderLargeRectangles($shapes);
```

**[⬆ 위로 가기](#목차)**

### 인터페이스 분리 원칙 (ISP)

ISP는 "클라이언트는 사용하지 않는 인터페이스에 의존하도록 강요되어서는 안 된다."를 뜻합니다.

이 원칙을 잘 설명해주는 예로는 많은 설정 객체를 요구하는 클래스를 들 수 있겠습니다.
클라이언트가 많은 양의 옵션을 설치하도록 요구하지 않는 것이 이롭습니다. 대부분의 경우, 모든 설치가 필요하지는 않기 때문이죠.
이것들을 선택사항으로 만드는 것이 "뚱뚱한 인터페이스"를 가지는 것을 방지합니다.

**나쁜 예:**

```php
interface Employee
{
    public function work(): void;

    public function eat(): void;
}

class Human implements Employee
{
    public function work(): void
    {
        // .... 일하는 중
    }

    public function eat(): void
    {
        // ...... 점심 휴식 시간에 먹는 중
    }
}

class Robot implements Employee
{
    public function work(): void
    {
        //.... 훨씬 많이 일하는 중
    }

    public function eat(): void
    {
        //.... 로봇은 먹을 수 없지만, 이 메소드를 반드시 implement해야합니다..
    }
}
```

**좋은 예:**

모든 일꾼(worker)이 직원(employee)은 아니지만, 모든 직원(employee)은 '일꾼(worker)' 입니다.

```php
interface Workable
{
    public function work(): void;
}

interface Feedable
{
    public function eat(): void;
}

interface Employee extends Feedable, Workable
{
}

class Human implements Employee
{
    public function work(): void
    {
        // .... 일하는 중
    }

    public function eat(): void
    {
        //.... 점심 휴식시간에 먹는 중
    }
}

// 로봇은 일만 할 수 있어요
class Robot implements Workable
{
    public function work(): void
    {
        // .... 일하는 중
    }
}
```

**[⬆ 위로 가기](#목차)**

### 의존성 역전 원칙 (DIP)

이 원칙은 두 가지 필수 사항을 명시합니다.
1. 상위 레벨의 모듈은 하위 레벨의 모듈에 의존해서는 안 됩니다. 상위 레벨과 하위 레벨의 모듈 모두 추상화에 의존해야 합니다.
2. 추상화된 것은 구체적인 것에 의존하면 안 됩니다. 구체적인 사항들은 추상화에 의존해야 합니다.

한 번에 이해하기는 어려울 수 있습니다. 하지만 만약 당신이 PHP 프레임워크(symfony 등)를 사용해왔다면, 의존성 주입(DI, Dependency Injection)폼 안에 해당 원칙이 구현된 것을 보아왔을 것입니다.
같은 개념은 아니지만, DIP는 상위 레벨 모듈들이 하위 레벨 모듈의 세부 사항을 알지 못하게 하고 그것들을 설정하는 것을 막습니다.
이것은 의존성 주입을 통해서 완수할 수 있습니다. 의존성 주입의 가장 큰 장점은 모듈 간의 결합을 줄일 수 있다는 것입니다.
결합은 아주 안 좋은 개발 패턴입니다. 그 이유는 우리의 코드를 리팩토링하기 어렵게 만들기 때문입니다.

**나쁜 예:**

```php
class Employee
{
    public function work(): void
    {
        // ....일하는 중
    }
}

class Robot extends Employee
{
    public function work(): void
    {
        //....훨씬 더 많이 일하는 중
    }
}

class Manager
{
    private $employee;

    public function __construct(Employee $employee)
    {
        $this->employee = $employee;
    }

    public function manage(): void
    {
        $this->employee->work();
    }
}
```

**좋은 예:**

```php
interface Employee
{
    public function work(): void;
}

class Human implements Employee
{
    public function work(): void
    {
        // ....일하는 중
    }
}

class Robot implements Employee
{
    public function work(): void
    {
        //....훨씬 더 많이 일하는 중
    }
}

class Manager
{
    private $employee;

    public function __construct(Employee $employee)
    {
        $this->employee = $employee;
    }

    public function manage(): void
    {
        $this->employee->work();
    }
}
```

**[⬆ 위로 가기](#목차)**

## 반복하지 마세요 (DRY)

[DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) 원칙을 지키도록 노력하세요.

중복코드를 피하고자 정말 최선을 다하세요. 중복된 코드는 나쁩니다. 만약 우리가 어떤 로직을 변경해야 할 때 고칠 곳이 한 곳 이상이라는 것을 뜻하기 때문이죠.

우리가 레스토랑을 운영하고 있다고 상상해보세요. 그리고 재고(토마토, 양파, 마늘, 양념 등등)를 기록하고 있다고요.
만약 우리가 이걸 기록하는 여러 개의 목록을 가지고 있다면, 토마토가 들어간 요리를 서빙할 때마다 모든 목록을 수정해야 할 겁니다.
만약 단 하나의 목록만 가지고 있다면, 수정할 곳은 단 한 곳뿐이겠지요!

종종 우리는 중복된 코드를 가집니다. 사소하게 다른 두어 개 때문인데, 많은 부분을 같이 공유하지만, 그 사소한 차이점이
거의 같은 일을 하는 두 개 이상의 서로 다른 함수를 만들어내게 합니다. 중복된 코드를 제거하는 것은 단 하나의 함수/모듈/클래스로 서로 다른 세트를 핸들 할 수 있는 추상화를 생성하는 것을 뜻합니다.

올바른 추상화를 갖는 것은 중요합니다. 그것이 [클래스](#클래스) 섹션에 있는 SOLID 원칙을 따라야 하는 이유입니다.
나쁜 추상화는 중복된 코드보다 나쁠 수 있습니다. 그러니 조심하세요!
지금껏 말했듯이, 좋은 추상화를 만들 수 있다면 그렇게 하세요!
같은 것을 반복 하지 마세요, 그렇지 않으면 하나를 바꾸려 할 때마다 여러 군데를 수정하고 있는 우리 자신을 발견하게 될 테니까요.

**나쁜 예:**

```php
function showDeveloperList(array $developers): void
{
    foreach ($developers as $developer) {
        $expectedSalary = $developer->calculateExpectedSalary();
        $experience = $developer->getExperience();
        $githubLink = $developer->getGithubLink();
        $data = [
            $expectedSalary,
            $experience,
            $githubLink
        ];

        render($data);
    }
}

function showManagerList(array $managers): void
{
    foreach ($managers as $manager) {
        $expectedSalary = $manager->calculateExpectedSalary();
        $experience = $manager->getExperience();
        $githubLink = $manager->getGithubLink();
        $data = [
            $expectedSalary,
            $experience,
            $githubLink
        ];

        render($data);
    }
}
```

**좋은 예:**

```php
function showList(array $employees): void
{
    foreach ($employees as $employee) {
        $expectedSalary = $employee->calculateExpectedSalary();
        $experience = $employee->getExperience();
        $githubLink = $employee->getGithubLink();
        $data = [
            $expectedSalary,
            $experience,
            $githubLink
        ];

        render($data);
    }
}
```

**아주 좋은 예:**

더 간결한 코드를 사용하는게 나은 것 같군요.

```php
function showList(array $employees): void
{
    foreach ($employees as $employee) {
        render([
            $employee->calculateExpectedSalary(),
            $employee->getExperience(),
            $employee->getGithubLink()
        ]);
    }
}
```

**[⬆ 위로 가기](#목차)**

## 번역

다른 언어로도 읽으실 수 있습니다.

* :cn: **중국어:**
   * [php-cpm/clean-code-php](https://github.com/php-cpm/clean-code-php)
* :ru: **러시아어:**
   * [peter-gribanov/clean-code-php](https://github.com/peter-gribanov/clean-code-php)
* :es: **스페인어:**
   * [fikoborquez/clean-code-php](https://github.com/fikoborquez/clean-code-php)
* :brazil: **포르투갈어:**
   * [fabioars/clean-code-php](https://github.com/fabioars/clean-code-php)
   * [jeanjar/clean-code-php](https://github.com/jeanjar/clean-code-php/tree/pt-br)
* :thailand: **태국어:**
   * [panuwizzle/clean-code-php](https://github.com/panuwizzle/clean-code-php)
* :fr: **불어:**
   * [errorname/clean-code-php](https://github.com/errorname/clean-code-php)
* 🇰🇷 **한국어:**
  * [yujineeee/clean-code-php](https://github.com/yujineeee/clean-code-php)


**[⬆ 위로 가기](#목차)**
