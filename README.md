# Implementation-of-Huffman-Coding-Algorithm
## Aim:
To implement Huffman coding to compress the data using Python.

## Software Required:
1. Anaconda - Python 3.7

## Algorithm:
### Step 1: 
Assign the input string.
### Step 2:
Create the required tree nodes.
### Step 3:
Create a function to implement the huffman coding.
### Step 4:
Calculate frequency of occurence.
### Step 5:
Print the characters and its Huffman code.
## Program:
~~~
Developed by : Rohithkumar S V
Registration Number : 212221230084
~~~
### Get the input String:
~~~
string=input("Rohithkumar S V 212221230084")
class NodeTree(object):
  def __init__(self,left=None,right=None):
    self.left=left
    self.right=right
    
  def children(self):
    return(self.left,self.right)
~~~        
### Create tree nodes:
~~~
#Main function implementing huffman coding

def huffman_code_tree(node,left=True,binString=''):
  if type(node) is str:
    return{node: binString}
  (l,r) = node.children()
  d=dict()
  d.update(huffman_code_tree(l,True,binString +'0'))
  d.update(huffman_code_tree(r,False,binString +'1'))
  return d
~~~    
### Main function to implement huffman coding:
~~~
#Calculating frequency

freq={}
for c in string:
  if c in freq:
    freq[c] +=1
  
  else:
    freq[c] = 1

freq=sorted(freq.items(),key=lambda x: x[1],reverse=True)
nodes=freq
~~~
### Calculate frequency of occurrence:
~~~
while len(nodes)>1:
  (key1,c1)=nodes[-1]
  (key2,c2)=nodes[-2]
  nodes=nodes[:-2]
  node =NodeTree(key1,key2)
  nodes.append((node,c1+c2))
  nodes=sorted(nodes,key=lambda x: x[1],reverse=True)
~~~    
### Print the characters and its huffmancode:
~~~

huffmanCode = huffman_code_tree(nodes[0][0])

print(' Char | Huffman code ')
print('----------------------')
for (char,frequency) in freq:
    print(' %-4r |%12s' % (char,huffmanCode[char]))
~~~
## Output:
![huffman out](huffsv.png)




## Result:

Thus, the huffman coding was implemented to compress the data using python programming.
