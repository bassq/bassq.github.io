# HP Calicurator
4 level RPN Calicurator

## HP-42S 
c.f. emulator Free42

### Calc Keys
STO / RCL reg		# store, recall	 value
@Clear>CLx			# Clear memory segments
@Print>PON / POFF	# printer on

### input Program AREA
@GTO . . @PRGM @PGM.FCN >LBL AREA [ENTER]
@^2 @pi x [EXIT]

### Call Programs
XEQ "prog"	# eXEC program, and RETurn
@Custom	# Open Customisable Menu of Progs
@Assign <Prog> To <Menu>	# set Custom Menu

### Debug
@PRGM		# toggle; normal / program mode
R/S			# toggle; Run / Stop
@Pgm.Fcn▼RTN	# Reset PCounter @normal mode
@GTO .n			# goto line n
@GTO ..			# new prog space
@GTO .[Enter] LBL [Enter]	# goto LBL
▲ / @BST	# menu select / Back STep NOP
▼ / @SST	# <Press: Show line -> STep

### Jump; Do if True
@Pgm.Fcn▼X?0	X=0?, X<0?, ...
@Pgm.Fcn▼X?Y	X=Y?, X<Y?, ...
FS? / FC? <num>	# Flag setted / cleared
FS?C / FC?C		# clearing the flag
# flag 36-80 are System flag, others are user's

### Menu
@Pgm.Fcn▲KEYG / KEYX	# KEY nn GTO / EXQ
@Pgm.Fcn▲MENU
R/S		# STOP

### Misc
PSE: PauSE 1 second
BEEP	/ TONE nn

### Prog: Timer
	LBL "TMR"
	LBL 00
	PSE
	DSE ST X
	GTO 00
	BEEP
	END

### Prog: Gengou
	LBL "GENG"
	CLMENU
	"1867"	KEY 1 GTO 01
	"1911"	KEY 2 GTO 02
	"1925"	KEY 3 GTO 03
	"1988"	KEY 4 GTO 04
	"2018"	KEY 5 GTO 05
	MENU	STOP
	LBL 01	1867	GTO 11
	LBL 02	1911	GTO 11
	LBL 03	1925	GTO 11
	LBL 04	1988	GTO 11
	LBL 05	2018	GTO 11
	LBL 11	X<Y?	+/-		+
	END

### Prog: Octarv
	LBL "OCT"
	1.00801	STO "C"		# Begin.EndSt; "C"ounter
	LBL 01	TONE IND "C"	ISG "C"	GTO 01
	8		STO "C"		# simply set num of times & DSE
	LBL 02	TONE IND "C"	DSE "C"	GTO 02
	BEEP	END
	# ISG:	Increment Skip if Greater than
	# DSE:	Decriment Skip if less than or Equal
	
