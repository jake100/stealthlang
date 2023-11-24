# stealthlang
Scripting language called stealth. Uses indentation-based syntax with optional parenthesis.



```
#python style comments

#main: is the entry point
main:
	i = 5
  j = 2, k = 4, l = 8

	arr = [0, "1", '2']
	list = {0, "1"}
	map = (a: "this is a", b: "this is b")
  otherMap = (0: "cat", 1: "dog", 2: "mouse")

  #list is used like a list and can be used like a stack, all are tables like lua, classes are also tables
	list.push('2')
  list.pop()

  xRange = 4
  xText = "This is x: "

	for x in range xRange:
		print xText + x

  for x in arr:
    print x

	for key, value in arr:
		print key + ", " + value

  for key, value in map:
    print key + ", " + value
	
	while i > 0:
		print i--

	if x < 5:
		print "true"

	elif x == 4:
		print "elif"

	else:
		print "else"

  #optional parentesis means a function can be called like this or called one after another with , inbetween function calls
	func
	func, otherFunc, func, otherFunc, func, func, func, otherFunc, otherFunc, otherFunc

	print funcParam(5, 5), print funcParam(6, 6), print funcParam(7, 7)

func:
	print "hello"

otherFunc:
	print "hi"

funcParam(x, y):
	return x * y

	Cat cat = new Cat(5, 5)
	Tiger tiger = new Tiger(10, 10)

	cat.meow, cat.meow, cat.meow
	tiger.meow, tiger.meow, tiger.meow

  cat.catStuff, tiger.catStuff

class Cat:
  #members are private by default, public or protected can be called, then later members are st to either public or protected
	x, y = 0
	Cat(x, y):
    #this is used to make the following variables to this, x and y is mapped to the private x and y members
		this x, y = x, y
	privateFunction:
		print "private"
	public 
	
	catStuff:
		print "do cat stuff"

	protected
	
	meow:
		print "meow"

class Tiger is a Cat:
	claws = "sharp"
	
	public

	growl:
		print "growl"
	
	protected
	
	meow:
		print "grrr"
```
