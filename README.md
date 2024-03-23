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
      is_deeply($m->unwrap($A), 1);
      is_deeply($m->unwrap($B), 2);
    
      ok $m->isLisp($l);  # 𝗘𝘅𝗮𝗺𝗽𝗹𝗲

      ok $m->isUserOrLisp($l);
     }
    

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
      is_deeply($m->unwrap($A), 1);
      is_deeply($m->unwrap($B), 2);
      ok $m->isLisp($l);
    
      ok $m->isUserOrLisp($l);  # 𝗘𝘅𝗮𝗺𝗽𝗹𝗲

     }
    

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

2 [getUser](#getuser) - Get a value expected to be a user value and return it as such.

3 [isLisp](#islisp) - Test whether a value is a user value

4 [isUser](#isuser) - Test whether a value is a user value

5 [isUserOrLisp](#isuserorlisp) - Test whether a value is a user or lisp value

6 [join](#join) - Join two values to make a lisp pair

7 [new](#new) - Create a new lisp memory

8 [newLisp](#newlisp) - Create a new lisp memory pair.

9 [put](#put) - Map a key to a value

10 [split](#split) - Split a lisp pair into two separate values

11 [unwrap](#unwrap) - Unwrap a value returned from memory to retrieve its original value

12 [wrap](#wrap) - Create a new user value

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
