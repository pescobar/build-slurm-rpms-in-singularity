Bootstrap: docker
From: centos:7

%post

   # check the versions in https://www.schedmd.com/downloads.php
   export SLURM_VERSION="18.08.0"

   # install the dependencies
   yum -y install epel-release
   yum -y install \
   bzip2 \
   freeipmi \
   freeipmi-devel \
   gcc \
   gcc-c++ \
   glibc-static \
   gtk2-devel \
   hdf5-devel \
   hdf5-static \
   hwloc \
   hwloc-devel \
   infiniband-diags \
   infiniband-diags-devel \
   infiniband-diags-devel-static \
   libcurl-devel \
   libibumad \
   libibumad-devel \
   libibumad-static \
   lua-devel \
   man2html-core \
   mariadb-devel \
   munge-devel \
   ncurses-devel \
   numactl \
   numactl-devel \
   openssl-devel \
   pam-devel \
   perl-ExtUtils-MakeMaker \
   readline-devel \
   redhat-lsb \
   redhat-rpm-config \
   rpm-build \
   rrdtool \
   rrdtool-devel \
   rrdtool-devel \
   rsync \
   wget
   yum clean all

   # download the source code and build the rpms
   cd /usr/local/src/
   wget https://download.schedmd.com/slurm/slurm-${SLURM_VERSION}.tar.bz2
   rpmbuild -ta --with mysql --with lua slurm*.tar.bz2

   # copy the created rpms to /tmp/rpmbuild
   [ -d /tmp/rpmbuild ] || mkdir /tmp/rpmbuild
   rsync -av --progress /root/rpmbuild/RPMS /tmp/rpmbuild/
   rsync -av --progress /root/rpmbuild/SRPMS /tmp/rpmbuild/
   echo 'Slurm RPMs are in /tmp/rpmbuild'

