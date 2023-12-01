# stealthlang
Scripting language called stealth. Uses indentation-based syntax with optional function parenthesis and optional strong static typing with weak dynamic typing as the default. It's Python mixed with Lua with some Java so far mostly, whole language is available with no imports neaded.

Hello world example.
```
main: print "hello world"
```

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
#brings all windows's public members into scope
using window from graphicsLib

#global variables
final title = "stealth"
num = 42

enum Type:
	Off, Low, Medium, High

#main: is the entry point
main:
	#dynamic weak typing by default
	i = 5
  	j = 2, k = 4, l = 8

	#optional strong static typing
	bool b = true
	int xNum = 0, yNum = 0
	long xLong = 0L, yLong = 0L
	float xx = 0.0f, yy = 0.0f
	double xxx = 0.0, yyy = 0.0
	string str = ""
	char c = 'a'
	byte by = 2

	#alternate to setting a type, the type is infered from right hand side and the type can't be changed
	allwaysInteger := 64

	iBool = (bool) i
	iFloat = (float) i

	str = "55"
	str2 = "10.5f"
	str3 = "^*&^#"
	strNum = str.parse to int or 0
	strFloat = str2.parse to float or 0.0f
	strError = str3.parse to bool or throw error "this is an error."

	text = "This is some text."
	otherText = "So is this."
	letter2 = text[2]
	lastLetter = text[-1]
	slice = text[0:3]
	toEndSlice = text[1:]
	fromStartSlice = text[:3]
	fString = f"{text} {otherText} This is an f string."
	print text.upper
	print text.lower
	print text.title
	print text.capitalize
	print text.endsWith("error.")
	print text.startsWith("This is")
	print text.strip
	print text.lStrip
	print text.rStrip
	print text.find("some")
	print text.rFind("some")
	print is "text" in text
	print is "cats" not in text
	print text.isNum
	print text.isAlpha
	print text.isAlphaNum
	print text.isAscii
	print text.isDecimal
	print text.isDigit
	print text.isIdentifier
	print text.isLower
	print text.isUpper
	print text.isTitle
	print text.isPrintable
	print text.isSpace
	print text.lJust
	print text.rJust
	print text.swapCase
	print text.zFIll(5)
	print text.center(20)
	print text.center(20, "-")

	#math
	print max(5, 8)
	print min(2, 4)
	print max(array)
	print min(array)
	print max [2, 3, 2, 4, 2, 5, 2]
	print min [3, 1, 3, 4, 5, 8, 2]
	print sqrt(9)
	print abs(-8)
	print round(5.5)
	print round(5.5555,  2)
	print ceil(4.5)
	print floor(6)
	print pi
	print e
	print cos * tan * sin * acos * asin * atan
	print exp(1.0)
	print log(1.0)

	#save variable with anything as the key and value to the languages key value store on disk
	save("x", 39)
	save("y", 42)
	save("alive", true)
	save(true, "it's all true.")
	save(false, "it's all false.")
	save(0. "first save.")
	save(1. "second save.")

	#load a variable with a string as key
	savedX = load("x")
	savedY = load("y")
	savedAlive = load("alive")
	trueSave = load(true)
	falseSave = load(false)
	firstSave = load(0)
	secondSave = load(1)
	#load and save a file
	saveFile("notes.txt, "1: note to self...")
	saveFile("notes.txt", loadFile("notes.txt") + "\n" + "2: second note to self...")

	#log creates the log file if it does not exist otherwise the first strings is the file name but without a file extension, the next string is added to the log, every log of same name adds to the file on a new line
	log("logs", "first log.")
	log("logs", "this is the second log.")

	time = now
	print . * 10
	after = now
	print difference = after - time

	print "it is " + now.hour + ":" + now.minute + ":" + now.second + now.am? "AM" || "PM" + " "+ now.year + "-" + now.month + "-" + now.day + " on a " + now.dayOfWeek + now.weekend? ", it's the weekend!" || "."
\
	#pattern matching
    	m = 1
	match m:
		1 => print "one"
		2 => print "two"
		3 => print "three"
		_ => print "anything thing else"

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
	#a random array element gets asigned to randItem variable
	randItem = rnd(array)
	randLetter = rnd(str)
	#returns an array value from the right with weights from the left that determine the odds of being chosen
	w = weighted(4: "this", 5: "that", .5f: "and", 4: "what", 5: "ever")

	#pointers don't utilize pointer arithmetic
	year = 2023
	yr = &year
	#prints 2023
	print *yr

	alive = true
	dead = false
	undead = !alive

	#prints true
	print true or false
	print false or true

	#prints false
	print false or false
	print true and false

	notHere = null
	print notHere or "value is null"

	#do creates a new scope
	do:
		#variables of this scope not afiliated with the i, j, k, l in the upper scope
		i = 0
		j = 0, k = 0, l = 0

		#modify i of the higher scope
		this i = 0

	zeroedArray = int [8]
	zeroedArray2D = int [8][8]
	emptyStringArray = string [12]
	columns = 10, rows = 10, depth = 10
	arrayInit = for all [columns] = 10
	arrayInit2D = for all [columns][rows] = 1
	#in the for all definition first dimension gets bound to _0 second dimension gets bound to _1 third to _2 and so on for how many dimensions
	arrayInit3D = for all [columns][rows][depth] = 3 * _0 * _1 * _2

	#all arrays, lists, maps, sets and classes are tables
	array = [0, "1", '2']
	array2D = [1, 2, 3], [4, 5, 6], [7, 8, 9]
	list = {0, "1"}
	map = (a: "this is a", b: "this is b")
  	otherMap = (0: "cat", 1: "dog", 2: "mouse")
	set = |0, 1, 2, 3|
	linkedList = /1, 2, 3, 4, 5, 6/
	table = <tString = "hello", tNum = 4, tFunc: return tString + ", " + tNum>
	nums = <x = 0, y = 1, z = 2, i = 4, j = 8, k = 16>

	#point data type
	p = point(0, 6), p2 = point(2, 7)
	print p.x == 0
	print p.y == 6
	print p * p2
	print p + p2
	print p.move(2, 5)
	p *= p2
	print p.up + ", " + p.down + ", " + p.left + " " + p.right

	#point with floating point x and y values
	pf = point(0f, 7f)
	pd = point(0.0, 7.5)

	p3d = point(0, 1, 3)

	rectangle = box(0, 0, 5, 5)
	otherRec = box(1, 1, 5, 5)
	floatRec = box(0.1f, 1.4f, 5.5f, 5.5f)
	print rectangle + otherRec
	print rectangle * otherRec
	print rectangle + p
	print rectangle * p
	print rectangle.intercepts(otherRec)
	print rectangle.intercepts(p)
	print rectangle.intercepts(4, 7)
	print rectangle.x, print rectangle.y, print ractangle.width, print rectangle.height

	red = Color(255, 0, 0)
	green = Color(0, 255, 0)
	blue = Color(0, 0, 255)
	transRed = Color(255, 0, 0, 100)
	r = Color.red
	g = Color.green
	b = Color.blue
	w = Color.white
	b = Color.black
	t = Color.transparent

	a0 = array.map(val : val + 2)
	a1 = array.filter(val : val < 10)
	a2 = array.reduce(prev, curr : curr = prev + curr)

	print nums.x + ", " nums.y, + ", " + nums.z + ", " + nums.i + ", " + nums.j + ", " + nums.k

	#same thing but shorter with ! after the table to prevent repetition
	nums! print x + ", " y + ", " + z + ", " + i + ", " + j ", " + k

	#multiline with the ! syntax
	nums!
		print x * y * z * i * j * k

	#! syntax on a function
	funcGame!
		while alive:
			x = rnd(10), y = rnd(10), z = rnd(10), alive = rnd(bool), funcGame

	firstClassFunc => return sqrt(pi ** 2) >> 2

	print table.tFunc

	print array.len

  	#list is used like a list and a stack
	list.push('2')
	list.add(1)
	list.dup(0)
	list.multi(0, 5)
	list(0) *= 3
	list.sort
	print list.peek(1)
	list.swap(0, 2)
	list.reverse
  	item = list.pop
	itemAtIndex = list.pop(2)
	list.remove(0)
	print "max: " + list.max + ", min: " + list.min + ", sum: " + list.sum

	print list

	list.clear

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

	for letter in xText:
		print letter

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

	#times the value by it's self for every value in the array
	for array = _ ** 2

	for 0..20:
		print _0

	for 0..10:
		for 0..10:
			print _0 + ", " + _1

	for 0..10:
		for 0..10:
			for 0..10:
				print _0 + ", " + _1 + ", " + _2

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
	text.replace("\s", "")
	text.replaceAll("\s*", "")
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

	//oop in stealth, optional constructor parenthesis, if it deosn't take parameters it doesn't need the ()
	game = new Game
	xGame = new XGame

	cat = new Cat(5, 5)
	tiger = new Tiger(10, 10)

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

otherFunc:
	print "hi"

pointerFunction(*something):
	something = "this is something"

pointerFunctionInteger(*int number):
	number++

funcGame:
	bool alive = false
	int x, y, z = 0, 0, 0

	return alive? print x + ", " + y + ", " + z || print "sorry you are dead"

funcParam(x, y):
	return x * y

typedParam(int x, int y):
	return x + y

funcInFunc:
	innerFunc:
		print "..."
	innerFunc, innerFunc, innerFunc, innerFunc

privateMemberFunction:
	private
	#can't be accessed from out of function
	int x, y, z
	#can be called with privateMemberFunction.pos
	public pos: print x + ", " + y + ", " + z

constFUnc:
	final
	
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
	elif anything instance of Function:
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
