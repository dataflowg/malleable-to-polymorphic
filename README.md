# Malleable VI to Polymorphic VI Converter
A small utility for creating sets of polymorphic VIs from malleable VIs, including nested malleable VIs. Useful for saving libraries to pre LabVIEW 2017 versions, or preparing code to convert to LabVIEW NXG.

The utility creates a duplicate set of VIs, and recursively generates polymorphic VIs for each malleable VI instance on a block diagram. Type Specialization structures are automatically removed, as are the Assert class of malleable VIs as they are no longer needed.

## Usage
1. All malleable VIs should be saved in a single library. At the same level as the lvlib file on disk, create a folder called `Polymorphic Templates`. **Do not add this folder to the lvlib.**
2. Inside this folder, create a new VI. This VI will be used to define the polymorphic names and types to generate from one malleable VI.
3. Open the new VI's block diagram and drop the malleable VI from the library. Wire it up to with the types for that malleable VI instance.
4. Create a block diagram comment with the name that should appear in the polymorphic selector, and attach it to the malleable VI.
5. Repeat the above process for as many malleable VI instances as required. The resulting block diagram will be a collection of the same malleable VI, each with unique wired types and attached comments.
6. Create and populate additional VIs in the `Polymorphic Templates` folder for each top level malleable VI as required.
7. Now run the conversion utility and select the library to be converted, and the destination folder and name for the polymorphic version of the library. It may take some time for the conversion to run.

There's currently no feedback on the conversion status, but all going well you should see the polymorphic VIs slowly appear in `<Destination Directory>\Polymorphic VIs`.

## Example
You can run this tool on the [G-Audio](https://github.com/dataflowg/g-audio) library to see it in action, and the resulting polymorphic output.