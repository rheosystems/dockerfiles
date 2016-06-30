FROM postgres:9.5
MAINTAINER Mikkel Christiansen "mikkel@rheosystems.com"
RUN apt-get update && apt-get install -y pgbadger && apt-get clean

# Append logging parameters to postgres.conf
COPY logging.conf /tmp/
RUN cat /tmp/logging.conf >> /var/lib/postgresql/data/postgresql.conf
