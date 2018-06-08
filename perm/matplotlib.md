tricks of matplotlib


# legend

- [plot legend as a separate file](https://stackoverflow.com/questions/4534480/get-legend-as-a-separate-picture-in-matplotlib)
- [legend outside of the plot](https://stackoverflow.com/a/4700762/557067)
- [only one marker](https://stackoverflow.com/questions/6146778/matplotlib-legend-markers-only-once?rq=1)
  - use `numpoints=1`


# axis

- [turn off axis](https://stackoverflow.com/questions/14908576/how-to-remove-frame-from-matplotlib-pyplot-figure-vs-matplotlib-figure-frame)


# colormap

- [map int to rbg](https://stackoverflow.com/questions/15140072/how-to-map-number-to-color-using-matplotlibs-colormap)

# plot

- [plot marker size](https://matplotlib.org/1.3.1/examples/pylab_examples/filledmarker_demo.html)
  - `plot(markersize=size)`
- [scatter plot marker size](https://stackoverflow.com/questions/14827650/pyplot-scatter-plot-marker-size)
  - `scatter(s=size)`
- [fill_between](https://matplotlib.org/examples/pylab_examples/fill_between_demo.html)
  - for example, to give the 25/75 quantile or confidence interval
- [get color of recent ploted line](https://stackoverflow.com/questions/36699155/how-to-get-color-of-most-recent-plotted-line-in-pythons-plt)
  - `p=plt.plot(...); color = p[0].get_color()`
- [set number of ticks](https://stackoverflow.com/questions/6682784/how-to-reduce-number-of-ticks-with-matplotlib)
  - `pyplot.locator_params(nbins=4)`

# colorbar

- [standalone cb](https://stackoverflow.com/a/16599889/557067)

example:

```python
a = np.array([[0,1]])
fig = plt.figure(figsize=(9, 1.5))
img = plt.imshow(a, cmap="Reds")
plt.gca().set_visible(False)
cax = plt.axes([0.1, 0.2, 0.8, 0.6])  # the x, y, height and width
cbar = plt.colorbar(orientation="horizontal", cax=cax, ticks=[0, 1])
cbar.ax.set_xticklabels(['l1', 'l2'])
cbar.outline.set_visible(False)  # hide the border
```

[more example](http://193.166.24.212:9999/notebooks/legend_and_colorbars.ipynb)

# custom style

refer to [the full list](https://matplotlib.org/users/customizing.html)