===================================
Poles and Zeros, Frequency Response
===================================

.. note::

    For metadata read using
    :func:`~obspy.core.inventory.inventory.read_inventory` into
    :class:`~obspy.core.inventory.inventory.Inventory` objects
    (and the corresponding sub-objects :class:`~obspy.core.inventory.network.Network`,
    :class:`~obspy.core.inventory.station.Station`,
    :class:`~obspy.core.inventory.channel.Channel`,
    :class:`~obspy.core.inventory.response.Response`), there is a convenience method
    to show Bode plots, see e.g.
    :meth:`Inventory.plot_response() <obspy.core.inventory.inventory.Inventory.plot_response>`
    or :meth:`Response.plot() <obspy.core.inventory.response.Response.plot>`).

The following lines show how to calculate and visualize the frequency response
of a LE-3D/1s seismometer with sampling interval 0.005s and 16384 points of
fft. Two things have to be taken into account for the phase (actually for the
imaginary part of the response):

* the fft that is used is defined as exp(-i*phi), but this minus sign is
  missing for the visualization, so we have to add it again
* we want the phase to go from 0 to 2*pi, instead of the output from atan2
  that goes from -pi to pi 

.. plot:: tutorial/code_snippets/frequency_response.py
   :include-source:
