termux-apt-repo
---------------
Script to create simple Termux apt repositories.

Usage instructions
------------------
Run as

    python termux-apt-repo <directory-with-debs> <apt-repository-directory>

All the .deb files in the first directory will be published in a newly created APT repository in the second directory (which will be deleted if it exists, so take caution).

Publishing the generated folder
-------------------------------
The published folder can be made available at a publicly accessible `$REPO_URL` using any method:

1. By running termux-apt-repository on a web server directly.
2. Using rsync, `rsync --delete -r <apt-repository-directory> your.host:path/to/folder`.
3. Creating a zip or tar file and unpacking it at a web server.
4. Any other creative way.

Accessing the repository
------------------------
With the created `<apt-repository-directory>` available at `$REPO_URL`, users can access repo by creating a file:

    $PREFIX/etc/apt/sources.list.d

containing the single line:

    deb [trusted=yes] $REPO_URL termux extras

If the `$REPO_URL` is https, users must first install the `apt-transport-https` package which is not preinstalled (likely to come preinstalled in the future).

