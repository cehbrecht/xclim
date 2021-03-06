==================
Climate indicators
==================

:class:`xclim.core.indicator.Indicator` instances essentially perform the same computations as the functions
found in the :mod:`xclim.indices` library, but also run a number of health checks on input data
and assign attributes to the output arrays. So for example, if there are missing values in
a time series, indices won't notice, but indicators will return NaNs for periods with missing
values (see :ref:`Missing values`). Indicators also check that the input data has the expected frequency (e.g. daily) and that
it is indeed the expected variable (e.g. a precipitation flux). The output is assigned attributes
that conform as much as possible with the `CF-Convention`_.

Indicators are split into realms (atmos, land, seaIce), according to the variables they operate on.
See :ref:`Defining new indicators` for instruction on how to create your own indicators.


atmos: Atmosphere
=================

.. raw:: html
    <dl>
   {% for indname, ind in indicators['atmos'].items() %}
     <dt><b>{{ ind.title }}</b>  (<var>atmos.{{ indname | safe}}</var>)</dt>
     <dd>{{ ind.abstract }} <br>
     Based on <a class="reference internal" href="indices.html#{{ ind.function }}" title="{{ ind.function }}"><code class="xref">{{ ind.function }}</code></a> <br>
     Produces {% for var in ind['outputs'] %} <code>{{ var['var_name'] }}: {{ var['long_name'] }} [{{ var['units'] }}]</code> {% endfor %}
     </dd>
   {% endfor %}
   </dl>

land: Land surface
==================

.. raw:: html
    <dl>
   {% for indname, ind in indicators['land'].items() %}
     <dt><b>{{ ind.title | e }}</b>  (<var>land.{{ indname | safe}}</var>) </dt>
     <dd>{{ ind.abstract | e }} <br>
     Based on <a class="reference internal" href="indices.html#{{ ind.function }}" title="{{ ind.function }}"><code class="xref">{{ ind.function }}</code></a> <br>
     Produces {% for var in ind['outputs'] %} <code>{{ var['var_name'] }}: {{ var['long_name'] }} [{{ var['units'] }}]</code>  {% endfor %}
     </dd>
   {% endfor %}
   </dl>

seaIce: Sea ice
===============

.. raw:: html
    <dl>
   {% for indname, ind in indicators['seaIce'].items() %}
     <dt><b>{{ ind.title }}</b>  (<var>seaIce.{{ indname | safe}}</var>) </dt>
     <dd>{{ ind.abstract }}<br>
     Based on <a class="reference internal" href="indices.html#{{ ind.function }}" title="{{ ind.function }}"><code class="xref">{{ ind.function }}</code></a> <br>
     Produces {% for var in ind['outputs'] %} <code>{{ var['var_name'] }}: {{ var['long_name'] }} [{{ var['units'] }}]</code> {% endfor %}
     </dd>
   {% endfor %}
   </dl>





.. _CF-Convention: http://cfconventions.org/
