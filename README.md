# Ruby notes
这是我学习Ruby的笔记，从2017年6月14日正式开始学。

## Table of content
  - [Method](#method)
    - [Defining a Method](#defining-a-method)
    - [Calling a Method](#calling-a-method)
    - [Return Value](#return-value)
    - [Optional Parameter](#optional-parameter)
    - [Private method](#private-method)
  - [Parameter](#parameter)
    - [Optional Parameter](#optional-parameter)
    - [Required parameter](#required-parameter)
    - [Array parameter](#array-parameter)
    - [Keyword parameter](#keyword-parameter)
    - [Block parameter](#block-parameter)
    - [Parameter order](#parameter-order)
  - [Class](#class)
    - [Defining a Class](#defining-a-class)
    - [Creating an Instance](#creating-an-instance)
    - [Attribute Accessor Methods](#attribute-accessor-methods)
    - [Inheritance, Subclass and Superclass](#inheritance-subclass-and-superclass)
    - [The Super Keyword](#the-super-keyword)
    - [Class Method](#class-method)
  - [Block](#block)
    - [Defining a Block](#defining-a-block)
    - [Yielding to a Block](#yielding-to-a-block)
    - [Lambda](#lambda)
  - [Hash](#hash)
    - [Defining a Hash](#defining-a-hash)
    - [Accessing the Key's Value](#accessing-the-keys-value)
    - [Adding new Key](#adding-new-key)
    - [Setting the Default value for a key](#setting-the-default-value-for-a-key)
    - [Keyword argument](#keyword-argument)
  - [Module as mixin](#module-as-mixin)
    - [Defining a module](#defining-a-module)
    - [Mixing in a module](#mixing-in-a-module)
    - [Inheritance sequence](#inheritance-sequence)
  - [Flow Control](#flow-control)
  - [Variable, constant and scope](#variable-constant-and-scope)
    - [Variable](#variable)
    - [Constant](#constant)

## Method
一个method其实就是可以完成某一任务的功能块，可以多次被利用。

### Defining a Method
一个method可以包含parameter, 或不包含parameter.

包含parameter。

```ruby
def say(message)
  message
end
```

不包含parameter。

```ruby
def sit
  # code to perform sit
end
```

### Calling a Method
当一个method没有参数时，直接写method的名字即可，可不写小括号()。如

```ruby
# call a method without any parameter
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

## Private method
You cannot call private method directly on object. They can only be called inside other method.

```ruby
class Message
	attr_accessor :text

	def initialize(text) 
		@text = text
	end

	def send(from, to)

	end

	def call_private_method
		secret
	end

	private
		def secret
			'This is a private method and you cannot call it on object directly.'
		end
end
```

## Parameter

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

### Required parameter
上面的`say` method的`message`参数就是一个required parameter。

### Array parameter
一个array parameter的前面以`*`开头。在如下例子中，`params`就是一个array parameter，所有跟着`required_param`的参数都会装进这个叫params的数组里。

```ruby
def method_name(required_param, *params)
  # params is an array
  params
end
```

### Keyword parameter
### Block parameter
### Parameter order

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
你不可以直接来获取或更改对象的instance variable, 如在上面的`liubei`对象中，如果你输入如下代码，将会出错。

```ruby
# try to access the instance variable called @birthplace
liubei.@birthplace
```

你必须在类里面定义一些方法来获取或更改instance variable。下面在Character这个类里面定义一些方法来获取和更改instance variable。

```ruby
class Character
  def initialize(name, birthplace, height)
    @name = name
    @birthplace = birthplace
    @height = height
  end

  # an attribute reader method which returns the @name
  def name
    @name
  end

  # an attribute writer method which sets the @name
  def name=(name)
    @name = name
  end

  def say(message)
    # code to perform the say
  end
end

# now if you run these code, you can get access to the instance variable @name
liubei.name
# reset the @name
liubei.name = "玄德"
```

Ruby提供了3个方法，可以快捷地定义一些attribute accessor method

1. `attr_accessor => 相当于同时包含attr_reader和attr_writer两个方法`
2. `attr_reader`
3. `attr_writer`

在上面Character这个类里，你可以直接写

```ruby
attr_accessor :name
```

### Inheritance, Subclass and Superclass
在superclass的基础上，建立一个subclass。在以下的例子中，Soldier 是一个subclass, 继承于Character这个superclass。

```ruby
class Soldier < Character
  def march(direction)
    # code to march somewhere
  end
end
```

### The Super Keyword
### Class Method

## Block
代码块，你可以在一个method中调用代码块。代码块看起来和method很相似，都可以接受参数和不接受参数，和返回值。不同之一是代码块没有名字。

### Defining a Block
代码块有两种形式。一种是`do...end`, 另一种是`{}`。

```ruby
do
  puts "yield to a block"
end
```

```ruby
{ puts "yield to a block" }
```

block通常与method一起使用，下面定义一个含有block作为参数的method.

```ruby
def method_name(&block_name)
  # call the block
  block_name.call
end
```

以上的例子中，代码块没有参数。下面的例子中，代码块包含参数，注意参数是用`||`包围着，与method用`()`不同。

```ruby
# define a User class
class User
  attr_accessor :name, :description

  def initialize(name, description)
    @name = name
    @description = description
  end

  def login
    # code to log in
  end
end

# an array to store the User
users = []

# create some User instance
users.push(User.new("Mary", "Hello, I am..."))
users.push(User.new("Lucy", "Hi, Nice to meet you."))

# greeting each user
users.each do |user|
  puts "Hi #{user.name}, Welcome to the Ruby zone and happy coding."
end
```

### Yielding to a Block
定义一个调用代码块的method。

```ruby
# accept an array and do sth with each element
def each_it(array)
  index = 0
  while index < array.length
    yield(array[index])
    index += 1
  end
end

# call each_it
prices = [9, 7, 9]
# say now there is a 10% discount, output the discount
each_it(prices) do |price|
  puts "You save #{price * 0.1}."
end
```

### Lambda



## Hash
Hash是一个key-value对的集合.

### Defining a Hash
可使用hash literal {}方式来建立一个hash，或使用Hash这个类来建立一个hash。

```ruby
city = {
  name: "广州",
  population: 2000,
  zones: ["天河", "越秀"]
}
```

使用Hash这个类。

```ruby
city = Hash.new
```

### Accessing the Key's Value
使用[]获取hash里的key的value。

```ruby
# get the city name
city[:name]
# get the city zones
city[:zones]
```

当你尝试去获取一个不存在的key时，返回值为nil。

```ruby
# return nil because location is not a key of the city
city["location"]
```

### Adding new Key
同样使用[]来增加新的key。

```ruby
city[:weather] = "Sunny"
```

### Setting the Default value for a key
设置key的默认值。

```ruby
bookself = Hash.new(0)
# now if try to get access to a key called color, you get 0 instead of nil
bookself["color"]
```

## Module as mixin
模块是一些方法的集合，很灵活。类是模块的一种。你可使用模块来扩充类。

### Defining a module

```ruby
module MyModule
  def first_method
    puts "fist_method called"
  end

  def second_method
    puts "second_method called"
  end
end
```

### Mixing in a module
使用include这个关键词在类里面添加一个模块。模块里的方法都变成类里面的实例方法。

```ruby
class MyClass
  include MyModule
end
```

### Inheritance sequence
当你调用一个对象的实例方法时，Ruby首先会在这个对象的类里寻找这个方法。当找不到时，它先会从已添加的模块里找，找到了即停止。如果找不到，会接着在superclass里找。

## Flow Control

## Variable, constant and scope

### Variable
需用不同的符号来表示不同的变量和作用域。

Variable | Sign | Scope
--- | --- | ---
global variable | $name | global
local variable | name | local
instance variable | @name | instance method
class variable | @@name | class method and instance method
class instance variable | @name | class method

### Constant
