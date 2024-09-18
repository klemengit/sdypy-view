SDyPy-view project
==================

Example usage:

.. code-block:: python

    import sdypy as sd

    nodes = ... # Finite element nodes
    elements ... # Finite elements

    plotter = sd.view.Plotter3D(nodes, elements)
    plotter.add_fem_mesh(nodes, elements)
    plotter.show(show_grid=True, show_axes=True)

To animate a mode shape:

.. code-block:: python

    mode_shape = ... # Shape (n_nodes, 3)

    plotter = sd.view.Plotter3D(nodes, elements)
    plotter.add_fem_mesh(nodes, elements, animate=mode_shape)

To animate according to a time history:

.. code-block:: python

    time_history = ... # Shape (n_nodes, 3, n_timesteps)

    plotter = sd.view.Plotter3D(nodes, elements)
    plotter.add_fem_mesh(nodes, elements, animate=time_history)

To color the mesh according to a norm of the ``mode_shape``:

.. code-block:: python

    field = ... # Shape (n_nodes,)

    plotter = sd.view.Plotter3D(nodes, elements)
    plotter.add_fem_mesh(nodes, elements, animate=mode_shape, scalar="norm")

Here, if ``scalar="norm"`` is passed, the mesh will be colored according to the
norm of the ``mode_shape`` (or more generally, according to the norm of the ``animate`` argument).
To color the mesh according to an arbitrary field, the ``scalar`` argument must be of shape ``(n_nodes, n_timesteps)``. 

The ``Plotter3D`` is a wrapper around the ``pyvista.BackgroundPlotter`` with some added functionality around
convenient simplifications for use in structural dynamics.