duplicate-letters
=================

Using PHP I demonstrate one way to produce an array of duplicated letters that are contained in a string. For example, if the input string is 'mississippi', the output array will be ['i', 's', 'p' ].

The reason I posted this is because many of the solutions have a run time of O(n^2).
The speed of this is 2n where n is the length of the string. In Big O notation this is O(n). 
