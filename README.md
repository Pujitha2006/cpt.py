def csortString(s):
    count=[0]*26
    for char in s:
        count[ord(char)-ord('a')]+=1
    sorted_str=''
    for i in range(26):
        sorted_str+=chr(i+ord('a'))*count[i]
    return sorted_str
name=input("Enter a single word")
sorted_name=csortString(name)
print("Original string:",name)
print("Sorted string:",sorted_name)
