**LIST,TUPLE,SET,DICTIONARY OPERATIONS** 



1\) Two users on an online learning platform have sets of course interests. Develop a Python program using sets to:

Find the common interests between the users.

Suggest new courses to one user based on the other user’s interests.



a = {"AI", "Data Science", "CSE"}

b = {"ECE", "CSE", "AI"}



common = a \& b

suggestion = b - a



print("Common Interests:" ,common)

print("Suggested for User A:", suggestion)



2)organization records three sets of IP addresses:

&nbsp;L – logged in successfully

&nbsp;F – failed login attempt

&nbsp;B – blacklisted IP addresses



&nbsp;Using set operations, identify:

&nbsp;IPs that appear in both successful and failed logins but are not blacklisted.

&nbsp;IPs that attempted access but never succeeded.

&nbsp;IPs that are only blacklisted and never attempted login.



A = {"264.168.1.1", "10.0.0.5"}

B = {"264.168.1.1", "172.16.0.2"}

C = {"172.16.0.2", "192.168.1.50"}



print("Both login types, not blacklisted:", (A \& B) - C)

print("Attempted but never succeeded:", B - A)

print("Only blacklisted, never attempted:", C - (A | B))



3)An online store maintains a set of available products and another set of sold products. Develop a Python program using sets to determine:

Products still in stock.

Products that have been sold out.



available = {"Laptop", "Speaker", "Keyboard", "Camera"}

sold = {"Mouse", "Monitor", "Camera"}



print("Still in stock:", available - sold)

print("Items sold :", sold \& available)



4\) An array contains skills required for a job role, another array contains skills of an applicant, and a string contains skills that are outdated. Write a Python program using set operations to identify missing required skills excluding outdated ones.



required = {"Python", "SQL", "Cloud", "DBMS"}

applicant = {"Python", "Java"}

outdated = "Computing, DBMS"



outdated\_set = set(outdated.replace(",", "").split())



missing\_skills = (required - applicant) - outdated\_set

print("Missing required skills (excluding outdated):", missing\_skills)



5)Student Attendance Analysis



A university maintains attendance records for two different days using sets of student roll numbers. Write a Python program using set operations to:

Identify students present on both days.

Identify students present on either day.

Identify students absent on the second day.



d1 = {10, 12, 14, 16, 18}

d2 = {14, 16, 18, 20, 22}



both = d1 \& d2

either = d1 | d2

missing\_d2 = d1 - d2



print("Students present on both days:",both)

print("Students present on either days:",either)

print("Student absent on second days:",missing\_d2)

&nbsp;

5)university maintains collaboration records of students participating in multiple technical clubs. Each record is stored as a list of strings, where each string follows this format:

&nbsp;StudentName:Club1,Club2,Club3

&nbsp;records = \["Arun:AI,ML,Robotics",  "Bala:ML,IoT", "Chitra:AI,CyberSecurity", "Divya:Robotics,IoT,AI", "Ezhil:ML,CyberSecurity","Farah:AI,ML", "Ganesh:IoT,Robotics,AI",   "Hari:ML"]

&nbsp;Write a Python program that performs the following operations strictly using combinations of lists, strings, and sets.

&nbsp;Extract all unique student names into a set.

&nbsp;Extract all unique clubs into a set.

&nbsp;Convert each student’s club list into a set and store the mapping in a suitable data structure.

&nbsp;Remove any duplicate club names if they appear due to formatting errors.

&nbsp;Find students who are members of both AI and ML clubs.

&nbsp;Find students who are members of AI but not Robotics.Identify clubs that no student belongs to alone (i.e., clubs that always appear with at least one other club).

&nbsp;Determine the intersection of clubs for students whose names start with a vowel.

&nbsp;Find the union of clubs for students whose names end with a consonant.

&nbsp;Create a set of all characters used in all student names (ignore case).

&nbsp;Find characters that appear in every student name.

&nbsp;Identify students whose name character set is a subset of the character set of "Arun".

&nbsp;Convert the list of club sets into a list and: Find duplicate club combinations (same set, different students). Count how many students share identical club memberships.

&nbsp;Sort students based on: Number of clubs (descending), Then alphabetically (ascending)

&nbsp;Create a final set of students who satisfy all of the following: Name length is a prime number, Member of at least one club starting with a vowel, Shares no common club with "Hari"



from functools import reduce



records = \[

&nbsp;   "Kavin:AI,ML,Robotics",

&nbsp;   "Karthika:ML,IoT",

&nbsp;   "Vijaya Bhaskar:AI,CyberSecurity",

&nbsp;   "Harish:Robotics,IoT,AI",

&nbsp;   "Raj:ML,CyberSecurity",

&nbsp;   "Reena:AI,ML",

&nbsp;   "Priya:IoT,Robotics,AI",

&nbsp;   "Vel:ML"

]



\# 1, 2, 3: Parsing data using basic loops

data = {}

all\_clubs = set()

for r in records:

&nbsp;   name, club\_str = r.split(':')

&nbsp;   club\_set = set(club\_str.split(','))

&nbsp;   data\[name] = club\_set

&nbsp;   for c in club\_set:

&nbsp;       all\_clubs.add(c)



names = set(data.keys())

print(f"1. Names: {names}\\n2. Clubs: {all\_clubs}\\n3. Mapping: {data}")



\# 4 \& 5: Simple filters

print(f"4. AI \& ML: {\[n for n, c in data.items() if {'AI', 'ML'} <= c]}")

print(f"5. AI not Robotics: {\[n for n, c in data.items() if 'AI' in c and 'Robotics' not in c]}")



\# 6: Logic for clubs never taken alone

solo = {list(c)\[0] for c in data.values() if len(c) == 1}

print(f"6. Never alone: {all\_clubs - solo}")



\# 7: Common clubs for vowel-start names (using reduce instead of \*)

v\_start = \[c for n, c in data.items() if n\[0].lower() in 'aeiou']

common\_v = reduce(lambda x, y: x \& y, v\_start) if v\_start else "None"

print(f"7. Vowel Start Common: {common\_v}")



\# 8: Union for consonant-end names

c\_end = \[c for n, c in data.items() if n\[-1].lower() not in 'aeiou']

union\_c = reduce(lambda x, y: x | y, c\_end) if c\_end else set()

print(f"8. Consonant End Union: {union\_c}")



\# 9 \& 10: Characters logic

all\_chars = set("".join(names).lower())

common\_chars = reduce(lambda x, y: x \& y, \[set(n.lower()) for n in names])

print(f"9. All Chars: {all\_chars}")

print(f"10. Common Chars: {common\_chars}")

print(f"11. Subset 'Arun': {\[n for n in names if set(n.lower()) <= set('arun')]}")

sort\_res = sorted(data.items(), key=lambda x: (-len(x\[1]), x\[0]))

print(f"13. Sorted: {sort\_res}")





def is\_prime(n): return n > 1 and all(n % i != 0 for i in range(2, n))

final = {n for n, c in data.items() if is\_prime(len(n)) and any(cl\[0].lower() in 'aeiou' for cl in c) and c.isdisjoint(data.get('Harish', set()))}

print(f"14. Final: {final}")



