## [Serialize and Deserialize BST](https://leetcode.com/problems/serialize-and-deserialize-bst)

<p>Serialization is converting a data structure or object into a sequence of bits so that it can be stored in a file or memory buffer, or transmitted across a network connection link to be reconstructed later in the same or another computer environment.</p>

<p>Design an algorithm to serialize and deserialize a <b>binary search tree</b>. There is no restriction on how your serialization/deserialization algorithm should work. You need to ensure that a binary search tree can be serialized to a string, and this string can be deserialized to the original tree structure.</p>

<p><b>The encoded string should be as compact as possible.</b></p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> root = [2,1,3]
<strong>Output:</strong> [2,1,3]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> root = []
<strong>Output:</strong> []
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[0, 10<sup>4</sup>]</code>.</li>
	<li><code>0 &lt;= Node.val &lt;= 10<sup>4</sup></code></li>
	<li>The input tree is <strong>guaranteed</strong> to be a binary search tree.</li>
</ul>


## Solutions
#### 🐍 Python
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

# O(N) Solution with pre-order traversal
# first element is the root,
# all elements that are less than root are left part of tree
# bigger is right, process left and right recursively
class Codec:

    def serialize(self, root: TreeNode) -> str:
        """Encodes a tree to a single string.
        """
        if root is None:
            return ""
        else:
            return str(root.val) + ";" + self.serialize(root.left) + self.serialize(root.right)
        

    def deserialize(self, data: str) -> TreeNode:
        """Decodes your encoded data to tree.
        """
        if data == "":
            return None

        nodes = data.split(';')
        root = TreeNode(int(nodes[0]))
        root.left = \
            self.deserialize(';'.join([n for n in nodes[1:] if len(n) and int(n) < root.val]))
        root.right = \
            self.deserialize(';'.join([n for n in nodes[1:] if len(n) and int(n) >= root.val]))
        
        return root
            
        

# Your Codec object will be instantiated and called as such:
# Your Codec object will be instantiated and called as such:
# ser = Codec()
# deser = Codec()
# tree = ser.serialize(root)
# ans = deser.deserialize(tree)
# return ans
```
