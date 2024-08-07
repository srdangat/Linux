# AWK

`awk` is mostly used for pattern scanning and processing.Scans a file line by line.

**Syntax**

```sh
awk options 'pattern {action}' file_name
```
**options**
- -F Field Separator
- -v var=value
- -f file

**Terms used in awk**

```sh
NR: No.of records/row
NF: No.of fields
$0: Print everything
$1,$2: Field no
```

**To demonstrate more about AWK usage,we are going to use the text file called emp.txt**

```sh
cat emp.txt
```

```sh
id  fname lname desig dept salary
101 Raju Rastogi Manager Loan 37000
102 Sham Mohan cashier Cash 32000
103 Baburao Apte Associate Loan 25000
104 Paul Philip Accountant Account 45000
105 Alex Watt Associate Deposit 35000
106 Rick Watt Manager Account 65000
107 Leena Jhonson Lead Cash 25000
108 John Paul Manager IT 75000
109 Alex Watt Probation Loan 40000
```

**Print each line of the file**

```sh
$ awk '{print}' emp.txt
```
**Output**
```sh
id  fname lname desig dept salary
101 Raju Rastogi Manager Loan 37000
102 Sham Mohan cashier Cash 32000
103 Baburao Apte Associate Loan 25000
104 Paul Philip Accountant Account 45000
105 Alex Watt Associate Deposit 35000
106 Rick Watt Manager Account 65000
107 Leena Jhonson Lead Cash 25000
108 John Paul Manager IT 75000
109 Alex Watt Probation Loan 40000
```

**Print the first field of each line**

```sh
$ awk '{print $1}' emp.txt
```

**Output**
```sh
id
101
102
103
104
105
106
107
108
109
```

**Print the first and third fields of each line**

```sh
$ awk '{print $1,$3}' emp.txt
```

**Output**
```sh
id lname
101 Rastogi
102 Mohan
103 Apte
104 Philip
105 Watt
106 Watt
107 Jhonson
108 Paul
109 Watt
```

**Print last column**

```sh
$ awk '{print $NF}' emp.txt
```

**Output**
```sh
salary
37000
32000
25000
45000
35000
65000
25000
75000
40000
```

**Search word**

```sh
$ awk '/Alex/ { print }' emp.txt
```

**Output**
```sh
105 Alex Watt Associate Deposit 35000
109 Alex Watt Probation Loan 40000
```

**Print only a given line no.**

```sh
$ awk 'NR == 5 { print }' emp.txt
```

**Output**
```sh
105 Alex Watt Associate Deposit 35000
```

**Print row or line no. at start of each line**

```sh
$ awk '{ print NR, $0 }' emp.txt
```

**Output**
```sh
1 id  fname lname desig dept salary
2 101 Raju Rastogi Manager Loan 37000
3 102 Sham Mohan cashier Cash 32000
4 103 Baburao Apte Associate Loan 25000
5 104 Paul Philip Accountant Account 45000
6 105 Alex Watt Associate Deposit 35000
7 106 Rick Watt Manager Account 65000
8 107 Leena Jhonson Lead Cash 25000
9 108 John Paul Manager IT 75000
10 109 Alex Watt Probation Loan 40000
```

**Print range of lines**

```sh
$ awk 'NR==3, NR==6 { print NR, $0 }' emp.txt
$ awk 'NR >= 3 && NR <= 6' emp.txt
```

**Output**
```sh
3 102 Sham Mohan cashier Cash 32000
4 103 Baburao Apte Associate Loan 25000
5 104 Paul Philip Accountant Account 45000
6 105 Alex Watt Associate Deposit 35000
```

**Search multiple words**

```sh
$ awk '/Raju|Sham|Paul/ { print $0 }' emp.txt
```

**Output**
```sh
101 Raju Rastogi Manager Loan 37000
102 Sham Mohan chashier Cash 32000
104 Paul Philip Accountant Account 45000
108 John Paul Manager IT 75000
```

**Ignore case while searching**

```sh
$ awk 'BEGIN { IGNORECASE = 1 } /sham/ { print $0 }' emp.txt
```

**Output**
```sh
102 Sham Mohan cashier Cash 32000
```

**Check if a given char is present in column**

```sh
$ awk '$2 ~ /a/' emp.txt
```

**Output**
```sh
id  fname lname desig dept salary
101 Raju Rastogi Manager Loan 37000
102 Sham Mohan cashier Cash 32000
103 Baburao Apte Associate Loan 25000
104 Paul Philip Accountant Account 45000
107 Leena Jhonson Lead Cash 25000
```