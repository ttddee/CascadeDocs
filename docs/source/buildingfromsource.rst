Building from Source
====================

Windows
-------

To build the project on Windows, you will have to install `Qt` and the `Vulkan SDK` manually. The other dependencies are handled by `vcpkg`.

Windows versions are compiled with `MSVC 2019 64bit`.

Install Qt for open source using the `official installer <https://www.qt.io/>`_. At the moment we are using version 5.15.0, installed into C:\Qt515.

Get the `Vulkan SDK <https://www.lunarg.com/vulkan-sdk/>`_ and install it into `C:\VulkanSDK`. We are currently using version `1.2.198.1`. If you want to use a newer version, you will have to change this line in `Cascade.pro` to the correct version number:

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

It will take a while to compile but upon completion you should be able to open the project in Qt Creator, configure your compiler and build.

Ubuntu (21.10)
--------------

We are going to download the repository into the home directory.

.. code-block:: console
    cd ~

    git clone https://github.com/ttddee/Cascade

Install dependencies:

.. code-block:: console
    apt -y install libopenimageio-dev libgtest-dev libtbb-dev qtcreator build-essential qtbase5-dev qt5-qmake qtbase5-dev-tools libopenexr-dev cmake libglew-dev freeglut3-dev

We have to build OpenColorIO ourselves, because the version supplied by Ubuntu is too old. Run the following commands:

.. code-block:: console
    mkdir external

    cd external

    git clone https://github.com/AcademySoftwareFoundation/OpenColorIO

    cd OpenColorIO

    git checkout tags/v2.1.0

    mkdir build

    mkdir install

    cd build

    cmake -DCMAKE_INSTALL_PREFIX=~/Cascade/external/OpenColorIO/install ~/Cascade/external/OpenColorIO -DOCIO_BUILD_PYTHON=OFF -DOCIO_BUILD_APPS=OFF -DOCIO_BUILD_TESTS=OFF -DOCIO_BUILD_GPU_TESTS=OFF -DCMAKE_BUILD_TYPE=Debug -D CMAKE_CXX_COMPILER=/usr/bin/gcc

    make -j8

    make install

We will also download glslang binaries:

.. code-block:: console
    cd ../..

    mkdir glslang

    cd glslang

    wget https://github.com/KhronosGroup/glslang/releases/download/master-tot/glslang-master-linux-Debug.zip

    unzip glslang-master-linux-Debug.zip

    rm glslang-master-linux-Debug.zip

Now, open the file `Cascade.pro` with QtCreator and configure it to use Qt5, GCC as compiler and GDB as debugger.