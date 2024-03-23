\#!/usr/bin/perl -I/home/phil/perl/cpan/DataTableText/lib/
\#-------------------------------------------------------------------------------
\# Lisp memory
\# Philip R Brenan at appaapps dot com, Appa Apps Ltd Inc., 2024
\#-------------------------------------------------------------------------------
use v5.34;
package Lisp::Memory;
use warnings FATAL => qw(all);
use strict;
use Carp;
use Data::Dump qw(dump);
use Data::Table::Text qw(:all);

makeDieConfess;

sub new(%)                                                                      # Create a new lisp memory
 {my (%options) = @\_;                                                           # Options
  genHash(\_\_PACKAGE\_\_,                                                          # Lisp memeory
    map   => {},                                                                # Maps a key to a value
    lisps => 0,                                                                 # Number of lisp pairs
   );
 }

sub newLisp($%)                                                                 # Create a new lisp memory pair. Pairs allow us to fanout quickly to create a structure of any size
 {my ($memory, %options) = @\_;                                                  # Memory, options
  "l".(++$memory->lisps)                                                        # The next pair available
 }

sub wrap($$%)                                                                   # Create a new user value
 {my ($memory, $value, %options) = @\_;                                          # Memory, user value, options
  "u$value"                                                                     # User value
 }

sub put($$$%)                                                                   # Map a key to a value
 {my ($memory, $key, $value, %options) = @\_;                                    # Memory, key, value, options
  $memory->map->{$key} = $value
 }

sub get($$%)                                                                    # Get the value of a key in a lisp memory
 {my ($memory, $key, %options) = @\_;                                            # Memory, key, options
  $memory->map->{$key}
 }

sub unwrap($$%)                                                                 # Unwrap a value returned from memory to retrieve its original value
 {my ($memory, $value, %options) = @\_;                                          # Memory, value, options
  substr($value, 1)
 }

sub join($$$%)                                                                  # Join two values to make a lisp pair
 {my ($memory, $a, $b, %options) = @\_;                                          # Memory, first value, second value, key, options
  $memory->isUserOrLisp($\_) for ($a, $b);
  "$a $b"
 }

sub split($$%)                                                                  # Split a lisp pair into two separate values
 {my ($memory, $value, %options) = @\_;                                          # Memory, lisp pair, options
  split / /, $value
 }

sub getUser($$%)                                                                # Get a value expected to be a user value and return it as such.
 {my ($memory, $key, %options) = @\_;                                            # Memory, key, options
  my $v = $memory->map->{$key};
  defined($v) or confess <<"END" =~ s/\\n(.)/ $1/gsr;
No value for key: $key
END
  $memory->isUser($v) or confess <<"END" =~ s/\\n(.)/ $1/gsr;
The value for key $key is not a user value
END
  substr($v, 1)
 }

sub isUser($$%)                                                                 # Test whether a value is a user value
 {my ($memory, $key, %options) = @\_;                                            # Memory, key, options
  $key =~ m(\\Au\\d+\\Z)
 }

sub isLisp($$%)                                                                 # Test whether a value is a user value
 {my ($memory, $key, %options) = @\_;                                            # Memory, key, options
  $key =~ m(\\Al\\d+\\Z)
 }

sub isUserOrLisp($$%)                                                           # Test whether a value is a user or lisp value
 {my ($memory, $key, %options) = @\_;                                            # Memory, key, options
  return 1 if $memory->isUser($key);
  return 2 if $memory->isLisp($key);
  confess <<"END" =~ s/\\n(.)/ $1/gsr;
Not a user or lisp value: $key
END
 }

goto finish if caller;
clearFolder(q(out), 99);                                                        # Clear the output folder
my $start = time;
eval "use Test::More";
eval "Test::More->builder->output('/dev/null')" if -e q(/home/phil/);
eval {goto latest} if -e q(/home/phil/);

my sub  ok($)        {!$\_\[0\] and confess; &ok( $\_\[0\])}
my sub nok($)        {&ok(!$\_\[0\])}

\# Tests

\#latest:;                                                                       #Tnew #Tput #Tget #TisUser #TgetUser
if (1)
 {my $m = new;
  my $a = $m->wrap(1);
  my $b = $m->wrap(2);
  $m->put($a, $b);
  my $v = $m->get($a);
  is\_deeply($v,            "u2");
  is\_deeply($m->isUser($v),  1);
  is\_deeply($m->getUser($a), 2);
 }

\#latest:;
if (1)                                                                          #TnewLisp
 {my $m = new;
  my $l = $m->newLisp;
  my $a = $m->wrap(1);
  my $b = $m->wrap(2);
  my $p = $m->join($a, $b);
  $m->put($l, $p);
  my $P = $m->get($l);
  my ($A, $B) = $m->split($P);
  is\_deeply($m->unwrap($A), 1);
  is\_deeply($m->unwrap($B), 2);
 }

&done\_testing;
finish: 1
