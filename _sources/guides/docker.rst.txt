Docker
======

Ble2WLED can be run inside a Docker container. This is especially useful for running the application on systems where Python is not installed or where you want to isolate the application from the host system.

Building the Docker Image
---------------------------

To build the Docker image, run the following command in the root directory of the project:

.. code-block:: bash

    docker build -t ble2wled .

This will create a Docker image named ``ble2wled``.

Run with overridden environment variables
-----------------------------------------

You can run the Docker container with environment variables overridden using the ``-e`` flag. For example:

.. code-block:: bash

    docker run -d \
        --name ble2wled \
        --network host \
        -e WLED_HOST=wled.local \
        -e MQTT_BROKER=192.168.1.10 \
        -e MQTT_PASSWORD=supersecret \
        ble2wled

This command runs the ``ble2wled`` container in detached mode, using the host network, and sets the specified environment variables.

🔎 Note: ``--network host`` is often required for:

- mDNS (wled.local)
- UDP output
- local MQTT brokers