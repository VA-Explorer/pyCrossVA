Background
----------

About Verbal Autopsy
^^^^^^^^^^^^^^^^^^^^

From `Wikipedia <https://en.wikipedia.org/wiki/Verbal_autopsy>`_:

  A verbal autopsy (VA) is a method of gathering health information about a deceased
  individual to determine his or her cause of death. Health information and a
  description of events prior to death are acquired from conversations or
  interviews with a person or persons familiar with the deceased and analyzed by
  health professional or computer algorithms to assign a probable cause of death.

  Verbal autopsy is used in settings where most deaths are undocumented. Estimates
  suggest a majority of the 60 million annual global deaths occur without medical
  attention or official medical certification of the cause of death. The VA method
  attempts to establish causes of death for previously undocumented subjects,
  allowing scientists to analyze disease patterns and direct public health policy
  decisions.

  Noteworthy uses of the verbal autopsy method include the Million Death Study in
  India, China's national program to document causes of death in rural areas, and
  the Global Burden of Disease Study 2010.

CrossVA
^^^^^^^^

CrossVA is a python package for transforming verbal autopsy data collected using
the 2016 WHO VA instrument (v1.5.1, or v1.4.1), 2012 WHO VA instrument, and
the PHRMC short questionnaire into a format suitable for openVA.

The flagship function of this package is the transform() function, which
prepares raw data for use in a verbal autopsy algorithm. The user can either
choose to use a default mapping, or create a custom one of their own design. The
default mappings are listed in `Currently Supported`_ and can be invoked by
passing in a tuple as the mapping argument in ``("input", "output")`` format.


Project Status
^^^^^^^^^^^^^^

This package is a fleshed out prototype of the framework MTIRE is
proposing for the open source CrossVA project going forward. This is an
alpha version (as of April 8, 2019) intended to demonstrate full concept
and flexibility, not for use in research or verbal autopsy evaluations.


Simple Usage
------------

The simplest way to get started with CrossVA is to invoke the ``transform`` function
with a default mapping, and the path to a csv containing your raw verbal autopsy
data.

.. code-block:: python

  from pycrossva.transform import transform

  transform(("2016WHOv151", "InterVA4"), "path/to/data.csv")

You can also call the transform function on a Pandas DataFrame, if you wanted to
read in and process the data before calling the function.

.. code-block:: python

  from pycrossva.transform import transform

  data = pd.read_csv("path/to/data.csv")
  data = some_special_function(data)
  transform(("2016WHOv151", "InterVA4"), data)

There are more details available in `transform function`_

Command Line
------------

`pycrossva` also contains a command line tool that allows users to invoke the main
transform function on one or more files from the command line, without having
to use the `Python` interpreter or write a `Python` script.




Currently Supported
--------------------

Inputs
^^^^^^^

* 2016 WHO Questionnaire from ODK export, v1.5.1
* 2016 WHO Questionnaire from ODK export, v1.4.1
* 2012 WHO Questionnaire from ODK export
* PHRMC Shortened Questionnaire

Outputs
^^^^^^^^

* InSillicoVA
* InterVA4
* InterVA5

Roadmap
-------

This is an alpha version of package functionality, with only limited support.

Expanding outputs
^^^^^^^^^^^^^^^^^^

One component of moving to a production version will be to offer additional
mapping files to support more output formats. The package currently supports
mapping to the InterVA4 and InsillicoVA format.

The following is a list of
additional outputs for other algorithms to be supported in future versions:

* Tarrif
* Tarrif 2.0

Style
-----

This package was written using google style guide for Python and PEP8 standards.
Tests have been written using doctest.

License
--------

This package is licensed under the GNU GENERAL PUBLIC LICENSE (v3, 2007).
Everyone is permitted to copy and distribute verbatim copies
of this license document, but changing it is not allowed.
