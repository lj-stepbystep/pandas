# pandas
self-learning processing
#按股票的代码对含有多种股票的大文件进行切片，并写成多个文件
import csv

file=open('C:\\Users\\Lijie\\Desktop\\marketData.190903\\marketData.190903')
dict1={}


for line in file.readlines():
    curline=line.strip().split(',')
    print(curline[2])
    
    
    if curline[2] not in dict1.keys():
        key=curline[2]
        valuelist=[]
        valuelist.append(line)
        dict1[key] = valuelist
       
    else:
        key=curline[2]
        valuelist = dict1[key]
        valuelist.append(line)
        dict1[key] = valuelist
        
for key,valuelist in dict1.items():
    with open('C:\\Users\\Lijie\\Desktop\\analyst\\'+key+'.csv','w',newline='')as csvfile:
        #writer=csv.writer(csvfile)
        #for value in valuelist:
        #    writer.writerow(value)
        for value in valuelist:
            csvfile.write(value)






















