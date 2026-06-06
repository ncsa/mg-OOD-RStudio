# Batch Connect - RStudio Server

A Batch Connect app that launches RStudio Server via a container inside of a Slurm job.

## Creating containers

Versioned RStudio containers from the Rocker project seem to work out-of-the-box:
https://rocker-project.org/images/versioned/rstudio.html

`apptainer pull rocker-rstudio-R_4.6.0-RStudio_TBD-20260512-00.sif docker://rocker/rstudio:4.6.0`

`apptainer shell` the container and find out what version of RStudio it includes. Then update the name to include that, i.e.`rocker-rstudio-R_4.6.0-RStudio_2026.04.0-526-20260512-00.sif`, i.e., `<project>-<image name>-<image version>-R_<version>-RStudio_<version-build>-YYYYMMDD-##.sif` where YYYYMMDD and ## is some optional increment on the image.

## Contributing

1. If necessary (no dev privs in ncsa/mg-OOD-RStudio), fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request
