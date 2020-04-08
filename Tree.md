# Tree

## TreeNode class
         public class TreeNode {
              private int key;
              private TreeNode left;
              private TreeNode right;

              public TreeNode(int key) {
                  this.key = key;
              }
          }
          
        
## BST is no duplicate element
  - It just use to find index
    
## Traversals
  - PerOrder
  - InOrder
  - PostOrder
    
## Search in BST
          ### recursive
          public TreeNode search(TreeNode root, int target) {
                  if (root == null || root.key == target) {
                      return root;
                  }
                  if (root.key > target) {
                      return search(root.left, target);
                  } else {
                      return search(root.right, target);
                  }
              }
              
          ### iterative
          public TreeNode search(TreeNode root, int target) {
                  TreeNode currentNode = root;
                  while (currentNode != null && currentNode.key != target) {
                      if (currentNode.key > target) {
                          currentNode = currentNode.left;
                      } else {
                          currentNode = currentNode.right;
                      }
                  }
                  return currentNode;
              }

## Insert in BST
  - Find the different recursive1 and recursive2
  - Notice interface design
  
            ### recursive1  not recommend this method 
            public TreeNode insert(TreeNode root, int target) {
                    if (root == null) {
                        TreeNode newRoot = new TreeNode(target);
                        return newRoot;
                    }
                    if (root.key > target) {
                        root.left = insert(root.left, target);
                    } else if (root.key < target){
                        root.right = insert(root.right, target);
                    }
                    return root;
                }
       ---------------------------------------------------------------------------
              ### recursive2
              public TreeNode insert(TreeNode root, int target) {
                    if (root == null) {
                        return new TreeNode(target);
                    }
                    helper(root, target);
                    return root;
               }

              public static void helper(TreeNode root, int target){
                  if (target == root.key) {
                      return;
                  } else if (target < root.key) {
                      if (root.left == null) {
                          root.left = new TreeNode(target);
                      } else {
                          helper(root.left, target);
                      }
                  } else {
                      if (root.right == null) {
                          root.right = new TreeNode(target);
                      } else {
                          helper(root.right, target);
                      }
                   }
                }
       ----------------------------------------------------------------------------         
               ### Iterative
               public TreeNode iterate(TreeNode root, int target){
                    TreeNode newNode = new TreeNode(target);
                    if (root == null) {
                        return newNode;
                    }
                    TreeNode currNode = root;
                    while (currNode.key != target) {
                        if (currNode.key > target) {
                            if (currNode.left != null) {
                                currNode = currNode.left;
                            } else {
                                currNode.left = newNode;
                                break;
                            }
                        } else {
                            if (currNode.right != null) {
                                currNode = currNode.right;
                            } else {
                                currNode.right = newNode;
                                break;
                            }
                        }
                      }
                      return root;
                  }


