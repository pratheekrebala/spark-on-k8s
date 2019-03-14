# Upgrading Hadoop Version:

To upgrade the hadoop version, download spark source code from [here](https://spark.apache.org/downloads.html) and build the binaries using the mvn packaged with spark and the following flags:

`build/mvn -Pkubernetes -Phadoop-3.1 -Phadoop-cloud -Dhadoop.version=3.2.0 clean package`

Then, create the executor images using the following command:

`bin/docker-image-tool.sh -r <repo> -t my-tag build`

...and push the images:

`bin/docker-image-tool.sh -r <repo> -t my-tag push`

Then, update the `spark.kubernetes.container.image` configuration in `setSparkEnvVars.sh` for Zeppelin and Jupyter.

Follow the instructions in ../docs/building_images.md to build the Zeppelin and Spark images.