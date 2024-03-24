# Name

LispMemory - Manage Memory in the Manner of Lisp

# Synopsis

# Description

Manage Memory in the Manner of Lisp

The following sections describe the methods in each functional area of this
module.  For an alphabetic listing of all methods by name see [Index](#index).

# Construct

Construct lisp memory

## new (%options)

Create a new lisp memory

       Parameter  Description
    1  %options   Options

**Example:**

    #latest:;

## newLisp ($memory, %options)

Create a new lisp memory pair. Pairs allow us to fanout quickly to create a structure of any size

       Parameter  Description
    1  $memory    Memory
    2  %options   Options

**Example:**

    if (1)
     {my $m = new;

      my $l = $m->newLisp;  # 𝗘𝘅𝗮𝗺𝗽𝗹𝗲

      my $a = $m->wrap(1);
      my $b = $m->wrap(2);
      my $p = $m->join($a, $b);
              $m->put ($l, $p);
      my $P = $m->get ($l);
      my ($A, $B) = $m->split($P);
      is_deeply($A, $a);
      is_deeply($B, $b);
      is_deeply($m->unwrap($A), 1);
      is_deeply($m->unwrap($B), 2);
      ok $m->isLisp($l);
      ok $m->isUserOrLisp($l);
     }

## wrap($memory, $value, %options)

Create a new user value

       Parameter  Description
    1  $memory    Memory
    2  $value     User value
    3  %options   Options

**Example:**

    if (1)
     {my $m = new;
      my $l = $m->newLisp;

      my $a = $m->wrap(1);  # 𝗘𝘅𝗮𝗺𝗽𝗹𝗲


      my $b = $m->wrap(2);  # 𝗘𝘅𝗮𝗺𝗽𝗹𝗲

      my $p = $m->join($a, $b);
              $m->put ($l, $p);
      my $P = $m->get ($l);
      my ($A, $B) = $m->split($P);
      is_deeply($A, $a);
      is_deeply($B, $b);
      is_deeply($m->unwrap($A), 1);
      is_deeply($m->unwrap($B), 2);
      ok $m->isLisp($l);
      ok $m->isUserOrLisp($l);
     }

## put ($memory, $key, $value, %options)

Map a key to a value

       Parameter  Description
    1  $memory    Memory
    2  $key       Key
    3  $value     Value
    4  %options   Options

**Example:**

    #latest:;

## get ($memory, $key, %options)

Get the value of a key in a lisp memory

       Parameter  Description
    1  $memory    Memory
    2  $key       Key
    3  %options   Options

**Example:**

    #latest:;

## unwrap  ($memory, $value, %options)

Unwrap a value returned from memory to retrieve its original value

       Parameter  Description
    1  $memory    Memory
    2  $value     Value
    3  %options   Options

**Example:**

    if (1)
     {my $m = new;
      my $l = $m->newLisp;
      my $a = $m->wrap(1);
      my $b = $m->wrap(2);
      my $p = $m->join($a, $b);
              $m->put ($l, $p);
      my $P = $m->get ($l);
      my ($A, $B) = $m->split($P);
      is_deeply($A, $a);
      is_deeply($B, $b);

      is_deeply($m->unwrap($A), 1);  # 𝗘𝘅𝗮𝗺𝗽𝗹𝗲


      is_deeply($m->unwrap($B), 2);  # 𝗘𝘅𝗮𝗺𝗽𝗹𝗲

      ok $m->isLisp($l);
      ok $m->isUserOrLisp($l);
     }

## join($memory, $a, $b, %options)

Join two values to make a lisp pair

       Parameter  Description
    1  $memory    Memory
    2  $a         First value
    3  $b         Second value
    4  %options   Key

**Example:**

    if (1)
     {my $m = new;
      my $l = $m->newLisp;
      my $a = $m->wrap(1);
      my $b = $m->wrap(2);

      my $p = $m->join($a, $b);  # 𝗘𝘅𝗮𝗺𝗽𝗹𝗲

              $m->put ($l, $p);
      my $P = $m->get ($l);
      my ($A, $B) = $m->split($P);
      is_deeply($A, $a);
      is_deeply($B, $b);
      is_deeply($m->unwrap($A), 1);
      is_deeply($m->unwrap($B), 2);
      ok $m->isLisp($l);
      ok $m->isUserOrLisp($l);
     }

## split   ($memory, $value, %options)

Split a lisp pair into two separate values

       Parameter  Description
    1  $memory    Memory
    2  $value     Lisp pair
    3  %options   Options

**Example:**

    if (1)
     {my $m = new;
      my $l = $m->newLisp;
      my $a = $m->wrap(1);
      my $b = $m->wrap(2);
      my $p = $m->join($a, $b);
              $m->put ($l, $p);
      my $P = $m->get ($l);

      my ($A, $B) = $m->split($P);  # 𝗘𝘅𝗮𝗺𝗽𝗹𝗲

      is_deeply($A, $a);
      is_deeply($B, $b);
      is_deeply($m->unwrap($A), 1);
      is_deeply($m->unwrap($B), 2);
      ok $m->isLisp($l);
      ok $m->isUserOrLisp($l);
     }

## getUser ($memory, $key, %options)

Get a value expected to be a user value and return it as such.

       Parameter  Description
    1  $memory    Memory
    2  $key       Key
    3  %options   Options

**Example:**

    #latest:;

## isUser  ($memory, $key, %options)

Test whether a value is a user value

       Parameter  Description
    1  $memory    Memory
    2  $key       Key
    3  %options   Options

**Example:**

    #latest:;

## isLisp  ($memory, $key, %options)

Test whether a value is a user value

       Parameter  Description
    1  $memory    Memory
    2  $key       Key
    3  %options   Options

**Example:**

    if (1)
     {my $m = new;
      my $l = $m->newLisp;
      my $a = $m->wrap(1);
      my $b = $m->wrap(2);
      my $p = $m->join($a, $b);
              $m->put ($l, $p);
      my $P = $m->get ($l);
      my ($A, $B) = $m->split($P);
      is_deeply($A, $a);
      is_deeply($B, $b);
      is_deeply($m->unwrap($A), 1);
      is_deeply($m->unwrap($B), 2);

      ok $m->isLisp($l);  # 𝗘𝘅𝗮𝗺𝗽𝗹𝗲

      ok $m->isUserOrLisp($l);
     }

## isPair  ($memory, $key, %options)

Test whether a value is a pair of values

       Parameter  Description
    1  $memory    Memory
    2  $key       Key
    3  %options   Options

## isUserOrLisp($memory, $key, %options)

Test whether a value is a user or lisp value

       Parameter  Description
    1  $memory    Memory
    2  $key       Key
    3  %options   Options

**Example:**

    if (1)
     {my $m = new;
      my $l = $m->newLisp;
      my $a = $m->wrap(1);
      my $b = $m->wrap(2);
      my $p = $m->join($a, $b);
              $m->put ($l, $p);
      my $P = $m->get ($l);
      my ($A, $B) = $m->split($P);
      is_deeply($A, $a);
      is_deeply($B, $b);
      is_deeply($m->unwrap($A), 1);
      is_deeply($m->unwrap($B), 2);
      ok $m->isLisp($l);

      ok $m->isUserOrLisp($l);  # 𝗘𝘅𝗮𝗺𝗽𝗹𝗲

     }

## null($memory, %options)

The lisp null value

       Parameter  Description
    1  $memory    Memory
    2  %options   Options

**Example:**

    #latest:;

## isNull  ($memory, $value, %options)

Test whether a value is a lisp null value

       Parameter  Description
    1  $memory    Memory
    2  $value     Value
    3  %options   Options

**Example:**

    #latest:;

# Data Structures

Standard data structures constructed in lisp memory

## Strings

Strings constructed from string memory

### newString   ($memory, $string, %options)

Create a string using lisp memory

       Parameter  Description
    1  $memory    Memory
    2  $string    String
    3  %options   Options

**Example:**

    if (1)
     {my $m = new;

      my $s = $m->newString("Hello World");  # 𝗘𝘅𝗮𝗺𝗽𝗹𝗲

      is_deeply($s, "l00000001");
      is_deeply($m, {lisps => 11, map => {
        l00000001 => "u00000072 l00000002",
        l00000002 => "u00000101 l00000003",
        l00000003 => "u00000108 l00000004",
        l00000004 => "u00000108 l00000005",
        l00000005 => "u00000111 l00000006",
        l00000006 => "u00000032 l00000007",
        l00000007 => "u00000087 l00000008",
        l00000008 => "u00000111 l00000009",
        l00000009 => "u00000114 l00000010",
        l00000010 => "u00000108 l00000011",
        l00000011 => "u00000100 l",
      }});
      is_deeply($m->getString($s),           "Hello World");
      is_deeply($m->getString($s, first=>5), "Hello");
     }

### getString   ($memory, $string, %options)

Return the characters in a string

       Parameter  Description
    1  $memory    Memory
    2  $string    String
    3  %options   Options

## Fixed Arrays

Create fixed length arrays.  The lengths of these arrays is a power of two.

### newArray($memory, $length, %options)

Create a string using lisp memory

       Parameter  Description
    1  $memory    Memory
    2  $length    Length of array
    3  %options   Options

**Example:**

    if (1)
     {my $m = new;

      my $s = $m->newArray(3);  # 𝗘𝘅𝗮𝗺𝗽𝗹𝗲

      is_deeply($s, "l00000006");
      is_deeply($m, {lisps => 6, map => {
        l00000001 => "l",
        l00000002 => "l",
        l00000003 => "l",
        l00000004 => "l00000001 l00000002",
        l00000005 => "l00000003 l",
        l00000006 => "l00000004 l00000005",
       }})
     }

### getArray($memory, $array, $index, %options)

Return the value of an indexed element of the array

       Parameter  Description
    1  $memory    Memory
    2  $array     Array
    3  $index     Index
    4  %options   Options

# Hash Definitions

## Lisp::Memory Definition

Lisp memeory

### Output fields

#### lisps

Number of lisp pairs

#### map

Maps a key to a value

# Index

1 [get](#get) - Get the value of a key in a lisp memory

2 [getArray](#getarray) - Return the value of an indexed element of the array

3 [getString](#getstring) - Return the characters in a string

4 [getUser](#getuser) - Get a value expected to be a user value and return it as such.

5 [isLisp](#islisp) - Test whether a value is a user value

6 [isNull](#isnull) - Test whether a value is a lisp null value

7 [isPair](#ispair) - Test whether a value is a pair of values

8 [isUser](#isuser) - Test whether a value is a user value

9 [isUserOrLisp](#isuserorlisp) - Test whether a value is a user or lisp value

10 [join](#join) - Join two values to make a lisp pair

11 [new](#new) - Create a new lisp memory

12 [newArray](#newarray) - Create a string using lisp memory

13 [newLisp](#newlisp) - Create a new lisp memory pair.

14 [newString](#newstring) - Create a string using lisp memory

15 [null](#null) - The lisp null value

16 [put](#put) - Map a key to a value

17 [split](#split) - Split a lisp pair into two separate values

18 [unwrap](#unwrap) - Unwrap a value returned from memory to retrieve its original value

19 [wrap](#wrap) - Create a new user value

# Installation

This module is written in 100% Pure Perl and, thus, it is easy to read,
comprehend, use, modify and install via **cpan**:

    sudo cpan install Lisp::Memory

# Author

[philiprbrenan@gmail.com](mailto:philiprbrenan@gmail.com)

[http://prb.appaapps.com](http://prb.appaapps.com)

# Copyright

Copyright (c) 2016-2023 Philip R Brenan.

This module is free software. It may be used, redistributed and/or modified
under the same terms as Perl itself.
