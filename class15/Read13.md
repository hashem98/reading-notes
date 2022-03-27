# Tree 

every tree have 
1. Node it include value and references
2. Root :top node
3. K : A number that specifies the maximum number of children any node may have
4. left and right node 
5. leaf node doesn't have children
6. Height - The height of a tree is the number of edges from the root to the furthest leaf

## Traversals
1. Depth first traversal is where we prioritize going through the depth (height) of the tree first there's three methods
    1. Pre-order: root >> left >> right
    2. In-order: left >> root >> right
    3. Post-order: left >> right >> root

* The most common way to traverse through a tree is to use *recursion*

2. Breadth first traversal iterates through the tree by going through each level of the tree node-by-node
> breadth first traversal uses a queue (instead of the call stack via recursion)

* What Is Recursion?

Recursion is a basic programming technique you can use in Java, in which a method calls itself to solve some problem. A method that uses this technique is recursive. Many programming problems can be solved only by recursion, and some problems that can be solved by other techniques are better solved by recursion.

One of the classic problems for introducing recursion is calculating the factorial of an integer. The factorial of any given integer — call it n so that you sound mathematical — is the product of all the integers from 1 to n. Thus, the factorial of 5 is 120: 5 x 4 x 3 x 2 x 1.

The recursive way to look at the factorial problem is to realize that the factorial for any given number n is equal to n times the factorial of n–1, provided that n is greater than 1. If n is 1, the factorial of n is 1.

This definition of factorial is recursive because the definition includes the factorial method itself. It also includes the most important part of any recursive method: an end condition. The end condition indicates when the recursive method should stop calling itself. In this case, when n is 1, it just returns 1. Without an end condition, the recursive method keeps calling itself forever
  ```
  private static long factorial(int n)
     {
    if (n == 1)
        return 1;
    else
        return n * factorial(n-1);
    }
   ```
# Binary Tree Vs K-ary Trees

> Trees can have any number of children per node, but Binary Trees restrict the number of children to two
> If Nodes are able have more than 2 child nodes, we call the tree that contains them a K-ary Tree

# Binary Search Trees

A Binary Search Tree (BST) is a type of tree that does have some structure attached to it. In a BST, nodes are organized in a manner where all values that are smaller than the root are placed to the left, and all values that are larger than the root are placed to the right.

