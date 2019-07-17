# Enumerations lab

Fork and clone this repo. On your fork, answer and commit the follow questions. When you are finished, submit the link to your repo on Canvas.


## Question 1

a) Define an enumeration called `iOSDeviceType` with member values `iPhone`, `iPad`, `iWatch`. Create a variable called `myDevice` and assign it one member value.

b) Adjust your code above so that `iPhone` and `iPad` have associated values of type String which represents the model number, eg: `iPhone("6 Plus")`. Use a switch case and let syntax to print out the model number of each device.

//a) Define an enumeration called `iOSDeviceType` with member values `iPhone`, `iPad`, `iWatch`. Create a variable called `myDevice` and assign it one member value.

enum IOSDeviceType {
case iPhone
case iPad
case iWatch
}

//b) Adjust your code above so that `iPhone` and `iPad` have associated values of type String which represents the model number, eg: `iPhone("6 Plus")`. Use a switch case and let syntax to print out the model number of each device.

enum IOSDeviceType {

case iPhone(String)
case iPad(String)
case iWatch(String)

}

let deviceModel = IOSDeviceType.iPhone("8 Plus")

switch deviceModel {

case .iPhone(let modelType):
print("This is an iPhone \(modelType)")
case .iPad(let modelType):
print("This is an iPad \(modelType)")
case .iWatch(let modelType):
print("This is an iWatch \(modelType)")

}


## Question 2

a) Write an enum called `Shape` and give it cases for `triangle`, `rectangle`, `square`, `pentagon`, and `hexagon`.

b) Write a method inside `Shape` that returns how many sides the shape has. Create a variable called `myFavoritePolygon` and assign it to one of the shapes above, then print out how many sides it has.

c) Re-write `Shape` so that each case has an associated value of type Int that will represent the length of the sides (assume the shapes are regular polygons so all the sides are the same length) and write a method inside that returns the perimeter of the shape.

//a) Write an enum called `Shape` and give it cases for `triangle`, `rectangle`, `square`, `pentagon`, and `hexagon`.

enum Shape {
case triangle
case rectangle
case square
case pentagon
case hexagon
}

//
//    b) Write a method inside `Shape` that returns how many sides the shape has. Create a variable called `myFavoritePolygon` and assign it to one of the shapes above, then print out how many sides it has.
//
enum Shape {
case triangle
case rectangle
case square
case pentagon
case hexagon

func printTheShape() {

switch self {

case .triangle:
print("Three sides")
case .rectangle:
print("Four sides")
case .square:
print("Four sides")
case .pentagon:
print("Five sides")
case .hexagon:
print("Six sides")
}
}
}

var myFavoritePolygon = Shape.rectangle

myFavoritePolygon.printTheShape()


//
//    c) Re-write `Shape` so that each case has an associated value of type Int that will represent the length of the sides (assume the shapes are regular polygons so all the sides are the same length) and write a method inside that returns the perimeter of the shape.

enum Shape {

case triangle(Int)
case rectangle(Int)
case square(Int)
case pentagon(Int)
case hexagon(Int)

func perimiter() {

switch self {

case .triangle(let sides):
print(sides * 3)
case .rectangle(let sides):
print(sides * 4)
case .square(let sides):
print(sides * 4)
case .pentagon(let sides):
print(sides * 5)
case .hexagon(let sides):
print(sides * 6)

}

}

}
let polygonPerimiter = Shape.triangle(5)
polygonPerimiter.perimiter()


## Question 3

Write an enum called `OperatingSystem` and give it cases for `windows`, `mac`, and `linux`. Create an array of 10 `OperatingSystem` objects where each one is set to a random operating system. Then, iterate through the array and print out a message depending on the operating system.


enum OperatingSystem {

case windows
case mac
case linux

}


enum OperatingSystem {
case windows
case mac
case linux
case four
case five
case six
case seven
case eight
case nine
case ten
}


var operatingSystemArray: [OperatingSystem] = [OperatingSystem.windows, OperatingSystem.mac, OperatingSystem.linux, OperatingSystem.four, OperatingSystem.five, OperatingSystem.six, OperatingSystem.seven, OperatingSystem.eight, OperatingSystem.nine, OperatingSystem.ten]

for i in operatingSystemArray {
switch i {
default:
print(i)
}
}



## Question 4

You are working on a game in which your character is exploring a grid-like map. You get the original location of the character and the steps he will take.

- A step .up will increase the y coordinate by 1.
- A step .down will decrease the y coordinate by 1.
- A step .right will increase the x coordinate by 1.
- A step .left will decrease the x coordinate by 1.
- Print the final location of the character after all the steps have been taken.

```swift
enum Direction {
    case up
    case down
    case left
    case right
}

var location = (x: 0, y: 0)
var steps: [Direction] = [.up, .up, .left, .down, .left]

// your code here
```

enum Direction: String {
case up
case down
case left
case right
}

var location = (x: 0, y: 0)
var steps: [Direction] = [.up, .up, .left, .down, .left]

for direction in steps {
print("The current location is at x: \(location.x) and y: \(location.y)")
print("I am about to go \(direction)")
switch direction {
case .up:
location.y += 1
case .down:
location.y -= 1
case .left:
location.x -= 1
case .right:
location.x += 1
}
}

print("The final location is: \(location)")



## Question 5

a) Define an enumeration named `HandShape` with three members: `.rock`, `.paper`, `.scissors`.

b) Define an enumeration named `MatchResult` with three members: `.win`, `.draw`, `.lose`.

c) Write a function called `match` that takes two `HandShapes` and returns a `MatchResult`. It should return the outcome for the first player (the one with the first hand shape).

Hint: Rock beats scissors, paper beats rock, scissor beats paper

enum HandShape {

case rock
case paper
case scissors

}

enum MatchResult {

case win
case lose
case draw

}

func match(firstShape: HandShape, secondHandShape: HandShape) -> MatchResult {
switch firstShape {
case .rock:
switch secondHandShape {
case .rock: return .draw
case.paper: return .lose
case.scissors: return .win
}
case .paper:
switch secondHandShape {
case .rock: return .win
case .paper: return .draw
case .scissors: return .lose
}
case.scissors:
switch secondHandShape {
case .rock: return .lose
case .paper: return .win
case .scissors: return .draw
}
}
}



## Question 6

a) You are given a `CoinType` enumeration which describes different coin values. Print the total value of the coins in the array `moneyArray` which contains tuples of type (`quantity`, `CoinType`).

```swift
enum CoinType: Int {
    case penny = 1
    case nickle = 5
    case dime = 10
    case quarter = 25
}

var moneyArray:[(Int,CoinType)] = [(10,.penny),
                                   (15,.nickle),
                                   (3,.quarter),
                                   (20,.penny),
                                   (3,.dime),
                                   (7,.quarter)]

// your code here
```

enum CoinType: Int {
case penny = 1
case nickle = 5
case dime = 10
case quarter = 25
}

var moneyArray:[(Int,CoinType)] = [(10,.penny),
(15,.nickle),
(3,.quarter),
(20,.penny),
(3,.dime),
(7,.quarter)]

var sum = 0

for i in moneyArray {

sum += (i.0 * i.1.rawValue)

}
print(sum)


b) Write a method in the `CoinType` enum that returns an Int representing how many coins of that type you need to have a dollar. Then, create an instance of `CoinType` set to `.nickle` and use your method to print out how many nickels you need to have to make a dollar.

enum CoinType: Int {
case penny = 1
case nickle = 5
case dime = 10
case quarter = 25

func printToDollar() {

switch self {
case .penny:
print(100 / rawValue)
case .nickle:
print(100 / rawValue)
case .dime:
print(100 / rawValue)
case .quarter:
print(100 / rawValue)
}

}

}

let thisIsMyCoin = CoinType.nickle
thisIsMyCoin.printToDollar()



## Question 7

a) Write an enum called `DayOfWeek` to represent the days of the week with a raw value of type String.

b) Given the array `poorlyFormattedDays`, write code that will produce an array of enums that match the days.

`let poorlyFormattedDays = ["MONDAY", "wednesday", "Sunday", "monday", "Tuesday", "WEDNESDAY", "thursday", "SATURDAY", "tuesday", "FRIDAy", "Wednesday", "Monday", "Friday", "sunday"]`

c) Write a method in `DayOfWeek` called `isWeekend` that determines whether a day is part of the weekend or not and write code to calculate how many week days appear in `poorlyFormattedDays`.

//a) Write an enum called `DayOfWeek` to represent the days of the week with a raw value of type String.

enum DayOfWeek: String {

case monday = "Monday"
case tuesday = "Tuesday"
case wednesday = "Wednesday"
case thursday = "Thursday"
case friday = "Friday"
case saturday = "Saturday"
case sunday = "Sunday"

}

//b) Given the array `poorlyFormattedDays`, write code that will produce an array of enums that match the days.

enum DayOfWeek: String {

case monday = "Monday"
case tuesday = "Tuesday"
case wednesday = "Wednesday"
case thursday = "Thursday"
case friday = "Friday"
case saturday = "Saturday"
case sunday = "Sunday"

}

let poorlyFormattedDays = ["MONDAY", "wednesday", "Sunday", "monday", "Tuesday", "WEDNESDAY", "thursday", "SATURDAY", "tuesday", "FRIDAy", "Wednesday", "Monday", "Friday", "sunday"]

var poorlyLowercase: [String] = []

var enumArray:[DayOfWeek] = []

for i in poorlyFormattedDays {
poorlyLowercase.append(i.lowercased())
}
print(poorlyLowercase)

for i in poorlyLowercase {

enumArray.append(DayOfWeek)

}
print(enumArray)


## Question 8

a) Create an enum called `MetroLine` with cases for the colors of the metro train lines. Create an instance of `MetroLine`.

b) Modify your enum so that each case has an associated value of either Character or Int that will represent the train on that line. Create a new instance of `MetroLine` and give it an appropriate train letter or number.

c) Write code that prints the train letter or number of your instance of `MetroLine`.

a) Create an enum called `MetroLine` with cases for the colors of the metro train lines. Create an instance of `MetroLine`.

enum MetroLine {

case blue
case red
case yellow
case orange
case green

}
MetroLine.blue

b) Modify your enum so that each case has an associated value of either Character or Int that will represent the train on that line. Create a new instance of `MetroLine` and give it an appropriate train letter or number.

enum MetroLine: String {

case blue = "A"
case red = "1"
case yellow = "Q"
case orange = "F"
case green = "6"

}

MetroLine.blue.rawValue


c) Write code that prints the train letter or number of your instance of `MetroLine`.

enum MetroLine: String {

case blue = "A"
case red = "1"
case yellow = "Q"
case orange = "F"
case green = "6"

func printTrainLine() {

switch self {

case .blue:
print(rawValue)
case .red:
print(rawValue)
case .yellow:
print(rawValue)
case .orange:
print(rawValue)
case .green:
print(rawValue)

}

}

}

var greenLine = MetroLine.green
greenLine.printTrainLine()



## Question 9

a) Think of your own example of something that can be modeled as an enum and write it. Remember that enums allow you to create instances of a defined list of cases.

b) Add a method to your enum.... try to have the method make sense.
