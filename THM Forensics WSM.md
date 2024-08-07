This is a semi-writeup for TryHackMe\'s Digital Forensics Case B4DM755.
I don't list every question's answers here, acting as a tutorial, but
rather show what I worked on. I gain practical experience using FTK
Imager to create and analyze a disk image for artifacts that would be
presented as evidence. A Write-Blocker would be used to mount the drive
in order to prevent any accidental tampering that would ruin the
evidence.

### Taking an Image and Checking for Encryption

A leftover flash drive was found at the scene of a crime. It's mounted
to a write-blocker and is sent to the Forensics Lab. The drive is
checked for encryption, then an image is taken to create a copy.

![](output\THM Forensics WSM/media/image3.png){width="6.677083333333333in"
height="4.614583333333333in"}

![](output\THM Forensics WSM/media/image1.png){width="8.59375in"
height="6.166666666666667in"}

![](output\THM Forensics WSM/media/image4.png){width="6.75in"
height="4.90625in"}

The image's integrity is verified by checking the hashes of the physical
drive and the disk image. Once verified, the physical flash drive is no
longer needed and is sent back.

![](output\THM Forensics WSM/media/image8.png){width="6.760416666666667in"
height="4.791666666666667in"}

![](output\THM Forensics WSM/media/image12.png){width="7.770833333333333in"
height="6.072916666666667in"}

### Analyzing the Image for Evidence

Now I can look through the contents of the drive and see if there is
anything suspicious or noteworthy

![](output\THM Forensics WSM/media/image10.png){width="10.0in"
height="5.444444444444445in"}

I can see corrupted files with 0 kb size and files that were deleted,
labeled with a red X on the icon. I can also click on files to view the
header and see if it matches what the file type is listed as. I can also
export all the files to my desktop to preserve it, with deleted and
corrupted files included but nonfunctional of course.

Some deleted files have a file size to them, hideout.pdf warehouse.pdf
and operations.xlsx, however I can't open them up as I get prompted with
an error. I also notice that "Exif" is in the header of these files, so
I will use exiftool to verify the file type and see if it was obfuscated
by the suspect to hide evidence.

![](output\THM Forensics WSM/media/image9.png){width="6.078297244094488in"
height="4.609375546806649in"}

![](output\THM Forensics WSM/media/image11.png){width="8.1875in"
height="2.1458333333333335in"}

It looks like hideout.pdf and warehouse.pdf are images and
operations.xlsx is a zip file. I can see additional details regarding
the images, including timestamps and even the model of the camera/phone
used to take it.

![](output\THM Forensics WSM/media/image13.png){width="9.0625in"
height="3.84375in"}

![](output\THM Forensics WSM/media/image6.png){width="9.166666666666666in"
height="3.3020833333333335in"}

Changing the file extensions of the images to .jpg and opening them up
displays pictures, of course, of the warehouse and hideout. Changing the
file extension of the .xlsx to .zip shows additional files within it.

![](output\THM Forensics WSM/media/image5.png){width="4.75in"
height="2.3229166666666665in"}

I can find the password to pandorasbox.zip within the notes.txt file
(along with details of transactions involving hundreds of millions of
dollars, along with geo coordinates) and then I extract all of the files
out of the .zip. From there, I can open the unsuspecting file titled
"DONOTOPEN" and find a hidden flag.

![](output\THM Forensics WSM/media/image7.png){width="8.130208880139982in"
height="3.0403587051618546in"}

I can also find other files related to trading algorithms with important
information

![](output\THM Forensics WSM/media/image2.png){width="7.869792213473316in"
height="4.762863079615048in"}

All the evidence I listed here, along with other existing documents I
haven't mentioned containing other suspects' names, can be used to
prosecute in a court of law.
