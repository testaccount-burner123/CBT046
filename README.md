# CBT046
Converted to GitHub via [cbt2git](https://github.com/wizardofzos/cbt2git)

This is still a work in progress. GitHub repos will be deleted and created during this period...

```
//***FILE 046 is the Mass Mutual disk pack maintenance program,     *   FILE 046
//*           "PACKRAT".  Its only function is to examine the       *   FILE 046
//*           VTOC of a particular volume and scratch the           *   FILE 046
//*           datasets specified.  The uncatalog only occurs if     *   FILE 046
//*           the data set is cataloged on the volume currently     *   FILE 046
//*           being examined.  If it is a multi-volume data set     *   FILE 046
//*           it is not scratched or uncataloged.                   *   FILE 046
//*                                                                 *   FILE 046
//*           As originally written, this program has been used     *   FILE 046
//*           on 3330, 3350, 3380, and 3390 devices.  It has been   *   FILE 046
//*           run under MVS/SP 1.3, MVS/XA, and MVS/ESA, and it     *   FILE 046
//*           stopped working on z/OS, but it was still working     *   FILE 046
//*           on OS/390 v2.10.  PACKRAT has now been fixed to       *   FILE 046
//*           work on z/OS in two ways:                             *   FILE 046
//*                                                                 *   FILE 046
//*           z/OS with UCBSCAN - members PACKRATZ and BACKENDZ     *   FILE 046
//*                                                                 *   FILE 046
//*           z/OS with ULUT    - members PACKRATU and BACKENDU     *   FILE 046
//*                                                                 *   FILE 046
//*           Assembly with UCBSCAN - member PACKRAT$               *   FILE 046
//*                                                                 *   FILE 046
//*           Assembly with ULUT    - member PACKRAT#               *   FILE 046
//*                                                                 *   FILE 046
//*           To assemble PACKRAT, you need to assemble two         *   FILE 046
//*           modules, PACKRAT and BACKEND, together in a batch     *   FILE 046
//*           assembly.  For OS/390 and z/OS, use the combination   *   FILE 046
//*           of PACKRATZ and BACKENDZ, or PACKRATU and BACKENDU.   *   FILE 046
//*           The respective assembly jobs are PACKRAT$ and         *   FILE 046
//*           PACKRAT#.                                             *   FILE 046
//*                                                                 *   FILE 046
//*           PACKRAT has now been fixed to work on z/OS in 2       *   FILE 046
//*           different ways.  For all z/OS levels, you can use     *   FILE 046
//*           members PACKRATZ and BACKENDZ.  Member PACKRAT$ is    *   FILE 046
//*           one sample assembly job for the z/OS version of       *   FILE 046
//*           PACKRAT.  (A big "thank you" goes to the person who   *   FILE 046
//*           fixed this program to work under z/OS.  He got a      *   FILE 046
//*           good tool back for us.)                               *   FILE 046
//*                                                                 *   FILE 046
//*           I'm quite sure that PACKRAT does not need to be       *   FILE 046
//*           run APF-authorized.  But it is true that whoever      *   FILE 046
//*           runs PACKRAT has to have TSO OPER authorization       *   FILE 046
//*           (in the PSCB, not in RACF).                           *   FILE 046
//*                                                                 *   FILE 046
//*           - - - - - - - - - - - - - - - - - - - - - - - - - -   *   FILE 046
//*                                                                 *   FILE 046
//*           A different version of PACKRAT, called PACKRATU       *   FILE 046
//*           here, uses a different method of UCB scanning in      *   FILE 046
//*           its BACKEND module, which is called BACKENDU.         *   FILE 046
//*           This method works from ESA 5.2.2 thru at least z/OS   *   FILE 046
//*           2.2.  Below ESA 5.2.2, BACKENDU uses the older        *   FILE 046
//*           methods of UCB scanning.  No APF authorization is     *   FILE 046
//*           needed.  The difference in PACKRATU from the "**Z"    *   FILE 046
//*           versions is that AMODE 31 is needed, and real (not    *   FILE 046
//*           copied) UCB's are obtained by the method.  BACKENDZ   *   FILE 046
//*           obtains copied UCB's, not the real UCB's, although    *   FILE 046
//*           that doesn't seem to make any difference in the       *   FILE 046
//*           processing.                                           *   FILE 046
//*                                                                 *   FILE 046
//*           - - - - - - - - - - - - - - - - - - - - - - - - - -   *   FILE 046
//*                                                                 *   FILE 046
//*           Directions for use:                                   *   FILE 046
//*                                                                 *   FILE 046
//*           PACKRAT is a full screen TSO application to delete    *   FILE 046
//*           or scratch datasets on a disk pack in a convenient    *   FILE 046
//*           manner.  After typing TSO PACKRAT, the prompt         *   FILE 046
//*           screen allows you to enter the VOLSER you wish to     *   FILE 046
//*           examine and the scan date.  A full screen of data     *   FILE 046
//*           sets can be scratched at a time.  Hitting the enter   *   FILE 046
//*           key, pages you forward through the VTOC.  Additional  *   FILE 046
//*           information may be found in the comments of the       *   FILE 046
//*           code itself, and you'll get the hang of it with       *   FILE 046
//*           some practice.  (Recommendation:  Try scratching      *   FILE 046
//*           a few test datasets first.)                           *   FILE 046
//*                                                                 *   FILE 046
//*           As coded currently, PACKRAT will delete SYS1. and     *   FILE 046
//*           other system datasets.  To protect users from doing   *   FILE 046
//*           this, look for SYS1. in the source code and           *   FILE 046
//*           uncomment or change the appropriate lines (z/OS ver). *   FILE 046
//*           This code is in source member BACKENDZ (or BACKENDU). *   FILE 046
//*                                                                 *   FILE 046
//*           This program does not need ISPF, and it can be run    *   FILE 046
//*           in TSO READY mode.                                    *   FILE 046
//*                                                                 *   FILE 046
//*           Members SAMPSCR1 and SAMPSCR2 were included to give   *   FILE 046
//*           you an idea about what the full screens look like.    *   FILE 046
//*                                                                 *   FILE 046
//*           SAMPSCR1 - the introductory screen                    *   FILE 046
//*           SAMPSCR2 - what a screen full of datasets on a        *   FILE 046
//*                      disk pack looks like                       *   FILE 046
//*                                                                 *   FILE 046
//*           email:  sbgolob@cbttape.org                           *   FILE 046
//*                                                                 *   FILE 046
```
