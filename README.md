# PyBank
from pathlib import Path
import csv
​
# Set path for csv
filePath = Path("budget_data.csv")
​
# New list
profitLosses = []
months = []
netChange = []
​
​
# open csv
with open(filePath, 'r') as csvfile:
    csvreader = csv.reader(csvfile, delimiter =",")
    csvheader = next(csvreader)
    
 # Sort through the rows in the file and append profit/losses and months
    for row in csvreader:
        months.append(row[0])
        profitLosses.append(int(row[1]))
        
 # calculating net change of the months
    for x in range(len(profitLosses)-1):
        netChange.append(profitLosses[x+1]-profitLosses[x])
        
maxIncreaseAmount = max(netChange)
minIncreaseAmount = min(netChange)
        
# Getting max and min values for profit/loss 
maxIncrease = netChange.index(max(netChange)) + 1
minIncrease = netChange.index(min(netChange)) + 1
​
​
​
#Printing Analysis
​
print("Financial Analysis")
print("------------------------")
print(f"Total Months:{len(months)}")
print(f"Average Change: ${round(sum(netChange)/len(netChange),2)}")
print(f"Greatest Increase in Profits: {months[maxIncrease]} (${(str(maxIncreaseAmount))})")
print(f"Greatest Increase in Profits: {months[minIncrease]} (${(str(minIncreaseAmount))})")
​
        
​
Financial Analysis
------------------------
Total Months:86
Average Change: $-2315.12
Greatest Increase in Profits: Feb-2012 ($1926159)
Greatest Increase in Profits: Sep-2013 ($-2196167)
