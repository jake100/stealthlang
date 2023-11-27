# stealthlang
Scripting language called stealth. Uses indentation-based syntax with optional parenthesis.



```
#python style comments

#import statement, file extension is .stlf

import otherFile.stlf
import library.stlf as lib

#global variables

final title = "stealth"
num = 42

#main: is the entry point
main:
	i = 5
  	j = 2, k = 4, l = 8

	randNum = rnd(5)
	randRange = rnd(1, 8)
	randInt = rnd(int)
	randFloat = rnd(float)
	randString = rnd(string)
	randChar = rnd(char)

	alive = true
	dead = false

	notHere = null

	#optional typing
	bool b = true
	int xNum = 0, yNum = 0
	long xLong = 0L, yLong = 0L
	float xx = 0.0f, yy = 0.0f
	double xxx = 0.0, yyy = 0.0
	string str = ""
	char c = 'a'

	#all arrays, lists, maps, sets and classes are tables
	array = [0, "1", '2']
	list = {0, "1"}
	map = (a: "this is a", b: "this is b")
  	otherMap = (0: "cat", 1: "dog", 2: "mouse")
	set = |0, 1, 2, 3|
	table = <tString = "hello", tNum = 4, tFunc: return tString + ", " + tNum>

	print table.tFunc

	print array.len

  	#list is used like a list and a stack
	list.push('2')
  	list.pop()

	lib.libFunc, print lib.libValue

  	final xRange = 4
  	xText = "This is x: "

	for x in range xRange:
		print xText + x

  	for x in array:
    		print x

	for key, value in array:
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

	Cat cat = new Cat(5, 5)
	Tiger tiger = new Tiger(10, 10)

	cat.meow, cat.meow, cat.meow
	tiger.meow, tiger.meow, tiger.meow

  	cat.catStuff, tiger.catStuff

func:
	print "hello"

otherFunc:
	print "hi"


funcParam(x, y):
	return x * y

typedParam(int x, int y):
	return x + y

constantFunc:

	final

	string s = "this can't be changed, "
	string ss = "this also, "
	string sss = "etc.."

	return s + ss + sss

#a type infront of a function means the function has to return that type
string catFunc:
	int x = 5, y = 4
	bool b = true
	string s = "string text", ss = "other text"
	

	// .. concatenates anything to anything
	return b .. x .. y + ", " + s + ", " + ss

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
	#makes everything after this final
	final

	teeth = "sharp"
	eyes = "wide open"


class Tiger is a Cat:
	claws = "sharp"
	
	public

	growl:
		print "growl"
	
	protected
	
	meow:
		print "grrr"
```
