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



def count_sort(arr,exp):
    n=len(arr)
    output=[0]*n
    count=[0]*10
    for i in range(n):
        index=(arr[i]//exp)%10
        count[index]+=1
    for i in range(1,10):
        count[i]+=count[i-1]
    i=n-1
    while i>=0:
        index=(arr[i]//exp)%10
        output[count[index]-1]=arr[i]
        count[index]-=1
        i-=1
    for i in range(n):
        arr[i]=output[i]
def radix_sort(arr):
    max_num=max(arr)
    exp=1
    while max_num//exp>0:
        count_sort(arr,exp)
        exp *= 10
arr=[170,45,75,90,802,24,2,66]
print("Before sort: ",arr)
radix_sort(arr)
print("After sort: ",arr)



#pancake sort:
def flip(arr,k):
    return arr[:k+1][::-1]+arr[k+1:]
def pancake(arr):
    n=len(arr)
    for size in range(n,1,-1):
        max_index=arr.index(max(arr[:size]))
        if max_index!=size-1:
            if max_index!=0:
                arr=flip(arr,max_index)
                print(f" flip at {max_index+1}:{arr}")
            arr=flip(arr,size-1)
            print(f"flip at {size}:{arr}")
    return arr
nums=list(map(int,input("Enter numbers separated with space: ").split()))
sorted_nums=pancake(nums)
print("sorted ",sorted_nums)
#Output#
Enter numbers separated with space:  9 1 4 7 3
flip at 5:[3, 7, 4, 1, 9]
 flip at 2:[7, 3, 4, 1, 9]
flip at 4:[1, 4, 3, 7, 9]
 flip at 2:[4, 1, 3, 7, 9]
flip at 3:[3, 1, 4, 7, 9]
flip at 2:[1, 3, 4, 7, 9]
sorted  [1, 3, 4, 7, 9]




