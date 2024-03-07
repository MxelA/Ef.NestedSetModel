This is a .NET8 package for working with trees in relational databases.

__Contents:__
- [Theory](#what-are-nested-sets)
- [Documentation](#documentation)


  
What are nested sets?
---------------------

Nested sets or [Nested Set Model](http://en.wikipedia.org/wiki/Nested_set_model) is
a way to effectively store hierarchical data in a relational table. From wikipedia:

> The nested set model is to number the nodes according to a tree traversal,
> which visits each node twice, assigning numbers in the order of visiting, and
> at both visits. This leaves two numbers for each node, which are stored as two
> attributes. Querying becomes inexpensive: hierarchy membership can be tested by
> comparing these numbers. Updating requires renumbering and is therefore expensive.

### Applications

Nested Set Model shows good performance. It is tuned to be fast for
getting related nodes. It'is ideally suited for building multi-depth menu or
categories for shop or similar things.

Documentation
-------------

Suppose that we have a model `Category`; a `$node` variable is an instance of that model
and the node that we are manipulating. It can be a fresh model or one from database.

#### Creating Root node

When you simply creating a node, it will be appended to the end of the tree:

```c#
 _db = new AppDbContext();
 _ns = new NestedSetModelManager<Node, int, int?>(_db);
Node clothing = _ns.InsertRoot(NewNode("Clothing"), NestedSetModelInsertMode.Right);
```
