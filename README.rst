Rbin
=====

``Rbin`` and ``Rbinlist`` are shell scripts to easily call command-line executables installed in the ``bin`` and/or ``exec`` directories of R packages (which are not usually added to a user's PATH when the package is installed because doing so is against CRAN policy).  

.. image:: http://www.repostatus.org/badges/latest/active.svg
   :alt: Project Status: Active – The project has reached a stable, usable state and is being actively developed.
   :target: http://www.repostatus.org/#active

Installation
------------

To use ``Rbin`` and ``Rbinlist`` download them, mark them executable, and add them to your `PATH`:: 
    
    $ curl -O https://github.com/trevorld/Rbin/raw/master/Rbin
    $ curl -O https://github.com/trevorld/Rbin/raw/master/Rbinlist
    $ chmod u+x Rbin Rbinlist
    $ cp Rbin* $HOME/bin/

Usage
-----

Example usage using the example executables from the `optparse <https://github.com/trevorld/optparse>`_ package::

    $ Rbinlist optparse
    display_file.R
    example.R
    $ Rbin optparse example.R --help
    Usage: /usr/local/lib/R/site-library/optparse/exec/example.R [options]


    Options:
            -v, --verbose
                    Print extra output [default]

            -q, --quietly
                    Print little output

            -c NUMBER, --count=NUMBER
                    Number of random normals to generate [default 5]

            --generator=GENERATOR
                    Function to generate random deviates [default "rnorm"]

            --mean=MEAN
                    Mean if generator == "rnorm" [default 0]

            --sd=STANDARD DEVIATION
                    Standard deviation if generator == "rnorm" [default 1]

            -h, --help
                    Show this help message and exit


    $ Rbin optparse example.R -q --count=11 --generator=runif
    0.373417189577594
    0.657838996266946
    0.802908265497535
    0.25030386634171
    0.305545562878251
    0.443784795468673
    0.238544765627012
    0.772253244416788
    0.541883816709742
    0.0226398415397853
    0.957296556560323

Aliases
-------

You can also use ``Rbin`` to define a bash alias in a user's ``.bashrc`` file so that it appears that a program is on the user's path::

    alias example.R="Rbin optparse example.R"
    alias knit="Rbin knitr knit"
