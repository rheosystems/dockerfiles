FROM centos:centos7
MAINTAINER Mikkel Christiansen "mikkel@rheosystems.com"
RUN yum -y install bzip2 tar && yum clean all
RUN adduser -m hydra
RUN mkdir -m 0755 /nix && chown hydra /nix && mkdir -m 0755 /var/lib/hydra && chown hydra /var/lib/hydra
USER hydra
WORKDIR /tmp
ENV USER hydra
RUN curl https://nixos.org/nix/install | sh
RUN source ~/.bash_profile && nix-channel --add http://hydra.nixos.org/jobset/hydra/master/channel/latest && nix-channel --update && nix-env -i hydra

# Database configuration
#
# Requires postgresql access with hydra user and database.
# > createuser -S -D -R -P hydra
# > createdb -O hydra hydra
#
ENV HYDRA_DBI dbi:Pg:dbname=hydra;host=localhost;user=hydra;
ENV HYDRA_DATA /var/lib/hydra
ONBUILD RUN source ~/.bash_profile && hydra-init && hydra-create-user alice --password foobar --role admin
ENTRYPOINT ~/.nix-profile/bin/hydra-server
EXPOSE 3000
