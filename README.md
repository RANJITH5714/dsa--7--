max = int(input("Enter max number: "))

odd_numbers = []

for i in range(1, max):
    if i % 2 == 1:
        odd_numbers.append(i)

print("Odd numbers: ", odd_numbers)
class Node:
    def __init__(self, data=None, next=None):
        self.data = data
        self.next = next

class LinkedList:
    def __init__(self):
        self.head = None

   def print(self):
        if self.head is None:
            print("Linked list is empty")
            return
        itr = self.head
        llstr = ''
        while itr:
            llstr += str(itr.data)+' --> ' if itr.next else str(itr.data)
            itr = itr.next
        print(llstr)

   def get_length(self):
        count = 0
        itr = self.head
        while itr:
            count+=1
            itr = itr.next

   return count

   def insert_at_begining(self, data):
        node = Node(data, self.head)
        self.head = node

   def insert_at_end(self, data):
        if self.head is None:
            self.head = Node(data, None)
            return

   itr = self.head

   while itr.next:
         itr = itr.next

  itr.next = Node(data, None)

  def insert_at(self, index, data):
        if index<0 or index>self.get_length():
            raise Exception("Invalid Index")

   if index==0:
       self.insert_at_begining(data)
       return

  count = 0
   itr = self.head
    while itr:
      if count == index - 1:
          node = Node(data, itr.next)
           itr.next = node
           break

   itr = itr.next
    count += 1

   def remove_at(self, index):
        if index<0 or index>=self.get_length():
            raise Exception("Invalid Index")

   if index==0:
       self.head = self.head.next
       return

  count = 0
  itr = self.head
  while itr:
       if count == index - 1:
           itr.next = itr.next.next
           break

   itr = itr.next
     count+=1

   def insert_values(self, data_list):
        self.head = None
        for data in data_list:
            self.insert_at_end(data)


if __name__ == '__main__':
    ll = LinkedList()
    ll.insert_values(["banana","mango","grapes","orange"])
    ll.insert_at(1,"blueberry")
    ll.remove_at(2)
    ll.print()

   ll.insert_values([45,7,12,567,99])
   ll.insert_at_end(67)
   ll.print()
  
   stock_prices = []
with open("stock_prices.csv","r") as f:
    for line in f:
        tokens = line.split(',')
        day = tokens[0]
        price = float(tokens[1])
        stock_prices.append([day,price])

  class HashTable:  
    def __init__(self):
        self.MAX = 10
        self.arr = [[] for i in range(self.MAX)]
        
   def get_hash(self, key):
        hash = 0
        for char in key:
            hash += ord(char)
        return hash % self.MAX
    
  def __getitem__(self, key):
        arr_index = self.get_hash(key)
        for kv in self.arr[arr_index]:
            if kv[0] == key:
                return kv[1]
           
   def __setitem__(self, key, val):
        h = self.get_hash(key)
        found = False
        for idx, element in enumerate(self.arr[h]):
            if len(element)==2 and element[0] == key:
                self.arr[h][idx] = (key,val)
                found = True
        if not found:
            self.arr[h].append((key,val))
        
   def __delitem__(self, key):
        arr_index = self.get_hash(key)
        for index, kv in enumerate(self.arr[arr_index]):
            if kv[0] == key:
                print("del",index)
                del self.arr[arr_index][index]
{
 "cells": [
  {
   "cell_type": "code",
   "execution_count": 56,
   "metadata": {},
   "outputs": [],
   "source": [
    "class HashTable:  \n",
    "    def __init__(self):\n",
    "        self.MAX = 10\n",
    "        self.arr = [None for i in range(self.MAX)]\n",
    "        \n",
    "    def get_hash(self, key):\n",
    "        hash = 0\n",
    "        for char in key:\n",
    "            hash += ord(char)\n",
    "        return hash % self.MAX\n",
    "    \n",
    "    def __getitem__(self, index):\n",
    "        h = self.get_hash(index)\n",
    "        return self.arr[h]\n",
    "    \n",
    "    def __setitem__(self, key, val):\n",
    "        h = self.get_hash(key)\n",
    "        self.arr[h] = val    "
   ]
  },
