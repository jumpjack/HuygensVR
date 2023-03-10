# HuygensVR
Building a VR360 video of Huygens probe landing on Titan


How to turn this:

![image](https://user-images.githubusercontent.com/1620953/214508603-b539e178-d033-45e8-85cc-63eee6f3d0df.png)


...into this...

![image](https://user-images.githubusercontent.com/1620953/214508571-1608d290-8191-4bbd-aa4d-99cd73fb7ed3.png)

... and eventually into an equirectangular projection to be viewd in VR viewers?

Video: https://sci.esa.int/web/cassini-huygens/-/39218-huygens-descent-to-titan-surface

# Panoramas/mosaics:

## Flat

There are [12 mosaics available](https://archives.esac.esa.int/psa/ftp/CASSINI-HUYGENS/DISR/HP-SSA-DISR-2-3-EDR-RDR-V1.3/EXTRAS/MOSAICS/MOSIACS_PNG/); the file names matche with ground resolution, e.g. 4.PNG has a 4m/pixel resolution:

- 1.PNG
- 2.PNG
- 3.PNG
- 4.PNG
- 5.PNG
- 10.PNG
- 15.PNG
- 20.PNG
- 30.PNG - referred to as "18.75 × 24.0 km" in [link](https://www.mps.mpg.de/phd/theses/investigating-the-surface-of-titan-with-the-descent-imager-spectral-radiometer-onboard-huygens.pdf) (fig 1.11, p.23)
- 40.PNG - referred to as "62.5 × 80.0 km" in above link (fig. 1.10, p.22)
- 50.PNG
- 60.PNG

The projection used for these mosaics is currently unknown.

## "Posters"

There are also some "posters" available in this folder; poster "C" contains 6 stereographic fisheye images taken from different altitudes: 150 km, 20km, 6km, 2km, 0.6km, 0.2km; FOV unknown (full size image [here](https://archives.esac.esa.int/psa/ftp/CASSINI-HUYGENS/DISR/HP-SSA-DISR-2-3-EDR-RDR-V1.3/EXTRAS/POSTERS/POSTER_C.JPG)):

![image](https://user-images.githubusercontent.com/1620953/214520292-b3a77897-5aff-4b14-a3fd-28b921fffc85.png)

![immagine](https://user-images.githubusercontent.com/1620953/214538248-4a813780-cdb0-400f-8097-2f3da2605655.png)

Descriptions:

Poster A - View's from the probe, in the 4 Cardinal
Directions (N,S,E,W) at 5 different altitudes above Titan's
surface.

Poster B - Mercator Projection of the view from the Huygens
probe at 4 different altitudes.

Poster C - Nadir, Stereographic (fish-eye) view of Titan's
surface from 6 different altitudes.  Shows the haze layer at
20-21 Km.

Poster D - Mercator projection of Huygens probe view from 10
Km Altitude.

Poster E - Distorted fish-eye projection (in nadir
direction) of the DISR images when the Huygens Probe was 5
Km above Titan's surface.

Poster F - Composite view of DISR's images taken while the
Huygens Probe was setting on Titan's surface, juxtaposed
with a similarly scaled picture taken on the Moon's surface.
Objects near the center of the picture are roughly the size
of a man's foot while objects at the horizon are a fraction
of a man's height.

Poster G - When printed on letter sized paper this poster
show's the size of the 'rocks' on Titan's surface in their
true size.

### Converting posters

Cropping out the raw fisheye from poster_E:

    ffmpeg    -i POSTER_E.jpg    -vf "crop=2800:2800:50:200"    -y  POSTER_E-mod(5km_fisheye)2.jpg

Cropping out the raw fisheye images from poster_C:   

- Poster C1:  ffmpeg    -i POSTER_C.jpg    -vf "crop=1301:1121:126:236"    -y  POSTER_C_x.jpg
- Poster C2:  ffmpeg    -i POSTER_C.jpg    -vf "crop=1301:1121:1453:236"    -y  POSTER_C_x.jpg
- Poster C3:  ffmpeg    -i POSTER_C.jpg    -vf "crop=1301:1121:126:1386"    -y  POSTER_C_x.jpg
- Poster C4:  ffmpeg    -i POSTER_C.jpg    -vf "crop=1301:1121:1453:1386"    -y  POSTER_C_x.jpg
- Poster C5:  ffmpeg    -i POSTER_C.jpg    -vf "crop=1301:1121:126:2537"    -y  POSTER_C_x.jpg
- Poster C6:  ffmpeg    -i POSTER_C.jpg    -vf "crop=1301:1121:1453:2537"    -y  POSTER_C_x.jpg


# Huygens cameras

Panoramas were created from images taken from 3 cameras: HRI, LRI, SLI; their FOVs are represented in picture below:

![image](https://user-images.githubusercontent.com/1620953/214509962-9c37b7c6-9592-4bfb-a257-8d8c25cbcdc0.png)

Numerically:

![image](https://user-images.githubusercontent.com/1620953/214510628-50ac2deb-0833-49fd-ad6d-e5bc37b4471f.png)

![image](https://user-images.githubusercontent.com/1620953/214511341-420db227-4fec-48b8-90f7-1706f7bd570d.png)

There is also a visual imager pointed to the sky, the Solar Aureole imager (SA):

![image](https://user-images.githubusercontent.com/1620953/214511724-282fddda-5f2c-4c33-b8e4-58f4e5dd1036.png)

Details about the camera optics:

![image](https://user-images.githubusercontent.com/1620953/214523232-13005e4c-4b84-4fc2-9243-61cce64cb048.png)


## Some data

- Titan radius: 2575 km
- Descent images avalable: 236 before touchdown

# Data folders
- [Main](https://archives.esac.esa.int/psa/ftp/CASSINI-HUYGENS/DISR/)
- [Full mosaics](https://archives.esac.esa.int/psa/ftp/CASSINI-HUYGENS/DISR/HP-SSA-DISR-2-3-EDR-RDR-V1.3/EXTRAS/MOSAICS/MOSIACS_PNG/)

# Reference documents

- [THE DESCENT IMAGER/SPECTRAL RADIOMETER (DISR) EXPERIMENT ON THE HUYGENS ENTRY PROBE OF TITAN (M. G. TOMASKO)](https://archives.esac.esa.int/psa/ftp/CASSINI-HUYGENS/DISR/HP-SSA-DISR-2-3-EDR-RDR-V1.3/DOCUMENT/DISR_SUPPORTING_DOCUMENTS/SPACE_SCIENCE_REVIEW/SSR.PDF)  ([local mirror](https://github.com/jumpjack/HuygensVR/blob/main/THE%20DESCENT%20IMAGER-SPECTRAL%20RADIOMETER%20(DISR)%20EXPERIMENT%20ON%20THE%20HUYGENS%20ENTRY%20PROBE%20OF%20TITAN.PDF))
- [Rain, winds and haze during the Huygens probe’s descent to Titan’s surface (M. G. Tomasko)](https://archives.esac.esa.int/psa/ftp/CASSINI-HUYGENS/DISR/HP-SSA-DISR-2-3-EDR-RDR-V1.3/DOCUMENT/DISR_SUPPORTING_DOCUMENTS/SPACE_SCIENCE_REVIEW/SSR.PDF) ([External mirror](https://www.academia.edu/en/18515156/Rain_winds_and_haze_during_the_Huygens_probes_descent_to_Titans_surface)) ([local mirror](https://github.com/jumpjack/HuygensVR/blob/main/Rain_winds_and_haze_during_the_Huygens_p.pdf))
- [NEW DIGITAL TERRAIN MODEL OF THE HUYGENS LANDING SITE](https://www.cosmos.esa.int/documents/772136/977578/PUG-IPGP-Titan.pdf/888eec57-cd40-44dc-58b5-26cd8dd3587b?t=1620900122478)
- Data Archive Users’ Guide for the Descent Imager and Spectral Radiometer (DISR) on the Huygens Probe (contains many details on data folder contents)
    - Only document: [link](https://pds-atmospheres.nmsu.edu/data_and_services/atmospheres_data/Huygens/DISR_DATA_USERS_GUIDE_2.PDF) (5.6 MB, 157 pages)
    - Only appendixes (tables and charts): [link](https://pds-atmospheres.nmsu.edu/data_and_services/atmospheres_data/Huygens/APPENDIX.pdf)  (29 MB, 474 pages)
    - Full document with appendixes: [link](https://pds-atmospheres.nmsu.edu/data_and_services/atmospheres_data/Huygens/DISR_Guide_Complete_r.pdf)  (24 MB, 617 pages)
- [Investigating the Surface of Titan with the Descent Imager/Spectral Radiometer onboard Huygens](https://www.mps.mpg.de/phd/theses/investigating-the-surface-of-titan-with-the-descent-imager-spectral-radiometer-onboard-huygens.pdf)

# Software
- Panorama viewer javascript library: https://photo-sphere-viewer.js.org/  ([source](https://github.com/mistic100/Photo-Sphere-Viewer))
- Images stitcher:
     - [Enblend](https://enblend.sourceforge.net/index.htm)
     - [Multiblend](https://horman.net/multiblend/)

# Links

- ftp://psa.esac.esa.int/pub/mirror/CASSINI-HUYGENS/DISR/
- https://archives.esac.esa.int/psa/ftp/CASSINI-HUYGENS/DISR/HP-SSA-DISR-2-3-EDR-RDR-V1
- http://archives.esac.esa.int/psa/ftp/CASSINI-HUYGENS/DISR/HP-SSA-DISR-2-3-EDR-RDR-V1.3/
- https://pds-atmospheres.nmsu.edu/data_and_services/atmospheres_data/Huygens/
- https://atmos.nmsu.edu/PDS/data/hpdisr_0001/
- https://atmos.nmsu.edu/PDS/data/hpdisr_0001V1/
