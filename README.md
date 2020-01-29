# audioconv
This repository contains a few scripts for converting music to mp3. Notes on what a script does and how to use them are below.

## How to install

Scripts don't care much for where you save them. They have to be in your $PATH, though.

## Dependencies:

* ffmpeg
* lame
* colors.sh (provided)

# Scripts

## TheHobbit.mkv

The script starts in the current directory and recursively searches for the following files:

* .m4a
* .aac
* .flac

and converts them to mp3. It tries to preserve metadata. Converted files end in the same folder as the source files.

If you launch the script with `-d` flag, the source files will be deleted.

## TheHobbit-TheDesolationOfSmaug.mkv

This script is a bit more directed iteration of `TheHobbit.mkv`, written back in 2013 or 2014 (I guess). It converts files inside a specific directory. After converting, it saves two copies: one in a temporary directory and one in the music library. By default, the directories are:

    source directory:          $HOME/0.convert/
    temporary dest. directory: /tmp
    permanent dest. directory: $HOME/Music

You can change these directories by opening the script and editing the following variables:

    convertDIR        source directory
    tmpDIR            temporary directory
    finalDestination  permanent destination directory
    
This script doesn't make sure files in temporary directory eventually actually get deleted.

Unlike the previous script, this script isn't recursive, but it converts from a wider array of formats:

* .flv
* .mkv
* .mp4
* .webm
* .m4a
* .flac

It also deletes the source files, so take care.

Since this iteration of the script was made with the sole purpose of ripping audio from youtube videos, it has some extra features: it adds metadata to the song. It can also cut the song short. Files that get converted by this script should be named in a very specific manner:

    Artist - Title [ - Album ] [ - start.hh.mm.ss ] [ - end.hh.mm.ss ]
      |       |        |               |                     |
      |       |        |            start time and end time of the song (both optional, both require
      |       |        |            this format. hh - hours, mm - minutes, ss - seconds. Must contain
      |       |        |            double digits for all three)
      |       |        |
      |       |    Album (optional, if it's present it gets written to metadata)
      |      Title (for metadata)
     Artist (for metadata)


## ytex

`ytex` is the newest iteration of the above, but simplified. It no longer requires you to specify three separate directions. Instead, the script only needs:
* Your music directory (default: /music)
* Directory for youtube downloads, which is located inside your music directory (default: ytdownloads)

The script doesn't require you to put files that you wish to convert in a specific folder. Instead, it takes the file name as an argument. When the script is done with converting, you're left with two copies of the .mp3 file. One is in the directory for youtube downloads, the other is in the same folder as the original file (assumption is that original file will be saved in /tmp). The original file will be deleted.

Since `ytex` shares most of its code with previous script, most of the features from before should still work.
