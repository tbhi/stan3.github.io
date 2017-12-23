---
layout: post
---
Had a few hundred old diving photos in raw format that I wanted white balance correct and convert to jpeg.  
Installed the raw plugin in gimp with 

    $ sudo apt install gimp-dcraw

I noticed that white balance correction seems to be applied on loading the raw files automatically.
Although not perfect it seemed ok for my needs.  So I decided to try and automate the process in
python-fu.

Mostly it's a simple load and save but I needed to use exiftool to copy over the metadata.

$ sudo apt install libimage-exiftool-perl

Then copying this function into the gimp python console:

    def convert(fname):
        img = pdb.gimp_file_load(fname, fname)
        layer = pdb.gimp_image_merge_visible_layers(img, 1)
        out_fname = fname + '.jpg'
        pdb.gimp_file_save(img, layer, out_fname, out_fname)
        subprocess.check_call(['exiftool', '-TagsFromFile', fname, out_fname])

and then calling the function from the console for the relevant files does the job nicely.
