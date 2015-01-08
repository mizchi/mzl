# Mzl language

Language for all caffeinist

This is just what I plan if I implement altjs for es6 era. No implementation yet :)

## Difference from coffeescript

- no scope variable
- es6 with types target

## Specs

```coffee
# variable declaration
let a = 3
let b: number = 3
# destructive assignment
let {x: number, y, z} = {x: 1, y: 2, z: 3}
let [x: number, y, z] = [1, 2, 3]

# function
let f = => true
let id = (n) => n
let square: (n: number) => number = (n) => n * n
double(n: number): number => n * n

# if
if true
  console.log 'a'
else
  throw 'dont come here'

# if returns value
a =
  if Math.random() > 0.5
    1
  else
    2

# switch
a = switch undefined
  when 1
    true
  else
    false

# for
for i in [1, 2, 3]
  i

arr =
  for i in [1, 2, 3]
    i * 2

arr2 =
  for k, v of {a: 1, b: 2}
    k * v

# class syntax
class Point
  x: number
  y: number

  constructor(@x, @y)

class Point3d extends Point
  z: number
  constructor(@x, @y, @z)

class X
  @staticMember: number
  @staticFunc(): number => 1

  member: number
  optionalMember: ?number

  f(arg1: number, arg2: string): number
    arg1 * arg2.length

  _p: p
  get prop() = @_p
  set prop(@_p)

```

Easy to convert to es6 is important.

All type checking was delegated to flow typecheck or others (atscript? It only take syntax)


## Optional features

Just what I want if it can.

```coffee
# trait (if it can
trait Measurable
  x: number
  y: number
  measure(other: Measurable): number
    Math.sqrt(
      Math.pow(@x - other.x, 2) + Math.pow(@y * other.y, 2)
    )

p = new Point(1, 2) with Measureable
p.measure(new Point(3, 4)) # => measure

lazyfunc(): async number
  setTimeout =>
    resolve 3
  , 100

  setTimeout =>
    reject
  , 300

let v: number = await lazyfunc()

# match
let v =
  match t
    case instanceof X => 1
    case typeof X => 100
    case & > 3
      2
    else
      3

# ruby like shorthand function
[1..3].map &.toString()
```
