12/04/2024

[Slideshow Link](https://docs.google.com/presentation/d/1YKV1xbEsPPlF8hLMvJiLB_agWoKt10AwTUTOvhXU8Rc/edit#slide=id.g317352aa759_0_0)

RB Tree Deletion
 - remove the node, replace the node with its child (if two chose better), then rearrange the tree 

Case 1
 - sibling of the double black node is red, will be later unbalanced
 - start by rotating the red sibling with the parent
 - recolor the sibling to black and the parent to red (root must be black)

Case 2
- sibling of the double black is a black node with at least one red child
- perform rotation around the paren, and recolor the parent, sibling, and far child to maintain the properties

Case 3
 - sibling of the double black and the siblings children are all black
 - recolor to rebalance the tree
 - recolor the sibling red, if parent was red, resolve the double black by turning it black, 
 - propogate back up treating the parent as the new double black node
 - otherwise repeat the process for the parent