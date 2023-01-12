import csv
from pathlib import Path

file_to_load = Path("Recources/budget_data.csv")
file_to_input = Path("analysis/budget_analysis.txt")

total_months = 0
month_of_change = []
net_change_list = []
greatest_increase = ["", 0]
greatest_decrease = ["", 999999999999999]
total_net = 0
print(total_net)

with open(file_to_load) as financial_data:
    reader = csv.reader(financial_data)
    
    
    #Read the header row
    header = next(reader)
    
    #Extract first row to avoid appending to net_change_list
    first_row = next(reader)
    total_months = total_months + 1
    total_net = total_net +int(first_row[1])
    prev_net = int(first_row[1])
    
    for row in reader:
        
        #track the total
        total_months = total_months + 1
        total_net = total_net + it(row[1])
        
        #track the net change
        net_change = int(row[1]) - prev_net
        prev_net = int(row[1])
        net_change_list = net_change_list + [net_change]
        month_of_change = month_change + [row[0]]
        
        #Calculate the greatest increase
        if net_change > greates_increase[1]:
            greatest_increase[0] = row[0]
            greatest_increase[1] = net_change
            
        #Calculate the greatest increase
        if net_change > greatest_increase[1]:
            greatest_increase[0] = row[0]
            greatest_increase[1] = net_change
            
        #Calculate the greatest decrease
        if net_change > greatest_decrease[1]:
            greatest_decrease[0] = row[0]
            greatest_decrease[1] = net_change
                
            
        
    
    #calculate the average net change
net_monthly_avg = round(sum(net_change_list) / len(net_change_list,2)

print(f"Financial Analysis\n")
print(f"----------------------------\n")
print(f"Total Months: {total_months}\n")
print(f"Total: ${total_net}\n")
print(f"Average change: ${net_monthly_avg}\n")
print(f"Greatest Increase in Profits: {greatest_increase[0]} (${greatest_increase[1]})\n")
print(f"Greatest Decrease in Profits: {greatest_decrease[0]} (${greatest_decrease[1]})\n")
