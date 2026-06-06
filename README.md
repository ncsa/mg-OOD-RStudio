# Batch Connect - RStudio Server

A Batch Connect app that launches RStudio Server via a container inside of a Slurm job.

## Creating containers

Versioned RStudio containers from the Rocker project seem to work out-of-the-box:
[https://rocker-project.org/images/versioned/rstudio.html](https://rocker-project.org/images/versioned/rstudio.html)

Pull down the container:
```bash
apptainer pull rocker-rstudio-R_4.6.0-RStudio_TBD-20260512-00.sif docker://rocker/rstudio:4.6.0
```

Use `apptainer shell` to investigate the container and find out what version of RStudio it includes. Then update the name to include that, i.e., `<project/org>-<image name>-R_<image/R version>-RStudio_<version>-<build>-YYYYMMDD-##.sif`, where YYYYMMDD is the date the image was downloaded and ## is some optional increment on the image, e.g., `rocker-rstudio-R_4.6.0-RStudio_2026.04.0-526-20260512-00.sif`.

If the image is modified, extended, or built by NCSA, then use 'ncsa' as the project/org.

The images can be given "pretty names" in the app interface, but naming the .sif files in a consistent and comprehensive manner is helpful to maintainers.

## Contributing

1. Work on the MG cluster, developing and testing your changes using the developer sandbox mode
2. If necessary (no dev privs in ncsa/mg-OOD-RStudio), fork the repository
3. Create your feature/topic branch (`git checkout -b username/ticket_id/short_desc`)
4. Add and commit your changes (`git commit -am 'Add some feature'`)
4. Push to the feature/topic branch (`git push origin username/ticket_id/short_desc`)
5. Create a new Pull Request

## Publishing containers on the MG cluster

NCSA staff can share containers in `/usr/local/oodimages/rstudio/` for others to use. Make sure permissions are set to allow everyone to access the .sif file.

In order for the app to show the container as an option it must be added in `form.yml.erb`. Be sure to verify that you can select the container and successfully launch the app.

Then put in a PR as described above. After the PR is approved and the branch is merged to `main`, make sure to add an appropriate version tag to the repo.

Finally, ask an admin to update the Open OnDemand server config to pull in this new release by the tag.

## Acknowledgments and References

[https://github.com/sol-eng/singularity-rstudio](https://github.com/sol-eng/singularity-rstudio)\
[https://discourse.openondemand.org/t/rstudio-when-launched-without-singularity-is-having-strange-troubles-with-authentication/1213/60](https://discourse.openondemand.org/t/rstudio-when-launched-without-singularity-is-having-strange-troubles-with-authentication/1213/60)\
[https://github.com/OSC/bc_osc_rstudio_server](https://github.com/OSC/bc_osc_rstudio_server)

