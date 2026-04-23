**Collections \& Date \& Time**



1\. Counter – Unique Elements



from collections import Counter



nums = \[5,3,5,2,3,1,4,1,2]

c = Counter(nums)



result = \[num for num, count in c.items() if count == 1]

print(result)



2\. Counter – Equal Frequency



from collections import Counter



s = "aabbccddeeffgg"

c = Counter(s)



print(len(set(c.values())) == 1)



3\. Counter – Find Missing Numbers



from collections import Counter



list1 = \[1,2,3,4,5]

list2 = \[1,2,2,3,4,4,5]



c1 = Counter(list1)

c2 = Counter(list2)



extra = c2 - c1



4\. defaultdict – Word Length Grouping



from collections import defaultdict



words = \["python","java","go","c","ruby","php"]

d = defaultdict(list)



for w in words:

&nbsp;   d\[len(w)].append(w)



print(dict(d))



5\. defaultdict – Student Marks



from collections import defaultdict



data = \[("Alice",85),("Bob",78),("Alice",92),("Bob",88)]

d = defaultdict(list)



for name, marks in data:

&nbsp;   d\[name].append(marks)



print(dict(d))



6\. OrderedDict – First Non-Repeating Character



from collections import OrderedDict



s = "swiss"

d = OrderedDict()



for ch in s:

&nbsp;   d\[ch] = d.get(ch, 0) + 1



for ch, count in d.items():

&nbsp;   if count == 1:

&nbsp;       print(ch)

&nbsp;       break



7\. deque – Sliding Window Sum



from collections import deque



nums = \[1,2,3,4,5,6]

k = 3

dq = deque(nums\[:k])



print(sum(dq))

for i in range(k, len(nums)):

&nbsp;   dq.popleft()

&nbsp;   dq.append(nums\[i])

&nbsp;   print(sum(dq))



8\. deque – Check Palindrome



from collections import deque



s = "level"

dq = deque(s)



is\_pal = True

while len(dq) > 1:

&nbsp;   if dq.popleft() != dq.pop():

&nbsp;       is\_pal = False

&nbsp;       break



print("Palindrome" if is\_pal else "Not Palindrome")



9\. namedtuple – Highest Salary



from collections import namedtuple



Employee = namedtuple('Employee', \['name','salary'])



emps = \[

&nbsp;   Employee("Alice",50000),

&nbsp;   Employee("Bob",70000),

&nbsp;   Employee("Charlie",60000)

]



print(max(emps, key=lambda x: x.salary))



10\. ChainMap – Combine Dictionaries



from collections import ChainMap



d1 = {"a":10,"b":20}

d2 = {"b":30,"c":40}



cm = ChainMap(d1, d2)

print(cm\['b'])



\[24bcs127@mepcolinux ex6]$cat pr1.py

from collections import Counter



nums = \[5,3,5,2,3,1,4,1,2]

c = Counter(nums)



result = \[num for num, count in c.items() if count == 1]

print(result)



**Problems Using datetime**



11\. Leap Year Check



import datetime



year = 2028

print(datetime.date(year, 1, 1).year % 4 == 0)



12\. Current Date Format



import datetime



today = datetime.datetime.now()

print(today.strftime("%d-%B-%Y %A"))



13\. Week Number



import datetime



d = datetime.datetime(2026,3,10)

print(d.strftime("%U"))



14\. Difference in Seconds



from datetime import datetime



t1 = datetime(2026,3,10,10,0,0)

t2 = datetime(2026,3,10,12,30,0)



print((t2 - t1).total\_seconds())



15\. Next 5 Days



from datetime import datetime, timedelta



today = datetime.today()



for i in range(1,6):

&nbsp;   print((today + timedelta(days=i)).date())



16\. Previous Month Date



from datetime import datetime



d = datetime(2026,3,10)

prev\_month = d.replace(month=d.month-1)



print(prev\_month.date())



17\. Count Sundays



import datetime



count = 0

for day in range(1,32):

&nbsp;   try:

&nbsp;       d = datetime.date(2025,1,day)

&nbsp;       if d.weekday() == 6:

&nbsp;           count += 1

&nbsp;   except:

&nbsp;       pass



print(count)



18\. Detect Weekend



import datetime



d = datetime.date(2026,3,14)

print("Weekend" if d.weekday() >= 5 else "Weekday")



19\. Daily Login Counter



from collections import Counter

from datetime import datetime



logins = \[

"2026-03-10 10:00",

"2026-03-10 12:00",

"2026-03-11 09:30",

"2026-03-11 11:45",

"2026-03-11 14:00"

]



dates = \[datetime.strptime(x,"%Y-%m-%d %H:%M").date() for x in logins]

print(Counter(dates))



20\. Most Frequent Login Hour



from collections import Counter

from datetime import datetime



logins = \[

&nbsp;   "2026-03-10 10:00",

&nbsp;   "2026-03-10 12:00",

&nbsp;   "2026-03-11 09:30",

&nbsp;   "2026-03-11 11:45",

&nbsp;   "2026-03-11 14:00"

]



hours = \[datetime.strptime(x,"%Y-%m-%d %H:%M").hour for x in logins]

c = Counter(hours)



print(c.most\_common(1))



21\. Monthly Event Counter



from collections import Counter

from datetime import datetime



events = \[

"2025-01-10",

"2025-01-20",

"2025-02-05",

"2025-02-15",

"2025-03-01"

]



months = \[datetime.strptime(e,"%Y-%m-%d").month for e in events]

print(Counter(months))



22\. Group Dates by Weekday



from collections import defaultdict

from datetime import datetime



dates = \["2025-01-10","2025-01-20","2025-02-05"]



d = defaultdict(list)



for dt in dates:

&nbsp;   date\_obj = datetime.strptime(dt,"%Y-%m-%d")

&nbsp;   d\[date\_obj.strftime("%A")].append(dt)



print(dict(d))



23\. Find Oldest Date



Given a list of date strings, find the oldest date using datetime.



from datetime import datetime



dates = \["2025-01-10","2023-05-01","2024-07-15"]



oldest = min(datetime.strptime(d,"%Y-%m-%d") for d in dates)

print(oldest.date())



24\. Detect Duplicate Dates



Given a list of dates, find which dates occur more than once using Counter



from collections import Counter



dates = \["2025-01-10","2025-01-10","2025-02-05"]



c = Counter(dates)

print(\[d for d, count in c.items() if count > 1])



25\. Recent Activity Tracker



Given a list of user activity timestamps, find users active in the last 24 hours

from datetime import datetime, timedelta



activities = \[

("user1","2026-03-25 10:00"),

("user2","2026-03-24 09:00"),

("user3","2026-03-25 23:00")

]



now = datetime(2026,3,26,10,0)



recent = \[]

for user, time in activities:

&nbsp;   t = datetime.strptime(time,"%Y-%m-%d %H:%M")

&nbsp;   if now - t <= timedelta(days=1):

&nbsp;       recent.append(user)



print(recent)

