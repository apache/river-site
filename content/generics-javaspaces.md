Title:     Generics in Java Spaces
license: https://www.apache.org/licenses/LICENSE-2.0

# Generics in Java Spaces 
There are currently several proposals beeing formed. 

## Modification of JavaSpaces interface

i.e.:

    public <T extends Entry> T read(T template, Transaction txn, long timeout)

## Use of generics in Entry implementing classes

