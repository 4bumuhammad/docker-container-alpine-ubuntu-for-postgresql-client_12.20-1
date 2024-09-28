### 🟡 References:
-   Ubuntu Wiki | Note Releases [version] <br />
    `https://wiki.ubuntu.com/Releases`

-   Ubuntu image registry [ ubuntu:22.04 ] <br />
    `https://hub.docker.com/layers/library/ubuntu/22.04/images/sha256-965fbcae990b0467ed5657caceaec165018ef44a4d2d46c7cdea80a9dff0d1ea?context=explore`

-   Postgresql 16 or other new release version installation in ubuntu 22.04 <br />
    `https://medium.com/@gembit.soultan/postgresql-16-or-other-new-release-version-installation-in-ubuntu-22-04-d94c9b26cdf2`

-   apt-archive.postgresql.org <br />
    `https://apt-archive.postgresql.org/pub/repos/apt/dists/index.html`

&nbsp;

### 🟡 Implementation steps

1.  Pull image ubuntu 22.04
    <pre>
    ❯ docker pull ubuntu:22.04

        22.04: Pulling from library/ubuntu
        a186900671ab: Pull complete 
        Digest: sha256:58b87898e82351c6cf9cf5b9f3c20257bb9e2dcf33af051e12ce532d7f94e3fe
        Status: Downloaded newer image for ubuntu:22.04
        docker.io/library/ubuntu:22.04

    ❯ docker images

        REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
        ubuntu       22.04     981912c48e9a   2 weeks ago   69.2MB
    </pre>

2.  Run the container with a continuously running process, such as `tail -f /dev/null`. 
    This will keep the container alive even if you exit the shell.
    <pre>
    ❯ docker run -d --name ubuntu-container ubuntu:22.04 tail -f /dev/null

        89bdc4bafd999c719ab5bf39b600d5856676cc0fe517486b8eabd5dc3375ff93
    </pre>

3.  Enter the container that is already running:
    <pre>
    ❯ docker exec -it ubuntu-container /bin/sh

    / #
    </pre>

👍🏼 **[ Done ]** 👍🏼

&nbsp;

### 🟡 Install postgresql-client (manual)

-   Refresh your package repository and install wget gnupg2 lsb-release software-properties-common
    <pre>
        # apt-get install -y wget gnupg2 lsb-release software-properties-common
    </pre>

-   Add postgresql repository
    <pre>
        # sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
    </pre>

-   Import the repository key
    <pre>
        # wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add -
    </pre>

-   Install the PostgreSQL client version ...
    <pre>
        # apt-get update && apt-get install -y postgresql-client-12=12.20-1.pgdg22.04+1
    </pre>

-   Check PostgreSQL client version
    <pre>
        # psql --version

          psql (PostgreSQL) 12.20 (Ubuntu 12.20-1.pgdg22.04+1)
    </pre>

👍🏼 **[ Done ]** 👍🏼

&nbsp;

### 🟡 Install postgresql-client (Bundling - Dockerfile)

-   vim Dockerfile
    <pre>
    FROM ubuntu:22.04

    # Install curl and necessary dependencies
    RUN apt-get update && \
        apt-get install -y wget gnupg2 lsb-release software-properties-common

    # Add PostgreSQL repository
    RUN sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'

    # Import the repository key
    RUN wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add -

    # Install the PostgreSQL client version 12.16
    RUN apt-get update && apt-get install -y postgresql-client-12=12.20-1.pgdg22.04+1

    # Default command to check PostgreSQL client version
    CMD ["psql", "--version"]
    </pre>

👍🏼 **[ Done ]** 👍🏼