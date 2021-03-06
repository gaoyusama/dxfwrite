.. _AngularDimension:

AngularDimension
================

Type: Composite Entity

.. class:: AngularDimension

    Draw an angle dimensioning line at dimline `pos` from `start` to `end`,
    dimension text is the angle build of the three points start-center-end.

.. method:: AngularDimension.__init__(pos, center, start, end, dimstyle='angle.deg', layer=None, roundval=None)

    :param pos: location as (x, y) tuple of dimension line, line goes
        through this point
    :param center: center point as (x, y) tuple of angle
    :param start: line from center to start is the first side of the
        angle
    :param end: line from center to end is the second side of the angle
    :param str dimstyle: dimstyle name, 'Default' - style is the
        default value
    :param str layer: dimension line layer, override the default value
        of dimstyle
    :param int roundval: count of decimal places

Example
-------

.. code-block:: python

   import dxfwrite
   from dxfwrite import DXFEngine as dxf

   # Dimlines are separated from the core library.
   # Dimension lines will not generated by the DXFEngine.
   from dxfwrite.dimlines import dimstyles, AngularDimension

   # create a new drawing
   dwg = dxf.drawing('dimlines.dxf')

   # dimensionline setup:
   # add block and layer definition to drawing
   dimstyles.setup(dwg)

   # There are three dimstyle presets for angular dimension
   # 'angle.deg' (default), 'angle.rad', 'angle.grad' (gon)
   # for deg and grad default roundval = 0
   # for rad default roundval = 3

   # angular dimension in grad (gon)
   dwg.add(AngularDimension(pos=(18, 5), center=(15, 0), start=(20, 0),
                            end=(20, 5), dimstyle='angle.grad'))

   # angular dimension in degree (default dimstyle), with one fractional digit
   dwg.add(AngularDimension(pos=(18, 10), center=(15, 5), start=(20, 5),
                            end=(20, 10), roundval=1))

.. image:: arcdim.png
