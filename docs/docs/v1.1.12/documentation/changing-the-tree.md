---
title: "Dynamically changing the tree"
excerpt: ""
---
[block:api-header]
{
  "type": "basic",
  "title": "Changing node attributes"
}
[/block]
Changing any attributes on the node itself will be reflected immediately, since change detection will force the tree node components to re-render.
[block:api-header]
{
  "type": "basic",
  "title": "Adding / Removing nodes"
}
[/block]
After adding or removing nodes from the tree, one must call the `update` method on the treeModel for it to take affect.

For example:
[block:code]
{
  "codes": [
    {
      "code": "<Tree #tree nodes=\"nodes\"></Tree>\n\n@ViewChild(TreeComponent)\nprivate tree: TreeComponent;\n\naddNode() {\n  // add node, then:\n  this.tree.treeModel.update()\n}",
      "language": "javascript"
    }
  ]
}
[/block]
This is due to the fact that the treeModel builds its own model around the nodes data, to calculate node levels, paths, parent links etc. So it must be informed of any change to the nodes' structure.

Calling update will have no effect on the tree status, i.e. current selected node, current focused node, current expanded nodes, etc.