# Ruby notes
这是我学习Ruby的笔记，我用的书是`Head First Ruby`，从2017年6月14日正式开始学。

## Method
一个method其实就是可以完成某一任务的功能块，可以多次被利用。就像你造了一个锤子，你可以用来敲核桃，也可以用来锤其它东西。为什么叫method呢？ 可不可以叫function?

### Defining a Method
一个method可以包含parameter, 或不包含parameter.

包含parameter。

```ruby
def say(message)
  puts message
end
```

不包含parameter。

```ruby
def sit
  # code to perform sit
end
```

### Calling a Method
当一个method没有参数时，直接写method的名字即可，无需小括号()。如

```ruby
# call a method without any parameter, please omit the parentheses
sit
```

当一个method有参数时，通常需要用小括号()。如

```ruby
# when calling a method with parameters, you hsould always include parentheses
say("Why do you want to learn Ruby? Do you want to make apps with it?")
```

那为什么`puts`, `print`和`p`这些method不用()？奇怪。

### Return Value
从一个method会返回什么值呢？一个method中的最后一个表达式会自动作为返回值。通常，不用写return这个关键词。如

```ruby
def buy?(money)
  # if the money in pocket is no less than 10 yuan, return true, in other words, buy it
  money >= 10
end
```

### Optional Parameter
Optional parameter指非必须的参数，当你调用一个有optional parameter
的method时，你可以提供argument或不提供。下面定义一个有optional parameter的method。

```ruby
def order(juice = "orange")
  puts "This is your #{juice}"
end

# call the method with no argument
order
```

## Class
定义一个类，你可以用这个类来建立很多个不同的例子。如定义一个叫Character类，你可以建立多个有不同名字，性格的例子。

### Defining a Class
类的名称必须以大写字母开头，如一个叫Character的类。在类里面，可使用initialize这个method来初始化一些变量(instance variable)，及定义一些instance method。

```ruby
class Character
  def initialize(name, birthplace, height)
    @name = name
    @birthplace = birthplace
    @height = height
  end

  def say(message)
    # code to perform the say
  end
end
```

在上面这个例子, @name, @birthplace和@height叫做instance variable，而say叫做intance method.

### Creating an Instance
建立一个例子。

```ruby
# create a new instance of the Character class
liubei = Character.new("刘备", "somewhere", "7尺");
# call an instance method
liubei.say("何不。。。")
```

### Attribute Accessor Methods

### Inheritance, Subclass and Superclass
在superclass的基础上，建立一个subclass。在以下的例子中，Soldier 是一个subclass, 继承于Character这个superclass。

```ruby
class Soldier < Character
  def march(direction)
    # code to march somewhere
  end
end
```

### Class Method

## Block

## Hash

## Mixin

