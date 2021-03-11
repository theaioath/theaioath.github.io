---
---
# How to batch rename file extensions

[[TOC]]

Today we finally got the approval for the use of patient's COVID images [Yey!]. So before we give access to external collaborators, we need to de-identify the data. I am using the RSNA's Anonymiser tool to do it (Read more about how to use the tool [here](linktootherarticle). This is what I learned in the process.

## Batch rename file extensions on Linux

Open a terminal in the directory where your files sit, and run this bash command

```for f in *; do mv $f `basename $f `.dcm; done;` ```

What the command does is keeping the basename for every file in this folder and adds the required extension to it. This is done regardless of the file's original extension, or if it even has one at all.
So if you need to add a different extension just replace `.dcm` with the one you need.

## Why I needed this  

For some reason, the extracted data had no extension name when I opened the image folder. But AFAIK, Anonymiser looks for specific extension names. You can configure the type of extensions, but you have to have one. There was no way I was going to manually rename 10K files, and because of COVID slowing everyone's work at the hospital, I couldn't ask for a new extraction again.

## What I still haven't figured out

### How to do this on windows

As I was working on a windows machine, I initially tried to rename the files in the command prompt using the rename command `ren *. *.dcm` but it kept failing. The command works on different files to change the extension from say `.txt` to `.md` but in my case there was no extension at all so the `*.` was not valid. For the sake of time I decided to switch to the linux VM and use bash instead, but I will get back to update this at some point.  
