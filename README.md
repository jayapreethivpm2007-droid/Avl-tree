AVL Tree Deletion Example

class Node:
    def __init__(self,key):
        self.key = key
        self.left = None
        self.right = None

def minValueNode(node):
    current = node
    while current.left != None:
        current = current.left
    return current

def delete(root,key):

    if root == None:
        return root

    if key < root.key:
        root.left = delete(root.left,key)

    elif key > root.key:
        root.right = delete(root.right,key)

    else:
        if root.left == None:
            temp = root.right
            root = None
            return temp

        elif root.right == None:
            temp = root.left
            root = None
            return temp

        temp = minValueNode(root.right)
        root.key = temp.key
        root.right = delete(root.right,temp.key)

    return root

def inorder(root):
    if root:
        inorder(root.left)
        print root.key,
        inorder(root.right)

root = Node(20)
root.left = Node(10)
root.right = Node(30)

print "Before Deletion:"
inorder(root)

root = delete(root,10)

print "\nAfter Deletion:"
inorder(root)
Output:

Before Deletion:
10 20 30

After Deletion:
20 30
