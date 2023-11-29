# stealthlang
Scripting language called stealth. Uses indentation-based syntax with optional function parenthesis and optional static typing. It's Python mixed with Lua with some Java so far mostly.



```
#python style comments

#java style multiline comment
/*
this is all in a multiline comment.
this also
etc...
*/

#import statement, file extension is .stlf
import otherFile.stlf
import library.stlf as lib

#global variables
final title = "stealth"
num = 42

enum Type:
	Off, Low, Medium, High

#main: is the entry point
main:
	#dynamic typing by default
	i = 5
  	j = 2, k = 4, l = 8

	Type type = Off

	match type:
		Off => print "off"
		Low => print "low"
		Medium => print "medium"
		High => print "high"
		_ => print "default"

	randNum = rnd(5)
	randRange = rnd(1, 8)
	randFLoatRange = rnd(0f, 5.5f)
	randDoubleRange = rnd(0.0, 15.5)
	randBool = rnd(bool)
	randInt = rnd(int)
	randFloat = rnd(float)
	randString = rnd(string, 12)
	randChar = rnd(char)

	alive = true
	dead = false

	notHere = null
	print notHere or "value is null"

	#optional static typing
	bool b = true
	int xNum = 0, yNum = 0
	long xLong = 0L, yLong = 0L
	float xx = 0.0f, yy = 0.0f
	double xxx = 0.0, yyy = 0.0
	string str = ""
	char c = 'a'

	#all arrays, lists, maps, sets and classes are tables
	zeroedArray = int [8]
	zeroedArray2D = int [8][8]
	emptyStringArray = string [12]
	array = [0, "1", '2']
	array2D = [1, 2, 3], [4, 5, 6], [7, 8, 9]
	list = {0, "1"}
	map = (a: "this is a", b: "this is b")
  	otherMap = (0: "cat", 1: "dog", 2: "mouse")
	set = |0, 1, 2, 3|
	table = <tString = "hello", tNum = 4, tFunc: return tString + ", " + tNum>

	firstClassFunc => return sqrt(pi ** 2)

	print table.tFunc

	print array.len

	print '.' * 3

  	#list is used like a list and a stack
	list.push('2')
  	list.pop()

	lib.libFunc, print lib.libValue

  	final xRange = 4
  	xText = "This is x: "

	for x in range xRange:
		print xText + x

	for i = 0, i < 5, i++:
		print i

	for x = 0, x < array2D.len, x++:
		for y = 0, y < array2D[0].len, y++:
			print x + ", " + y + " = " + array2D[x][y]

  	for x in array:
    		print x

	for key, value in array:
		print key + ", " + value

  	for key, value in map:
    		print key + ", " + value

  	for key, value in table:
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

	funcToPass => print '.' * 3
	tripleFunc(funcToPass)
	tripleFunc( => print '!' * 3 )
	tripleFunc(func)
	
	#pattern matching
    	m = 1
	match m:
		1 => print "one"
		2 => print "two"
		3 => print "three"
		_ => print "anything"

	//regex funcitons
	text = "0 look at the cats. All those cats."
	#regex strings have to start with r infront of the ""
	reg = r"\d"
	#regex function string parameters don't need r
	print search("\d", text)
	#flag i = ignore case, flag s = . matches newline
	otherReg = ris"ThE Case DoEsN't MaTtEr\nNeW lInEs GeT mAtChEd WiTh .\n"
	print search(is"all", text)
	print search(reg, text)
	print all("cats", text)
	words = split(" ", text)
	lines = split(text)
	threeLines = split("\n", text, 2)
	subbed = sub("\s", 0, text)
	twoSubbed = sub("\s", 0, text, 2)
	ms = regex("\w", "this is the way")
	print ms.matched
	firstGroup = ms.group(0)
	secondGroup = ms.group(1)
	namedGroup = ms.group("name")

	regex("(\w)(\w)(\w)(?<name>).*", "this will be matched then groups will be asigned to $1, $2, $3 then a group named name")
	#$ infront of an integer gives the last matched expression's group at that index
	print $1 + $2 + $3

	#$"name" for named groups
	print $"name"

	if "isWord" =~ "[\w]":
		print "match"
	else:
		print "no match"

	//oop in stealth
	Cat cat = new Cat(5, 5)
	Tiger tiger = new Tiger(10, 10)

	cat.meow, cat.meow, cat.meow
	tiger.meow, tiger.meow, tiger.meow

  	cat.catStuff, tiger.catStuff

	if tiger instance of Tiger:
		print "it's a tiger"

	if cat instance of Cat, Bird, Mouse:
		print "it's either a cat, bird or mouse"

	guess = input("Enter something: ")
	print guess or "you did not enter anything"

func:
	print "hello"

otherFunc:
	print "hi"

funcParam(x, y):
	return x * y

typedParam(int x, int y):
	return x + y

nullFUnc:
	string s = "this can't be changed."
	string ss = "this also."
	string sss = "etc..."

	return s + ss + sss

tripleFunc(Function func):
	func, func, func


#a type infront of a function means the function has to return that type
string catFunc:
	int x = 5, y = 4
	bool b = true
	string s = "string text", ss = "other text"
	
	// .. concatenates anything to anything
	return b .. x .. y + ", " + s + ", " + ss

string typeIdentifier(anything):
	if anything instance of int:
		return "int"
	elif anything instance of float:
		return "float"
	elif anything instance of Funtion:
		return "Function"
	elif anything instance of bool:
		return "bool"
	elif anything instance of Cat:
		return "Cat"
	elif anything instance of Table:
		return "Table"
	return "unknown"

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
