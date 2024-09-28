### 🟡 Implementation steps

1.  Pull image Alpine 3.18
    <pre>
    ❯ docker pull alpine:3.18

        3.18: Pulling from library/alpine
        720f3032cd11: Pull complete 
        Digest: sha256:3ddf7bf1d408188f9849efbf4f902720ae08f5131bb39013518b918aa056d0de
        Status: Downloaded newer image for alpine:3.18
        docker.io/library/alpine:3.18

    ❯ docker images

        REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
        alpine       3.18      3e834921e367   2 weeks ago   7.67MB
    </pre>

2.  Run the container with a continuously running process, such as `tail -f /dev/null`. 
    This will keep the container alive even if you exit the shell.
    <pre>
    ❯ docker run -d --name alpine-container alpine:3.18 tail -f /dev/null

        bdc54da33a97b8df5a7c9b44f335fb4d87d010c7f5589924fc3c212454d4fd16
    </pre>

3.  Enter the container that is already running:
    <pre>
    ❯ docker exec -it alpine-container /bin/sh

    / #
    </pre>

👍🏼 **[ Done ]** 👍🏼

&nbsp;

**References:**
-   List: Release Notes Postgresql <br />
    `https://www.postgresql.org/docs/release/`

### 🟡 Install postgresql-client
<pre>
/# apk add --no-cache postgresql-client

    . . .
    * Setting postgresql15 as the default version
    OK: 13 MiB in 23 packages

/ # psql --version
psql (PostgreSQL) 15.8
</pre>

👍🏼 **[ Done ]** 👍🏼