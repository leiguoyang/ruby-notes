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

从一个method会return回来什么值呢？一个method中的最后一个表达式会自动作为返回值。通常，不用写return这个关键词。如

```ruby
def buy?(money)
  # if the money in pocket is no less than 10 yuan, return true, in other words, buy it
  money >= 10
end
```

### Instance Method
### Class Method

## Class

## Block

## Hash

## Mixin

