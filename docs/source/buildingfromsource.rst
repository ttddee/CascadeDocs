Building from Source
====================

Windows
-------

To build the project on Windows, you will have to install `Qt` and the `Vulkan SDK` manually. All other dependencies are handled by `vcpkg`.

Windows versions are compiled with `MSVC 2019 64bit`.

Install Qt for open source using the `official installer <https://www.qt.io/>`_. At the moment we are using version 5.15.0, installed into C:\Qt515.

Get the `Vulkan SDK <https://www.lunarg.com/vulkan-sdk/>`_ and install it into `C:\\VulkanSDK`. We are currently using version `1.2.198.1`. If you want to use a newer version, you will have to change this line in `Cascade.pro` to the correct version number:

.. code-block:: console

    INCLUDEPATH += C:/VulkanSDK/1.2.198.1/include

It's easiest to use Qt Creator as IDE, but feel free to use Visual Studio if you want.

Open a command prompt and clone the Cascade repository:

.. code-block:: console

    git clone https://github.com/ttddee/Cascade

Enter the project directory and install vcpkg:

.. code-block:: console

    cd Cascade
    git clone https://github.com/microsoft/vcpkg
    .\vcpkg\bootstrap-vcpkg.bat

Now you can install all other dependencies using the command below:

.. code-block:: console

    .\vcpkg\vcpkg --feature-flags="versions" --triplet=x64-windows  install

This will take a while to compile but upon completion you should be able to open the project in Qt Creator, configure your environment and build.

GNU/Linux
--------------
You need to download the repository.

.. code-block:: console

    git clone https://github.com/ttddee/Cascade

To install dependencies run script:

.. code-block:: console

    ./scripts/install-deps.sh

This script might ask you for the administrator password if a package dependency can be insalled via the system package manager.

To download source files and dependencies, you can run:

.. code-block:: console

    git clone https://github.com/ttddee/Cascade
    cd Cascade/scripts
    sh install-deps.sh
    cd ..

Now, open the file `Cascade.pro` with QtCreator.
