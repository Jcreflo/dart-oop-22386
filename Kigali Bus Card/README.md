# Dart OOP Assignment: Kigali Bus Card

**Name:** Creflo Johson Manjoe  
**Student ID:** 22386

## My numbers

- D = 86
- L = 6
- Starting balance = 1,860 RWF
- Bus fare = 286 RWF
- Student discount = 16%

## Output of main.dart

```text
Error: name too short
Owner: Creflo Johson Manjoe | Balance: 1860 RWF
Owner: Creflo Johson Manjoe | Balance: 1860 RWF
Error: top-up must be 500 to 50000 RWF
Topped up 2000 RWF
Paid 286 RWF
Paid 286 RWF
Owner: Creflo Johson Manjoe | Balance: 3288 RWF
Student discount: 45 RWF
Paid 241 RWF
Owner: Creflo Johson Manjoe | Balance: 1619 RWF
Student card: 16% off
```

## Part 1: Why no setter for balance?

Without a balance setter, code cannot assign an arbitrary balance and bypass the card's payment and top-up rules. The balance changes only through the card's methods.

## Part 2: What does ~/ do?

`/` performs division and gives a decimal result: `237 * 17 / 100` is `40.29`. `~/` performs integer division and drops the fractional part: `237 * 17 ~/ 100` is `40`.

## Part 4: Bug table

| Bug | The line | Why it is wrong | Your fix |
|---|---|---|---|
| 1 | `String _brand;` and `int _battery;` | Non-nullable fields need initial values before the constructor body assigns them. | Initialize them to `''` and `0`. |
| 2 | `SmartPhone(String brand, int battery, String system) {` | The `Phone` parent constructor must run to initialize its fields. | Add `: super(brand, battery)`. |
| 3 | `@override void restart()` in `SmartPhone` | `Phone` does not declare a `restart` method to override. | Add `restart()` to `Phone`. |
| 4 | `p.battery = 100;` | The getter does not allow assignment, so a setter is missing. | Add a setter that accepts values from 0 to 100. |
| 5 | `print(p.battery());` | `battery` is a getter property, not a method. | Use `print(p.battery);`. |
| Not a bug | `Phone p = new Phone('Tecno', 50);` | `new` is optional in Dart but still valid syntax. | No change needed. |

## Part 5

My prediction before running the code: it prints `1` and then `4`. I think each `BigBag.add()` call adds one item, and the final assignment adds one more.

Real output:

```text
1
5
```

Was I right? Not completely. The first output was right, but each `BigBag.add()` calls the parent's `add()` twice, so the two calls add 4 items. The final assignment adds 1 more, making 5. My corrected prediction is `1` and then `5`.
