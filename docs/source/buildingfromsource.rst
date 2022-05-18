Building from Source
====================

Windows
-------

To build the project on Windows, you will have to install `Qt` and the `Vulkan SDK` manually. All other dependencies are handled by `vcpkg`.

Windows versions are compiled with `MSVC 2019 64bit`.

Install Qt for open source using the `official installer <https://www.qt.io/>`_. At the moment we are using version 5.15.2.

Make sure you have an environment variable `QT5_DIR` pointing to the path of your Qt installation. The path might look like this:

.. code-block:: console

    C:\Qt515\5.15.2\msvc2019_64

Get the `Vulkan SDK <https://www.lunarg.com/vulkan-sdk/>`_ and install it. We are currently using version `1.2.198.1`. The environment variable `VULKAN_SDK` has to be set to your Vulkan SDK. For example:

.. code-block:: console

    C:/VulkanSDK/1.2.198.1

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

To download source files and dependencies, you can run:

.. code-block:: console

    git clone https://github.com/ttddee/Cascade
    cd Cascade/scripts
    sh install-deps.sh
    
This script might ask you for the administrator password if a package dependency can be insalled via the system package manager.

Now, open the file `Cascade.pro` with QtCreator.
