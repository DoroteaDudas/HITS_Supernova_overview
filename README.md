# Overview

[HITS_Supernova](https://gitlab.com/HITS_Supernova) is a collection of software
projects that were created for the astronomical planetarium and visitor center
[ESO Supernova](https://supernova.eso.org) in Garching b. München, Germany.
Development for these projects was done at the [Heidelberg Institute for
Theoretical Studies
(HITS)](https://www.h-its.org/hits-projects/eso-supernova-planetarium-visitor-center/)
by [Dorotea Dudaš](mailto:dorotea.dudas@h-its.org) and
[Volker Gaibler](mailto:volker.gaibler@h-its.org).

The software resources provided here generally target other developers. While
end users may be able to use much of it, the code has not been tailored, tested
or adapted for general public usage. We hope that this repository may provide a
helpful basis for other developers for similar projects and further work. Most
projects are developed to run on a GNU/Linux operating system.  Please note
that some of the software has been written for a rather specific setup,
however, developers should not find it too hard to adapt to other use cases or
environments.


# General usage

Many of the applications can be used with modern browsers or in other
simple ways.  For stable daily operation in an exhibition setup, however, a
dedicated managment system named *Hilbert* is used and startup is done by a
number of scripts. You won't need that additional layer of complexity for an individual use case. For an automatized museum setup find more details about it below. 
The startup scripts are used for the more complex applications that consist of several programs that need to run hand-in-hand.

Browser-based applications (GitLab repositories use LFS, so downloading an archive omits images):  

<!--
  - [Day / Night / Seasons](https://gitlab.com/HITS_Supernova/0203_daynight)  
  - [Moon phases / Eclipses](https://gitlab.com/HITS_Supernova/0206_moonphaseseclipses)  
  - [Stellar Evolution](https://gitlab.com/HITS_Supernova/0415_stellarevolution)  
  - [Habitable zones](https://gitlab.com/HITS_Supernova/0506_habitablezones)  
  - [Chilean Night Sky](https://gitlab.com/HITS_Supernova/0612_chileannightsky)  
  - [Astronomical Image Processing](https://gitlab.com/HITS_Supernova/0807_astroimage)  
  - [Time Relativity](https://gitlab.com/HITS_Supernova/1206_timerelativity)  
-->

<table align="center">
    <tr>
    <td align="left">GitLab (LFS)</td>
    <td align="left">&nbsp;&nbsp;</td>
    <td align="left">GitHub (no LFS, can download everything in .zip archive)</td>
    </tr>
    <tr>
    <td align="left">&#8226; <a href="https://gitlab.com/HITS_Supernova/0203_daynight">Day / Night / Seasons</a> </td>
    <td align="left">&nbsp;&nbsp;</td>
    <td align="left">&#8226; <a href="https://github.com/DoroteaDudas/HITS_Supernova_0203_daynight">Day / Night / Seasons</a> </td>
    </tr>
    <tr>
    <td align="left">&#8226; <a href="https://gitlab.com/HITS_Supernova/0206_moonphaseseclipses">Moon phases / Eclipses</a> </td>
    <td align="left">&nbsp;&nbsp;</td>
    <td align="left">&#8226; <a href="https://github.com/DoroteaDudas/HITS_Supernova_0206_moonphaseseclipses">Moon phases / Eclipses</a> </td>
    </tr>
    <tr>
    <td align="left">&#8226; <a href="https://gitlab.com/HITS_Supernova/0415_stellarevolution">Stellar Evolution</a> </td>
    <td align="left">&nbsp;&nbsp;</td>
    <td align="left">&#8226; <a href="https://github.com/DoroteaDudas/HITS_Supernova_0415_stellarevolution">Stellar Evolution</a> </td>
    </tr>
    <tr>
    <td align="left">&#8226; <a href="https://gitlab.com/HITS_Supernova/0506_habitablezones">Habitable zones</a> </td>
    <td align="left">&nbsp;&nbsp;</td>
    <td align="left">&#8226; <a href="https://github.com/DoroteaDudas/HITS_Supernova_0506_habitablezones">Habitable zones</a> </td>
    </tr>
    <tr>
    <td align="left">&#8226; <a href="https://gitlab.com/HITS_Supernova/0612_chileannightsky">Chilean Night Sky</a> </td>
    <td align="left">&nbsp;&nbsp;</td>
    <td align="left">&#8226; <a href="https://github.com/DoroteaDudas/HITS_Supernova_0612_chileannightsky">Chilean Night Sky</a> </td>
    </tr>
    <tr>
    <td align="left">&#8226; <a href="https://gitlab.com/HITS_Supernova/0807_astroimage">Astronomical Image Processing</a> </td>
    <td align="left">&nbsp;&nbsp;</td>
    <td align="left">&#8226; <a href="https://github.com/DoroteaDudas/HITS_Supernova_0807_astroimage">Astronomical Image Processing</a> </td>
    </tr>
    <tr>
    <td align="left">&#8226; <a href="https://gitlab.com/HITS_Supernova/1206_timerelativity">Time Relativity</a> </td>
    <td align="left">&nbsp;&nbsp;</td>
    <td align="left">&#8226; <a href="https://github.com/DoroteaDudas/HITS_Supernova_1206_timerelativity">Time Relativity</a> </td>
    </tr>
</table>

Applications that consist of multiple programs or/and use a specific hardware setup (GitLab only):  

  - [Projection on a Half-sphere](https://gitlab.com/HITS_Supernova/0202_halfsphere)  
  - [Paranal / ALMA Webcam](https://gitlab.com/HITS_Supernova/0702_paranalalmawebcam)  
  - [Galaxy Collision](https://gitlab.com/HITS_Supernova/1006_galaxycollisiontable) 
  - [Milky Way Panorama](https://gitlab.com/HITS_Supernova/1007_milkywaypanorama)  


## Hilbert museum management system

Applications within Supernova exhibition are run with the
[Hilbert](https://github.com/hilbert) museum management system by
[Imaginary](https://imaginary.org). Hilbert provides a framework to control and
monitor graphical applications in an exhibition, including a high-level web
interface and a low-level command line interface.  It permits distributing
applications on computers matching a certain hardware profile and running the
applications in a well-defined, reproducible way.

For this, *Hilbert* starts applications (and additional service programs) in
Docker containers so that a restart should result in a reproducible behaviour
of the respective application. The containers are launched off Docker images
that can be built from the files contained in the project repositories.

### Building docker images

Repositories generally contain a `Dockerfile` to build the Docker image and a
`Makefile` that acts as a wrapper to build the images. `Makefile`s are meant to
be used on top of the Docker images provided by the [Hilbert docker
images](https://github.com/hilbert/hilbert-docker-images) repository. This
repository furthermore contains settings and helpers to run graphical
applications within Docker, which can be tricky otherwise because Docker usage
normally targets running non-graphical applications.

Most of our interactive applications are based on `hilbert/kiosk` images whose
main purpose is to run content in a hardened kiosk browser (using `electron`
for this). Hilbert docker images are hierarchically structured (adding more
functionality to higher levels) and we merely add an additional level by basing
our docker images on them. For many applications, docker images are based on
`hits/hitsfat`, which is a local baseimage that is also based on `hilbert/kiosk`
and includes a variety of Ubuntu packages used for several interactive
applications. If you build your own images, you probably want to replace it
with a base image of your own.


### Running application in docker containers

Applications are generally configured by `docker-compose` files that define a
set of docker options that are to be used for the container startup. For more
complex or specific hardware setups, the respective startup script is started
through docker-compose, instead of the default browser. The 
[Hilbert docker images](https://github.com/hilbert/hilbert-docker-images)
repository also contains a `docker-compose.yml` file that we use as basis for
our own files, which are more closely tailored towards the hardware and other
exhibition setup at the ESO Supernova and furthermore may contain local
credentials. The repositories of the respective interactives contain
information about how to start up the application, and this information would
be included in your custom docker-compose file, too - depending on your local
system configuration.

Once the image has been built and start-up commands for the containers are
defined in the respective `docker-compose.yml` files, *Hilbert* will take
care of deploying them to the individual computers, launching, switching and
stopping applications, starting and stopping computers and keeping track of the
status of the exhibition in general.


## Git repositories

**Important:** _The repositories generally use the
[Git LFS](https://git-lfs.github.com) feature to handle large file versioning.
You need to install and activate Git LFS on your computer before cloning the
repository, otherwise you will end up with missing content for these files._

Several of the project repositories rely on git submodules. Sometimes this is
due to the usage of externally maintainted repositories, sometimes re-use for
other ESO Supernova interactives, sometimes simply for historic reasons.
Accordingly, the repositories are best cloned like `git clone --recursive
https://gitlab.com/HITS_Supernova/XXX.git`, which also pulls the submodules
along with the parent repository.

In case you're wondering: there is nothing special about the names having
4 digits prefixed. This is simply an internal station numbering system at ESO
Supernova and we keep it here for consistency.

# Application-specific information

Since most applications have different requirements, history, hardware use or
depend on different software components, the respective repositories contain
the relevant information about startup and chained scripts in their `README.md`
files.


# Licenses

Applications are released under different open-source licenses. Please check 
the respective repositories and their `README.md`.

