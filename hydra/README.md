# Hydra

## About

Hydra is a Nix-based continuous build system, released under the terms
of the GNU GPLv3 or (at your option) any later version. It
continuously checks out sources of software projects from version
management systems to build, test and release them. The build tasks
are described using Nix expressions. This allows a Hydra build task to
specify all the dependencies needed to build or test a project. It
supports a number of operating systems, such as various GNU/Linux
flavours, Mac OS X, and Windows.


## Docker Setup

Make sure the container has access to a postgresql instance.

`$ docker run --name hydra-db -e POSTGRES_PASSWORD=hydra -e POSTGRES_USER=hydra -p 5432:5432 -d postgres:9.4`


Start the hydra container:

`$ docker run --name hydra-app hydra -p 3000:3000 -d rheosystems/hydra:latest`


Run the init script and create a user from inside the hydra app container:

`$ docker exec -it hydra-app /bin/bash`  
`$ /home/hydra/.nix-profile/bin/hydra-init`  
`$ /home/hydra/.nix-profile/bin/hydra-create-user alice --full-name 'Alice Q. User' --email-address 'alice@example.org' --password foobar --role admin`

## References

- https://nixos.org/hydra/
