title: "[LeetCode] Serialize and Deserialize Binary Tree"
date: 2016-02-28 18:37:37
tags: [LeetCode, Tree]
---

## Analysis:
> Since this is not a complete binary search tree, we cannot use the index to dertermine the position of the child nodes.
> use the preorder traversal to store the information

## Time Complexity:
> * O(n)

## Space Complexity：
> * O(n)


## Code
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Codec:


    def serialize(self, root):
        """Encodes a tree to a single string.

        :type root: TreeNode
        :rtype: str
        """
        if root is None:
            return ""
        valist = []
        def doit(node):
            if node is None:
                 valist.append('#')
            else:
                valist.append(str(node.val)) 
                doit(node.left)
                doit(node.right)

        doit(root)
        return ' '.join(valist)


    def deserialize(self, data):
        """Decodes your encoded data to tree.

        :type data: str
        :rtype: TreeNode
        """

        leng = len(data)
        if leng == 0:
            return None

        vals = iter(data.split())

        def doit():
            val = next(vals)
            if val == '#':
                return None
            curNode = TreeNode(int(val))
            curNode.left = doit()
            curNode.right = doit()
            return curNode
        return doit()




        

# Your Codec object will be instantiated and called as such:
# codec = Codec()
# codec.deserialize(codec.serialize(root))

```
