# Random Number Generation #
SmileBASIC has a set of built-in random number generation functions.
Number generation has a number of applications in computer science,
so these features can be a useful tool if used properly.

## Generating Numbers ##
To generate random numbers, you must call the generator (or RNG)
with one of the following instructions.
### RND ###
The [`RND` instruction](/instruction/rnd.md) returns a random integer
that is greater than or equal to 0, and less than a specified
upper bound. For example, the function `RND(5)` returns a
random integer between 0 and 4.
### RNDF ###
The [`RNDF` instruction](/instruction/rndf.md) returns a random number
greater than or equal to 0 and less than 1.

## Using Multiple Generators ##
SmileBASIC has 8 separate RNGs, whose IDs are 0 through 7.
They all have separate seed states, so they can all produce
unique sequences of numbers independent of one another.

`RND` and `RNDF` each accept an optional first argument,
selecting the generator to use when generating the next number.
`RND(0,10)` will return a number 0 through 9 generated by RNG 0.
`RNDF(4)` will return a random fraction generated by RNG 4. If
a generator ID is not specified, generator 0 is used.

## Seeding the Generator ##
The [`RANDOMIZE` instruction](/instruction/randomize.md) can initialize
the seed of a chosen generator. For example, `RANDOMIZE 2` initializes
RNG 2 with a random seed. In addition, an optional seed value can be specified.
`RANDOMIZE 2,1234` sets the seed of RNG 2 to the number 1234. By setting a
specific seed, the same sequence of numbers can be obtained by a generator every time.

## Example Code ##
```
FOR I%=1 TO 20
 PRINT RND(10)
NEXT
```
Prints 20 random integers, between 0 and 9.

```
RANDOMIZE 0,12345
PRINT RNDF()
```
Will always print 0.801218124.

## Technical Notes ##
When using the same generator ID, `RND` and `RNDF` are *not* independent of
one another. They both affect the same seed state, so they will affect
eachother's sequence.

## See Also ##
- [`RND` Instruction](/instruction/rnd.md)
- [`RNDF` Instruction](/instruction/rndf.md)
- [`RANDOMIZE` Instruction](/instruction/randomize.md)
