gfpoken is a C program and the artwork and graphics files were 32x32 pixels.  I adjusted the various parts of the program and those files as needed to work in 64x64 pixels.

Any bugs introduced by these changes are my fault and of course not intentional.  Send me a note if you find something (Flowerbug <flowerbug@anthive.com>) along with a suggested fix.

Below is an outline of the steps I took to get all of this done and how to apply to your own local source code copy.

  1. Edited art/mirror.xcf in gimp
    - one of the images was missing a pixel so I added it (also to mask)
    - scaled images from 32x32 pixels to 64x64 pixels

  2. Changed tile size in art/mktiles to 64
    - I don't think it is actually used, but just in case...

  3. Fixed art/mkmarbles
    - Use of HOME environment variable just didn't seem right to me
      (what if mktemp fails? it's not tested) so I changed that name
      to use GFP_TMP_HOME instead

  4. Used blender to create 64x64 pixel version of marbles

  5. Used convert to resize the remaining png pictures

  6. Changes to gfp.h to reflect larger sizes
     - Not sure what frameskip does, but it needed to change too

  7. main.c small fix
     - Was printing out dragging information when the program is
       started from the shell


How to apply this to your own local copy of the source code:

  1. Get a copy of the gfpoken source code (and any build 
     dependencies also needed).  I also keep a local backup
     copy of the original just in case I need to compare...

  2. Get a copy of the files I've changed and copy them over 
     your local versions.

  3. ./configure

  4. make clean && make && make install

If any issues show up from this needing different directories and/or permissions these will have to be adjusted based upon your local configuration desires/needs.

  At the moment none of these changes are complicated enough that I would copyright any of them.
