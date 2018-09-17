# build-slurm-rpms-in-singularity

If you have a linux machine with [Singularity](https://www.sylabs.io/) and root/sudo access just run this command:

```
sudo singularity build /tmp/slurm_rpms.simg slurm.def 
```

You can re-use the container with:
```
singularity exec -B `pwd` rpmbuild -ta --with mysql --with lua slurm-${SLURM_ANOTHER_VERSION}.tar.bz2
```

You will get the Slurm rpms in `/tmp/rpmbuild`

If you prefer to build the RPMs in a vagrant virtual machine you can check [these slides](https://scicore-unibas-ch.github.io/singularity-slides/#33)
