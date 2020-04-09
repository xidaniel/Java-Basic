# Tree

## TreeNode class
         public class TreeNode {
              int key;
              TreeNode left;
              TreeNode right;

              public TreeNode(int key) {
                  this.key = key;
              }
          }
          
        
## BST is no duplicate element
  - It just use to find index
    
## Traversals
  - PerOrder
  
           public List<Integer> preOrder(TreeNode root) {
                 List<Integer> res = new ArrayList<Integer>();
                 if (root == null) {
                     return res;
                 }
                 Deque<TreeNode> stack = new LinkedList<TreeNode>();
                 stack.offerFirst(root);

                 while (!stack.isEmpty()) {
                     TreeNode cur = stack.pollFirst();
                     if (cur.right != null) {
                         stack.offerFirst(cur.right);
                     }
                     if (cur.left != null) {
                         stack.offerFirst(cur.left);
                     }
                     res.add(cur.key);
                 }
                 return res;
             }

  
  - InOrder
  
           public List<Integer> inOrder(TreeNode root) {
                 List<Integer> res = new ArrayList<Integer>();
                 if (root == null) {
                     return res;
                 }
                 Deque<TreeNode> stack = new LinkedList<TreeNode>();
                 TreeNode helper = root;
                 while (!stack.isEmpty() || helper != null) {
                     if (helper != null) {
                         stack.offerFirst(helper);
                         helper = helper.left;
                     } else {
                         helper = stack.pollFirst();
                         res.add(helper.key);
                         helper = helper.right;
                     }
                 }
                 return res;
             }
         
  - <b>PostOrder</b>
         
             public List<Integer> postOrder(TreeNode root) {
                 List<Integer> res = new ArrayList<Integer>();
                 if (root == null) {
                     return res;
                 }
                 Deque<TreeNode> stack = new LinkedList<>();
                 TreeNode prev = null;
                 stack.offerFirst(root);
                 while (!stack.isEmpty()) {
                     TreeNode cur = stack.pollFirst();
                     if (prev == null || cur == prev.left || cur == prev.right) {
                         if (cur.left != null) {
                             stack.offerFirst(cur.left);
                         } else if (cur.right != null) {
                             stack.offerFirst(cur.right);
                         } else {
                             res.add(cur.key);
                             stack.pollFirst();
                         }
                     } else if (prev == cur.left) {
                         if (cur.right != null) {
                             stack.offerFirst(cur.right);
                         } else {
                             res.add(cur.key);
                             stack.pollFirst();
                         }
                     } else {
                         res.add(cur.key);
                         stack.pollFirst();
                     }
                     prev = cur;
                 }
                 return res;
             }
    
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


