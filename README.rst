
Introduction
============

A MicroPython driver for the Sensirion SGP30 gas sensor with eCO2 and TVOC output. This sensor uses I2C!

Installation
=============

On a LoPy, just put ``adafruit_sgp30.py`` in the ``lib/`` directory.

Usage Notes
=============

See `the guide <https://learn.adafruit.com/adafruit-sgp30-gas-tvoc-eco2-mox-sensor/circuitpython-wiring-test>`_
for wiring instructions.

First, import the library:

.. code-block:: python

    import adafruit_sgp30

Next, initialize the I2C bus object:

.. code-block:: python

    from machine import I2C
    i2c = I2C(0, I2C.MASTER)
    i2c.init(I2C.MASTER, baudrate=100000)

Since we have the I2C bus object, we can now use it to instantiate the SGP30 object:

.. code-block:: python

    sgp30 = adafruit_sgp30.Adafruit_SGP30(i2c)

Reading from the Sensor
------------------------

To read from the sensor:

.. code-block:: python

    co2eq, tvoc = sgp30.iaq_measure()
    print("CO2eq = %d ppm \t TVOC = %d ppb" % (co2eq, tvoc))


Contributing
============

Contributions are welcome! Please read our `Code of Conduct
<https://github.com/adafruit/Adafruit_CircuitPython_sgp30/blob/master/CODE_OF_CONDUCT.md>`_
before contributing to help this project stay welcoming.

Building locally
================

Sphinx documentation
-----------------------

Sphinx is used to build the documentation based on rST files and comments in the code. First,
install dependencies (feel free to reuse the virtual environment from above):

.. code-block:: shell

    python3 -m venv .env
    source .env/bin/activate
    pip install Sphinx sphinx-rtd-theme

Now, once you have the virtual environment activated:

.. code-block:: shell

    cd docs
    sphinx-build -E -W -b html . _build/html

This will output the documentation to ``docs/_build/html``. Open the index.html in your browser to
view them. It will also (due to -W) error out on any warning like Travis will. This is a good way to
locally verify it will pass.
