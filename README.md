# Prime-Number-Generator
# My 1st Program in Python3 (Generates Prime Numbers)

# Still working on:
# -Loping the Input to check for several prime factors
# -writing the prime number list to a file
# -reading the file back into the program
# -testing the limits of data manipulation
# -optimizing execution time

# It's been 20+ years since I programmed in Fortran 77, feels like starting over

# If you are just browing by - check it out and let me know how I did!

# upper limit 10,000,000

# Create List of Numbers to Check
seedlist = []
x = 3
for i in range(1000):
	seedlist.append(x)
	x += 2
#print(seedlist)

# Define Variables
listlength = len(seedlist)
g = int(listlength / 2)
numeratorstartingpoint = 3
numeratoriterator = 0
numeratorposition = 0
denominatorposition = 0
remainder = 0
removallist = []
loopcounter = 0
totaliterations = g - numeratorstartingpoint
evenlistpointer = 0
evenlistincrementor = 0

# Start Checking for NON-Primes
while (loopcounter <= totaliterations):

# Calculate Index Starting Point 
	numeratorposition = numeratorstartingpoint + numeratoriterator

# Validate Index Starting Point
	if numeratorposition >= listlength:
#		print("***EOL***")
		break
	
# Iterate Numerator Thru List and Check for Integer Remainders
	for i in range(len(seedlist)):
		remainder = seedlist[numeratorposition] % seedlist[denominatorposition]
#		print("Function", seedlist[numeratorposition], "%", seedlist[denominatorposition], "'False if EVEN'", bool(remainder))
		numeratorposition = numeratorposition + 1
	
# Add Indexed Value of Integer Remainer(s) to a Seperate List
		if bool(remainder) == False:
			evenlistpointer = i + numeratorstartingpoint + evenlistincrementor
			removallist.append(seedlist[evenlistpointer])

# Iterate Denominator
		if numeratorposition >= listlength:
			numeratorposition = 0
			evenlistincrementor += 3
			loopcounter += 1
			numeratoriterator += 3
			denominatorposition += 1
			break

# Print NON-Primes List, Remove Duplicates
removallist = list(dict.fromkeys(removallist))

# Remove all Values of NON-Primes List from Seed List
seedset = set(seedlist)
removalset = set(removallist)
primeset = seedset - removalset
primelisttemp = list(primeset)
primelist = sorted(primelisttemp)

# Start Checking for Prime Factors

# Add the Oddball "2" into Prime Number List
primelist.insert(0, 2)
print ("primelist", primelist)

# Define Variables
itcount = len(primelist)
checker = 0
seed = 0

# Request a Number to be Checked
print ("# of primes in list             :::", len(primelist))
print ("largest prime number in list is :::", primelist[-1])
print ("largest allowable seed # is     :::", primelist[-1] * 2)
seed = int(input("Input Seed #                    ::: "))

# Check for Prime Factors
for x in range (itcount):
	if (seed % primelist[x] == 0):
		print ("Prime Factor                    :::",primelist[x])
