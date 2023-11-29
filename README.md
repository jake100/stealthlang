# stealthlang
Scripting language called stealth. Uses indentation-based syntax with optional function parenthesis and optional static typing. It's Python mixed with Lua with some Java so far mostly, Gain all access of the languages features by default no imports to access language features.

```
#python style comments

#java style multiline comment
/*
this is all in a multiline comment.
this also
etc...
*/

#import statement, file extension is .stlf, file extension is omitted in import statement but all files must end in .st1f
import otherFile as o
import library as lib
import thing from library as t

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

	#pattern matching
    	m = 1
	match m:
		1 => print "one"
		2 => print "two"
		3 => print "three"
		_ => print "anything else"

	type = Type.Off
	highType = Type.High
	mediumType = Type.Medium
	lowType = Type.Low

	match type:
		Off => print "off"
		Low => print "low"
		Medium => print "medium"
		High => print "high"

	match highType:
		Off => print "off"
		_ => print "on"

	match type, lowType, mediumType, highType:
		before:
			print "-" * 12
		Off => print "cold"
		High => print "hot"
		Low, Medium => print "warm"
		after:
			print "." * 12

	randNum = rnd(5)
	randFloat = rnd(5.0f)
	randDouble = rnd(5.0)
	randRange = rnd(1, 8)
	randFLoatRange = rnd(1f, 5.5f)
	randDoubleRange = rnd(1.0, 15.5)
	randBool = rnd(bool)
	randInt = rnd(int)
	randFloat = rnd(float)
	randString = rnd(string, 12)
	randChar = rnd(char)
	randByte = rnd(byte)

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
	byte by = 2

	#all arrays, lists, maps, sets and classes are tables
	zeroedArray = int [8]
	zeroedArray2D = int [8][8]
	emptyStringArray = string [12]
	columns = 10, rows = 10, depth = 10
	arrayInit = for all [columns] = 10
	arrayInit2D = for all [columns][rows] = 1
	#in the for all definition first dimension gets bound to _0 second dimension gets bound to _1 third to _2 and so on for how many dimensions
	arrayInit3D = for all [columns][rows][depth] = 3 * _0 * _1 * _2
	array = [0, "1", '2']
	array2D = [1, 2, 3], [4, 5, 6], [7, 8, 9]
	list = {0, "1"}
	map = (a: "this is a", b: "this is b")
  	otherMap = (0: "cat", 1: "dog", 2: "mouse")
	set = |0, 1, 2, 3|
	table = <tString = "hello", tNum = 4, tFunc: return tString + ", " + tNum>
	nums = <x = 0, y = 1, z = 2, i = 4, j = 8, k = 16>
	print nums.x + ", " nums.y, + ", " + nums.z + ", " + nums.i + ", " + nums.j + ", " + nums.k

	#same thing but shorter with ! after the table to prevent repetition
	nums! print x + ", " y + ", " + z + ", " + i + ", " + j ", " + k

	#multiline with the ! syntax
	nums!
		print x * y * z * i * j * k

	firstClassFunc => return sqrt(pi ** 2) >> 2

	print table.tFunc

	pubVars!
		while alive:
			x = 10, y = 10, z = 10, alive = rnd(bool), pubVar

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

	#prints the value at each index with _
	for array => print _

	#prints the indexes of each dimension for every value in the array
	for arrayInit3D => print _0 + ", " + _1 + ", " + _2

	#doubles every value in the array
	for array = _ ** 2

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

	#f is asigned to a lambda that calls func then otherFunc then on the next line it is called 7 times, func will be called then otherFunc, 7 sets of times 
	f => func, otherFunc
	f, f, f, f, f, f, f

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
	#$m returns true if last regex expression matched
	print $m? "it matched" || "it did not match"
	#$ infront of an integer gives the last matched expression's group at that index
	print $1 + $2 + $3
	print $m? $1 + $2 + $3 || "no match"

	#$"name" for named groups
	print $"name"

	if "isWord" =~ "[\w]":
		print "match"
	else:
		print "no match"

	//oop in stealth, optional constructor parenthesis
	Game game = new Game

	Cat cat = new Cat(5, 5)
	Tiger tiger = new Tiger(10, 10)

	cat.meow, cat.meow, cat.meow
	tiger.meow, tiger.meow, tiger.meow

  	cat.catStuff, tiger.catStuff

	#more use of the ! syntax but with a class
	cat! meow, meow, meow, meow, catStuff

	if tiger instance of Tiger:
		print "it's a tiger"

	if cat instance of Cat or Bird or Mouse:
		print "it's either a cat, bird or mouse"

	guess = input("Enter something: ")
	print guess or "you did not enter anything"

func:
	print "hello"

pubVars:
	public
	bool alive = false
	int x, y, z = 0, 0, 0

	return alive? print x + ", " + y + ", " + z || print "sorry you are dead"

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

isOdd(int num):
	return num % 2 != 0

#functions can be on be a single line
oneLiner: print 0, print "...", print "..." * 3, print "...", print 99

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

class Game:
	alive = true
	undead = false
	Game:
		run: print "creating a new thread and starting the game loop", loop
	loop:
		while alive or undead:
			update, render, sleep(1 / 60)
			if rnd(5) == 0: alive = false
			if rnd(50) == 0: undead = !undead
			alive? print "you are alive." || undead? print "you are undead." || print "you are dead."
			if !alive and !undead: print "dead for the last time."		
	protected

	update:
		print "updating..."
	render:
		print "rendering..."

class XGame is a Game:
	xs = 1
	xStr = ""
	XGame: super, print "died"

	protected

	update:
		xStr += "x" * xs++ + "\n"
	render:
		print xStr

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
	Tiger(x, y):
		super(x, y)
		print "after Cat's init"
	public

	growl:
		print "growl"
	
	protected
	
	meow:
		print "grrr"

```
