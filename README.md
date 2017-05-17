# flume-taildir-support-file-rename

Flume 1.7.0 implements Taildir Source in [FLUME-2498].


## Description of Taildir Source

This is the proposal of implementing a new tailing source.

This source watches the specified files, and tails them in nearly real-time once appends are detected to these files.

1. This source is reliable and will not miss data even when the tailing files rotate.
2. It periodically writes the last read position of each file in a position file using the JSON format.
3. If Flume is stopped or down for some reason, it can restart tailing from the position written on the existing position file.
4. It can add event headers to each tailing file group.

A attached patch includes a config documentation of this.
This source requires Unix-style file system and Java 1.7 or later.

## Add feature

1. 原taildir不支持文件重命名，本版本支持文件重命名并保持数据不重不漏


## Compilation

The project is maintained by [Maven](http://maven.apache.org/).

## Installation instructions

After your compilation, you should ship the target jar `flume-taildir-source-1.7.0.jar` to the `$FLUME_HOME/flume-ng/lib/`. Then you can edit flume.conf to use the Taildir Source.

Now follows a brief overview of Taildir Source with usage instructions.

## Sources

### Taildir Source

The 'Taildir Source' is extended from original flume 1.7.0's Taildir Source, so you can use other properties just like using Taildir Source.

