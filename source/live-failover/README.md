Live Failover Tests
===================

This document describes usage for the Live Failover test suite.

In this directory, you will find a script called ``live-failover.py``. This script is designed to be used by drivers to run the live failover tests.

In the ``/configs`` directory you will find a number of json files. ``live-failover.py`` should be run one time for each config file in the ``/configs`` directory.  While ``live-failover.py`` is running, the driver should run specified workloads against the cluster described in the json file (see spec, TODO link).

Requirements
------------

The ``live-failover.py`` script requires python 3.

The script also requires that the binary for the automation agent be in an executable called ``mongodb-mms-automation-agent`` in the working directory.

Running the live-failover.py script
-----------------------------------

The ``live-failover.py`` script operates in three stages represented by three distinct commands:

* `start` - launch a mongo cluster matching the given config file (via the automation agent):

   ``python live-failover.py start <path/to/config/file>``

* `scenario` - put the cluster through a series of restarts (via the automation agent) using a simulated server downtime of T seconds:

   ``python live-failover.py scenario --sleep T``

* `stop` - spin down the cluster (and the automation agent)

   ``python live-failover.py stop``


Use `--help` for more information.