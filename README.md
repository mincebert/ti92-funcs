TI-89/92 MISCELLANEOUS FUNCTIONS
================================

This file contains a number of functions for the TI-89 (inc. Titanium) and
TI-92 (inc. Voyage 200) calculators, written in TI-BASIC.

All functions were written using version 3.10 of the operating system on a
Voyage 200 and are saved with a '.v2f' extension.  However, they have also
been tested on a TI-89 Titanium running the same version of software and
install without issue using TI DeviceExplorer.

They have also been tested on a TI-92 Plus with 2.09 of the operating system
and, if necessary, minor tweaks made to make them compatible (for example,
avoiding using of 'low<value<high' expressions).

These functions are ones I've just found the need for when solving particular
problems - there's no particular connection between them, although they are
organised into sets of related ones, often working together.


Numeric base functions
----------------------

The 'base' directory contains a number of functions to manage numbers in
different, arbitrary bases up to base 36: the characters making up large
bases are the list '{0-9}{A-Z}'.

As well as adding support for Octal and other bases, these may be useful
on a TI-92 without the Plus module (which doesn't have the built in base
functions), although this is untested.

Numbers in non-native bases are represented as strings and must (at the
present time) be converted back to one of the built-in numeric types
(e.g. decimal) to be used with arithmetic operations.

* frmbasen(str, base) - converts a string representation of number in 'str'
  in base 'base' to the current base (e.g. frmbasen("25",8) whilst in decimal
  mode converts 25 octal to decimal, i.e. 21); if a particular digit is
  invalid for the specified base (e.g. a '9' is used for a base 6 number),
  the value returned is 'undef' (TI-BASIC doesn't not appear to support
  deliberately throwing errors)

* tobasen(num, base) - converts the number 'num' (expressed in the current
  base mode) to a string in the base 'base' (e.g. tobasen(19,5) whilst in
  decimal mode converts 19 decimal to base 5, e.g. "34")

There is nothing about a string to determine which base it's in, so this must
be retained separately.


Set functions
-------------

The 'set' directory contains a number of functions to use lists of numbers as
a set.  The functions all maintain the lists in ascending numeric order to
optimise searching and other operations.

* setin(s, e) - returns whether element 'e' is present in set 's'; if so, the
  position is returned; if not, the position where it would be is returned as
  a negative number (e.g. setin({1, 3}, 2) returns -2); if the element is not
  present and would appear at the end of the list, -(length + 1) is returned

* setunion(s1, s2) - returns the union of sets 's1' and 's2', i.e. the set of
  all numbers in both s1 and s2; if any are duplicated, they are only
  included once

* setisect(s1, s2) - returns the intersection of sets 's1' and 's2', i.e. the
  set of numbers present in both s1 and s2

You can use normal list operations on a set (such as dim()) as long as the
order of elements is maintained and no duplicates created.  You can add a
single element to a set with 'setunion(s, {elem})'.

Sets of non-numeric elements are not supported at this time.
