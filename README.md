Download Link: https://assignmentchef.com/product/solved-cs570-assignment-3-a-double-linked-list-with-fast-accessing
<br>
<h1>Assignment</h1>

This assignment consists in implementing a double-linked list <em>with fast accessing</em>. Fast accessing is provided by an internal <em>index</em>. An index is just an array-based list that stores references to nodes. Before going further, let’s take a step back and recall some basic notions regarding double-linked lists.

As explained in the lectures, a double-linked list (DLL) is a list in which each node has a reference to the next one and also a reference to the previous one. The corresponding Java class therefore has three data fields or attributes:

<ul>

 <li>Node&lt;E&gt; head</li>

 <li>Node&lt;E&gt; tail</li>

 <li><strong>int </strong>size</li>

</ul>

Accessing the elements of the list is therefore realized through the references head and tail. For example, the <em>i</em>-th element is obtained by starting from head and then jumping through <em>i − </em>1 nodes. Indeed, just like single-linked lists, accessing an element in a DLL is of time complexity <em>O</em>(<em>n</em>). In order to alleviate this situation this assignment asks you to implement an enhanced DLL, <em>Indexed DLL </em>or IDLL. An IDLL includes an additional attribute, namely an <em>index</em>. An index is simply a list based array that stores the references to each node in the DLL. Since the access to an element in an array-based list is <em>O</em>(1), this will allow the users of IDLL to enjoy the benefits of fast access, and at the same time, use a list implementation which does not waste memory given that it may shrink or grow dynamically, a property which is known to be one of the advantages of linked-lists in general. The way faster access is achieved is that the get(<strong>int </strong>i) operation, in its implementation, rather than starting from the head of the list and traversing each node until the <em>i</em>-th node is reached, it simply uses the get(<strong>int </strong>i) operation of an array-based list or index called indices which it maintains, together with the other data fields.

This does come at a price though. We need more memory to store the array-based list indices for one thing. Another is that all the operations of IDLL will have to maintain the indices up to date. For example, whenever a new element is added to the DLL, the array-based indices will have to be updated by inserting the new reference.

You are requested to implement a class IDLList&lt;E&gt; that encodes Indexed DLLs, following the guidelines presented in the next section.

Design of the Class <sub>IDLList&lt;E&gt;</sub>

<strong>2.1.1          The Inner Class </strong><strong>Node&lt;E&gt;</strong>

First of all, an inner class Node&lt;E&gt; should be declared. This class should include three data fields:

<ul>

 <li>E data</li>

 <li>Node&lt;E&gt; next</li>

 <li>Node&lt;E&gt; prev</li>

</ul>

It should also include the following operations:

<ul>

 <li>Node (E elem), a constructor that creates a node holding elem.</li>

 <li>Node (E elem, Node&lt;E&gt; prev, Node&lt;E&gt; next), a constructor that creates a node holding elem, with next as next and prev as prev.</li>

</ul>

<strong>2.1.2           The Class </strong><strong>IDLList&lt;E&gt;</strong>

The class IDLList&lt;E&gt; should include the declaration of this inner private class Node&lt;E&gt;. Apart from that, it should have four data fields:

<ul>

 <li>Node&lt;E&gt; head</li>

 <li>Node&lt;E&gt; tail</li>

 <li><strong>int </strong>size</li>

 <li>ArrayList&lt;Node&lt;E&gt;&gt; indices</li>

</ul>

Note that indices is an array-based list of references to nodes. A reference to the first element of list is therefore available as the first element of indices. A reference to the second element of the list is therefore the second element in indices. And so on.

You are requested to implement the following operations (a summary is provided at the end of this assignment, in a UML diagram) for IDLList&lt;E&gt;:

<ul>

 <li><strong>public </strong>IDList (), that creates an empty double-linked list.</li>

 <li><strong>public boolean </strong>add (<strong>int </strong>index, E elem) that adds elem at position index (counting from wherever head is). It uses the index for fast access.</li>

 <li><strong>public boolean </strong>add (E elem) that adds elem at the head (i.e. it becomes the first element of the list).</li>

 <li><strong>public boolean </strong>append (E elem) that adds elem as the new last element of the list (i.e. at the tail).</li>

 <li><strong>public </strong>E get (<strong>int </strong>index) that returns the object at position index from the head. It uses the index for fast access. Indexing starts from 0, thus get(0) returns the head element of the list.</li>

 <li><strong>public </strong>E getHead () that returns the object at the head.</li>

 <li><strong>public </strong>E getLast () that returns the object at the tail.</li>

 <li><strong>public int </strong>size() that returns the list size.</li>

 <li><strong>public </strong>E remove() that removes and returns the element at the head.</li>

 <li><strong>public </strong>E removeLast () that removes and returns the element at the tail.</li>

 <li><strong>public </strong>E removeAt (<strong>int </strong>index) that removes and returns the element at the index index. Use the index for fast access.</li>

 <li><strong>public boolean </strong>remove (E elem) that removes the first occurrence of elem in the list and returns true. Return false if elem was not in the list.</li>

 <li><strong>public </strong>String toString(). That presents a string representation of the list.</li>

</ul>

The following operations require index maintenance (i.e. they have to assign or modify the index):

<ul>

 <li><strong>public </strong>IDLList ().</li>

 <li><strong>public boolean </strong>add (<strong>int </strong>index, E elem).</li>

 <li><strong>public boolean </strong>add (E elem).</li>

 <li><strong>public boolean </strong>append (E elem).</li>

 <li><strong>public </strong>E remove().</li>

 <li><strong>public </strong>E removeLast ().</li>

 <li><strong>public </strong>E removeAt (<strong>int </strong>index).</li>

 <li><strong>public boolean </strong>remove (E elem).</li>

</ul>