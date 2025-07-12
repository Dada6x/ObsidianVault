
Binary Search Trees
Balanced Trees
B-Trees
Heap
Graph
DFS BFS & topological sort
Spanning Trees
Dijkstra 
Floyd washall



# lec1 Intro To Trees 
---

Trees are Non-Linear [[Data Structures]]

# ~={green}Trees=~

what are trees ?
trees are set of items called `Nodes` that are related to eachother with whats named `Edges`
Starting from Root Node , every node has one parent only , but the root is special it dosent have parents 

## types of Nodes in Trees

~={yellow}External Nodes =~: so do called Leaves , those are the nodes at the end of the tree having no children 

~={yellow}Internal Nodes=~ normal nodes and have children .

### ~={red}some important Nodes =~

| N-        | D(node)                                                   | H(node)                                                                          | D(tree)                                                                                | H(tree)                                                                       | Width                            | Level               |
| --------- | --------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | -------------------------------- | ------------------- |
| عدد العقد | درجة العقدة : تشير الى عدد الفروع(الابناء )التي يصدؤ منها | ارتفاع العقدة هو بعد هذه العقدة عن عقدة الجذر Root <br>~={red}وهو عدد الوصلات =~ | تشير الى اقص عدد من الفروع التي يمكن ان ينبثق من احد العقد <br>اي اكبر درجة لعقدة فيها | المسافة العمودية من قاعدتها root الى اعلى نقطة فيها اي اكبر ارتفاع لعقدة فيها | هو اكبر عدد عقد في احد المستويات | ارتفاع اعلى عقدة +1 |
|           |                                                           |                                                                                  |                                                                                        |                                                                               |                                  |                     |

## ~={cyan}Types Of Trees=~

[[#Binary Trees]]
[[#Binary Search Trees]]
[[#AVL Trees]] 
[[#B-Trees]]
[[#Heap]]


### Binary Trees 
كلمة Binary تعني ثنائي ومنها فإن الشجرة الثنائية تعرف حيث كل عقدة منها تتفرع إلى عقدتين اثنتين على الاكثر، عقدة يسارية )Node Child-Left )وعقدة يمينية ) Child-Right .
عدد الابناء يتراوح بين (0-1-2)
الاشجار العادية غير محدودة الابناء
##### full Tree :
جميع مستويات العقدة مملوءة بالعقد
![[Pasted image 20250712131148.png]]

#### Complete Tree :
هي شجرة فيها كل مستو ممتلئ عدا المستوى الاخير يمكن ان يحوي فرغات لكن من الجزء اليميني حصرا
![[Pasted image 20250712131242.png]]

##### Linear Tree :
هي شجرة فيها لكل عقدة ابن واحد فقط

Binary Tree Representation 

- pointers 
- one-Dimensional Arrays
- Two-dimensional Arrays 
## Binary Tree With Pointers 
```
// Node 
public Class Node {
int data;
Node left,right;
Node(int data){
this.data=data;
left=null;
right=null;
	}
}

public class Tree{
Node root;
Tree(){
root=null;
	}
}


class Main{
psvm(){
	Tree tree = New Tree();
	tree.root=new Node(5);
	tree.root.left= new Node(3);
	tree.root.right= new Node(6);
		}
	}
```
-----

- Two-Dimensional Arrays
![[Pasted image 20250712132231.png]]

----

- one-Dimensional Arrays
![[Pasted image 20250712132252.png]]


---
#### Binary Search Trees
this have an condition additional to the number of children thats the left children must be lesser than the root and the children on the right are bigger than the root .

### ~={orange}Whats the Point of the BST?=~
its has advantges on the side of the (Searching , Deletion ,Insertion), 
in the Normal one we would need to Scan the Whole tree to do any of these operation 
but in the **BST** we would just search for the node depending on the root 

> each time the n is reduced to the half of the original size (if the left subtree= right subtree)
> ex : if we have like 100 items , and we want to search for the node that its data is 14
> 14 <50 => 14< 25 => found it  

## ~={green}1.Search =~
we compare the root with our value we want to find 
if more we search up the Right Sub tree 
if less we search up the left Sub tree.

about the ~={orange}Complexity=~
if the tree is lienar tree : O(N).
if the tree is full tree : O(Log n).
if the value we looking for is the root O(1).

## ~={green}2.Insertion =~
it goes two ways 
- we can add Leafs ( nodes without children )
- adding in the root 

### ~={green}3.Deletion=~
it goes three ways 
- deleting an Leaf
- deleting an node with one child 
- deleting an node with two children
---
# ~={purple}Balanced Tree=~s
balanced trees are special condetion of the bst with additional condition called `balance factor` that reduce the **heigt** of the Tree and with that reduce the Time Complexity of the tree , there are many types of balanced Trees( AVL , Red-Black Trees, Balanced Trees)
>All balanced Trees are Binary Trees

## ~={green}AVL Trees :=~
named after **A**delson-**V**elesky -**L**indis
the avl is an BST that have an balance Factor that takes theses values ( -1,0,1)
O(log n )
~={red}balance Factor :=~
its the hight of the left subtree - the hight of the rightsubtree

what if the balance factor isnt of theses values ??
=> we retain the balance using the `Rotations`

## ~={cyan}Rotations =~
its the operation to change the places of the nodes with maintaing the blacnce factor condition 
#### types of the Rotations 
##### ~={purple}Complex rotations :=~
- right left rotations.
- left right rotations.
##### ~={purple}sinple rotations :=~
- right rotations.
- left rotations.
the addition and the deletion and are the exact same with the BST just require the fixes with the rotations 
  how to select the right rotation to the AVL 
### Insertion 
addition leafs complexity O(h)
### Deletion
addition leafs complexity O(h)
`end of Lecture 3`


---
### B-Trees 



---

### Heap 

---