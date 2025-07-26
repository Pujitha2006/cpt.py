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



with open ("file1.txt",'w')as f:
    f.write("Pujitha Shankar")
with open("file1.txt",'r+')as f:
    data=f.read()
    print("Previous:",data)
    new_data=data.replace("Shankar","Suresh")
    f.seek(0)
    f.write(new_data)
    f.truncate()
with open("file1.txt",'r')as f:
    print("Latest:",f.read())
## Output:
Previous: Pujitha Shankar
Latest: Pujitha Suresh



##at the end insertion on DLL:
class Node:
    def __init__(self,data):
        self.data=data
        self.prev=None
        self.next=None
class DoubleLinkedList:
    def __init__(self):
        self.head=None
    def iae(self,data):
        newnode=Node(data)
        if self.head is None:
            self.head=newnode
            return
        temp=self.head
        while temp.next:
            temp=temp.next
        temp.next=newnode
        newnode.prev=temp
    def display(self):
        temp=self.head
        print("Double Linked List:")
        while temp:
            print(temp.data,end="<->")
            temp=temp.next
        print("None")
dll=DoubleLinkedList()
n=int(input("Enter the number of elements to insert at end: "))
for i in range(n):
    val=int(input(f"Enter element{i+1}:"))
    dll.iae(val)
dll.display()


##insertion at begining
class Node:
    def __init__(self,data):
        self.data=data
        self.prev=None
        self.next=None
class DoubleLinkedList:
    def __init__(self):
        self.head=None
    def iab(self,data):
        newnode=Node(data)
        if self.head is None:
            self.head=newnode
        else:
            newnode.next=self.head
            self.head.prev=newnode
            self.head=newnode
    def display(self):
        temp=self.head
        print("Double Linked List:")
        while temp:
            print(temp.data,end="<->")
            temp=temp.next
        print("None")
dll=DoubleLinkedList()
n=int(input("Enter the number of elements to insert at begining: "))
for i in range(n):
    val=int(input(f"Enter element{i+1}:"))
    dll.iab(val)
dll.display()


#insertion at position at value
class Node:
    def __init__(self,data):
        self.data=data
        self.prev=None
        self.next=None
class DoubleLinkedList:
    def __init__(self):
        self.head=None
    def iap(self,pos,data):
        newnode=Node(data)
        if pos<=0:
            print("Invalid position")
            return
        if pos==1:
            newnode.next=self.head
            if self.head:
                self.head.prev=newnode
            self.head=newnode
            return
        temp=self.head
        for _ in range(pos-2):
            if temp is None:
                print("Position off range")
                return
            temp=temp.next
        if temp is None:
            print("No elements......")
            return
        newnode.next=temp.next
        newnode.prev=temp
        if temp.next:
            temp.next.prev=newnode
        temp.next=newnode

    def display(self):
        temp=self.head
        print("Double Linked List:")
        while temp:
            print(temp.data,end="<->")
            temp=temp.next
        print("None")
dll=DoubleLinkedList()
dll.iap(1,100)
n=int(input("Enter the number of elements to insert at begining: "))
for i in range(n):
    val=int(input(f"Enter element{i+1}:"))
    pos=int(input(f"Enter the position to insert {val}:"))
    dll.iap(pos,val)
dll.display()
