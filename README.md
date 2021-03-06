# Libre- and Open-Office image optimizer

This is an utility that reduces the file-size of images
contained within a Libre-/Open-Office document.

This may heavily cut down on the overall file-size of the document,
and will thus __save memory__ and __speed up working on the document__,
This is most useful if one saves and/or opens the document often,
or in case of little available RAM.

## Building

```bash
mvn package
```

The resulting "binary" will be at
_target/libreofficeimageoptimizer-*-jar-with-dependencies.jar_.

## Usage

### Examples

For shortening our command lines, we will use this in all the examples (bash code):

```bash
alias docOptimizer='java \
	-cp $HOME/src/LibreOfficeImageOptimizer/target/libreofficeimageoptimizer-*-jar-with-dependencies.jar \
	net.hoijui.libreofficeimageoptimizer.Optimizer'
```

Example 1 - Optimization with defaults:

```console
docOptimizer document-with-huge-images.ods
```

Example 2 - Write result to a specific file:

```console
docOptimizer document-with-huge-images.ods optimized-output.ods
```

Example 3 - Specify maximum resolution in either direction (width and height);
the resizing is always preserving the aspect ratio:

```console
docOptimizer -max-size 200 document-with-huge-images.ods
```

## How it works

It simply:

 1. unzips the Libre-/Open-Office document to a temporary directory
 2. resizes the large images, making them smaller
 3. re-zips the archive into an optimized quasi copy
    of the original document

