---
title: "Import & Work With Python Packages"
subtitle: "Learn how to import a Python package or a specific part of (a module, class or function) a Python package. You will also learn about package aliases in Python. "
author: "Leah Wasser"
date: 2023-02-13
categories:
  - Python
  - Get-started
  - Packages
nav_title: "Use Python packages"
partner: "dss"
image: "/images/python/import-python-packages.png"
module: "install-python"
url: "python/install/import-packages.html"
format: hugo-md
order: 4
---

{{< toc >}}

Import and Install Python Packages for Science

Learn about managing Python packages in your code.

{{< noticeowl "learn" >}}

After completing this chapter, you will be able to:

* Explain what a package is in **Python**.
* Import a package into **Python**.
* List important **Python** packages for science.

## <i class="fa-solid fa-square-check"></i> What You Need

You should have Bash and Conda setup on your computer and a conda environment such as `geo-python`. Follow the <a href="/setup-geo-python/">Setup Git, Bash, and Conda on your computer</a> to install these tools.

{{< /noticeowl >}}

## What is a Python Package

In **Python**, a package is a bundle of pre-built functionality that adds to the functionality available in base **Python**. Base **Python** can do many things such as perform math and other operations. However, **Python** packages can significantly extend this functionality.

You can think of a **Python** package as a toolbox filled with tools. The tools in the toolbox can be used to do things that you would have to otherwise hand code in base **Python**. These tasks are things that many people might want to do in **Python**, thus warranting the creation of a package. After all, it doesn't make sense for everyone to hand code everything!

For example, the **matplotlib** package allows you to create plots of data. Since most of us create plots routinely, having a **Python** package to create plots makes programming more efficient for everyone who needs to create plots.

## Open Source Python Packages for spatial and time series data

There are many different packages available for **Python**. Some of these are optimized for scientific tasks such as:

-   Statistics
-   Machine learning
-   Using geospatial data
-   Plotting & visualizing data
-   Accessing data programmatically

and more! The list below contains a few core packages that are often
used by scientists as examples.

-   **os**: handle files and directories.
-   **glob**: create lists of files and directories for batch processing.
-   **matplotlib**: plot data.
-   **numpy**: work with data in array formats (often related to imagery and raster format data).
-   **pandas**: work with tabular data in a DataFrame format.
-   **rioxarray**: work with raster (image and arrays) data using XArray and rioxarray approaches.
-   **geopandas**: work with vector format (shapefiles, geojson - points, lines and polygons) using a geodataframe format.

## Where Do Packages Live On Your Computer?

Packages are organized directories of code that can be installed and then imported to your code file (e.g. .py script, **Jupyter Notebook** file).

When you install a package, you may be wondering, where does it go? If you are
using mambaforge on a Mac, the packages that you install are located in your mambaforge directory under `envs` (e.g. `/home/username/mambaforge/envs/`).

When you install a package into the conda environment of your choice. For example, `geo-python` that you installed in this tutorial series will end up in the `/home/username/mambaforge/envs/geo-python` folder.

<img src="../images/python/conda-environment-python-packages.png" title="When you install Python packages in an conda environment, they will be located within the /home/username/mambaforge/envs/environment-name directory." data-fig-alt="Image showing a directory structure within the folder /username/mambaforge/envs/environment-name. Within the directory there is a conda-meta directory that contains a list of all of the packages that are in your environment. " alt="When you install Python packages in an conda environment, they will be located within the /home/username/mambaforge/envs/environment-name directory." />

Once packages are installed in your **Python** environment (e.g. `geo-python` conda environment), you can call them in **Python** at the command line, in a script (.py file), or in a **Jupyter Notebook** file.

You have to explicitly call and load (i.e. import) each package that you want to use in your script (.py file) or **Jupyter Notebook** file, in order for the functions (or tools) in that package to be available for use in your code.

{{< noticeowl "tip" >}}

You can import `Python` packages using `import package-name`. Once a package has been imported, you can call functions from that package

{{< /noticeowl >}}

### Python Packages Can Contain Modules

Packages can contain many modules (i.e. units of code) that each provide different functions and can build on each other. For example, the **matplotlib** package provides functionality to plot data using modules, one of which is the commonly used module called **pyplot**.

Every **Python** package should have a unique name. This allows you to import the package using the name with the `import` command.

For example, the command below imports the **matplotlib** package.

``` python
import matplotlib
```

Now you can create a plot but notice that you have to call
matplotlib as a full word each time you run a plot command below.

``` python
import matplotlib

# Sample data
x = [1, 2, 3, 4, 5]
y = [2, 4, 6, 8, 10]

# Create a basic plot
matplotlib.pyplot.plot(x, y)

# Add labels and title
matplotlib.pyplot.xlabel("X-axis")
matplotlib.pyplot.ylabel("Y-axis")
matplotlib.pyplot.title("Simple Matplotlib Plot")

# Show the plot
matplotlib.pyplot.show()
```

<img src="4-python-packages_files/figure-markdown_strict/cell-3-output-1.png" data-fig-alt="Here is the alt tag" width="659" height="449" alt="A basic line plot" />

### What is a Module in a Python Package?

Packages often have modules. A module is a set of related functionality that lives within the package.

For example, **pyplot** is a module within the matplotlib package that makes it easier to quickly set up plots.

You can import a specific module like **pyplot** by first calling the package name and then the module name - using `.` to separate the names like this:

``` python
import matplotlib.pyplot
```

You can also import the module using an alias or short name, such as `plt` for `matplotlib.pyplot`.

``` python
import matplotlib.pyplot as plt
```

Below you import both matplotlib and numpy to create a plot.

``` python
import matplotlib.pyplot as plt
import numpy as np

# Generate some sample data
x = np.linspace(0, 2 * np.pi, 100)
y = np.sin(x)

# Create a prettier plot
plt.figure(figsize=(8, 6))  # Set the figure size
plt.plot(
    x,
    y,
    label="Sine Wave",
    color="b",
    linewidth=2,
    linestyle="-",
    marker="o",
    markersize=6,
    markerfacecolor="r",
)
plt.title("Prettier Matplotlib Plot")
plt.xlabel("X-axis")
plt.ylabel("Y-axis")
plt.grid(True, linestyle="--", alpha=0.7)
plt.legend(loc="upper right")
plt.tight_layout()

# Show the plot
plt.show()
```

<img src="4-python-packages_files/figure-markdown_strict/cell-5-output-1.png" data-fig-alt="And another Here is the alt tag" width="757" height="564" alt="Another line plot" />

And an interactive plot...

``` python
print("bokeh would be here")
# from bokeh.plotting import figure, show

# # Sample data
# x = [1, 2, 3, 4, 5]
# y = [2, 4, 6, 8, 10]

# # Create a Bokeh figure
# p = figure(
#     title="Simple Bokeh Plot", x_axis_label="X-axis", y_axis_label="Y-axis"
# )

# # Add a line plot
# p.line(x, y, line_width=2, legend_label="Line")

# # Display the plot
# show(p)
```

    bokeh would be here
