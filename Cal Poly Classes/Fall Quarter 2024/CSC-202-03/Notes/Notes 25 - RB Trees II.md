12/02/2024

[Slideshow Link](https://docs.google.com/presentation/d/1vIwuX_uISmnFNHr5MG_1FysnGfxvsH8s80Qr-tSc5T0/edit#slide=id.g2ce5dae6584_0_266)

RB Insertion
 - new nodes are always red
 - problem cases

Case 1
 - node is a root, color it as black
 - reason the root needs to be black

Case 2
 - no uncle because parent is the root
 - parent is black
 - no changes

Case 3
 - Node z is red but it's parent is also red
 - recolor the parent, uncle, and grandparent to restore the RB properties
 - recoloring may propagate back up to the root, if root becomes red, recolor is back to black to maintain the root property

Case 4a
 - Z and Parent are Both Right Children are red, needs rotation, remember null children are black
 - basically showing a height imbalance

Case 4b
 - Triangle line complications
 - Z and Parent form a triangle
 - goal is to turn the violation into a line, and then fix the line
 - calls a right rotation the parent and cild if on right, if on left perform a left rotation
 - child node becomes parent, parent becomes right node of child