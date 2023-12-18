# Sorting IP addresses

Write a program that reads IP addresses and displays them in ascending order using decimal notation. To convert an address, for example 192.168.1.2, into a decimal number, use the formula:

192 * 256^3 + 168 * 256^2 + 1 * 256^1 + 2 * 256^0 = 3232235778

Input data:

The first line contains the number n, then n lines with IP addresses.


#Input example
12
123.199.44.25
123.199.201.245
145.198.168.93
170.67.181.62
170.67.222.111
170.67.11.90
45.8.106.59
203.13.32.156
179.67.171.194
179.67.181.62
179.67.212.111
177.67.10.90


    
Output:

List of IP addresses sorted by decimal notation.

        
#Example output
45.8.106.59
123.199.44.25
123.199.201.245
145.198.168.93
170.67.11.90
170.67.181.62
170.67.222.111
177.67.10.90
179.67.171.194
179.67.181.62
179.67.212.111
203.13.32.156




    
Solution
Method 1 – using ipaddress:

        
import ipaddress
n = int(input())
spisok = []
for i in range(n):
     temp = input()
     spisok.append(temp)
sortedkey = sorted(spisok, key = ipaddress.IPv4Address)
print(*sortedkey, sep='\n')
    

    
Method 2:

        
print(*sorted([input() for _ in range(int(input()))], key=lambda x: [*map(int, x.split('.'))]), sep='\ n')
    

    
Method 3:

        
def decFormat(ip):
     return sum(map(lambda x, y: int(x) * 256 ** y, ip.split('.'), (3, 2, 1, 0)))
ips = [input() for _ in range(int(input()))]
print(*sorted(ips, key = decFormat), sep = '\n')
