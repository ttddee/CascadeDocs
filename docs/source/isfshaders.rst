Using ISF shaders
=================

What is ISF?
------------

From the `ISF Spec <https://github.com/mrRay/ISF_Spec>`_:

    ISF stands for "Interactive Shader Format", and is a file format that describes a GLSL fragment shader, as well as how to execute and interact with it. The goal of this file format is to provide a simple and minimal interface for image filters and generative video sources that allows them to be interacted with and reused in a generic and modular fashion. ISF is nothing more than a [slightly modified] GLSL fragment shader with a JSON blob at the beginning that describes how to interact with the shader (how many inputs/uniform variables it has, what their names are, what kind of inputs/variables they are, that sort of thing). ISF isn't some crazy new groundbreaking technology- it's just a simple and useful combination of two things that have been around for a while to make a minimal- but highly effective- filter format.

How do I use it?
----------------

On firts start Cascade creates a folder called `isf` which contains all the default shaders that are shipped with the software.

To see the whole shader collection, or write your own, go to `editor.isf.video <https://editor.isf.video>`_.

If you see an effect that you would like to use, simply copy the code from the editor window on the left to a text file with the ending `.fs`.

.. image:: https://github.com/ttddee/CascadeDocs/blob/main/docs/source/image/isfshaders01.png?raw=true

Place the text file into the `isf` folder. External shaders are compiled when the application starts, so you will have to restart Cascade and the new shader should show up as a node in the menu.

.. image:: https://github.com/ttddee/CascadeDocs/blob/main/docs/source/image/isfshaders02.png?raw=true

.. image:: https://github.com/ttddee/CascadeDocs/blob/main/docs/source/image/isfshaders03.png?raw=true

.. note:: 
    As of now, the ISF specification has not been fully implemented. What's still to come, in particular, is support for multiple input images and multiple render passes. 
    If you add a shader and it does not show up in the menu, check the log file `Cascade.log` for clues.


