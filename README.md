# Links link
<base target="_blank">

## Today's class
* [semEnd](files/semEnd.md)
* [Explainer0](files/Explainer0.md)



# Widget
```python
import torch
import ipywidgets as widgets
from IPython.display import display
from IPython.display import clear_output
from ipywidgets import Output
import matplotlib.pyplot as plt
%matplotlib inline
# Generate some random data for the scatterplot
torch.manual_seed(0)
X = torch.randint(low=0,high=5, size=(20,))

Y = X * 2 + 3 + torch.randn(20)

# Define the sliders for the linear regression line
w_slider = widgets.FloatSlider(value=0, min=-5, max=5, step=0.1, description='w')
b_slider = widgets.FloatSlider(value=0, min=-5, max=5, step=0.1, description='b')
out = Output()
# Define the function to update the plot based on the slider values
def update_plot(change):
    clear_output(wait=True)
    with out:
      w = w_slider.value
      b = b_slider.value
      # plt.clf()
      plt.scatter(X, Y)
      plt.plot(X, X * w + b, 'r')
      plt.ylim(0, 10)
      plt.xlim(0, 10)
      plt.draw()
    display(w_slider, b_slider, out)
    


w_slider.observe(update_plot, names='value')
b_slider.observe(update_plot, names='value')

# Display the sliders and the initial plot
# display(w_slider, b_slider)
update_plot(None)


```

## Using Colab Reminders:
* Colab does ***NOT*** autosave!!!
* Cmd+O -> Github tab
* Look for the right repository in the `Repository` dropdown. If it's not there, put Viewpoint-School-Computer-Science in the `Enter a GitHub URL or search by organization or user` search box and try again
* ***MAKE SURE*** we're using GPU
    - Runtime -> Change Runtime Type -> Select GPU
* Always run the first few cells
* Save work whenever you've finished a meaningful "chunk" of work and definitely at the end of class
    - File -> Save a copy in Github.
    - Look at the Repository dropdown and make sure it's the right name, fixing if not
    - ***CHANGE*** the commit message to something meaningful that captures what has happened in the file since the last save
    - Make sure the `Include a link to Colaboratory` checkbox is checked
    - Hit `OK`


## Notebooks
* [nb0](https://classroom.github.com/a/DF3J9551)
* [nb1](https://classroom.github.com/a/QpcoqLfc)
* [nb2](https://classroom.github.com/a/sm-T03pF)

## Old
* [MNIST Baseline Lab](files/MNIST%20Baseline%20Lab.md)
* Open nb2 in [colab](https://colab.research.google.com)
* run first 2 code cells (the imports)
* Gradient descent example
    ```
    heights = tensor([16., 20., 22., 24., 40., 52., 53., 56., 63., 82.])
    flowers = tensor([2., 2., 3., 2., 4., 5., 6., 5., 6., 8.])
    ```
* Gradient descent new example:
    ```
    x=tensor([35., 42., 43., 54., 59., 64., 76., 78., 82., 98.])
    y=tensor([52., 55., 54., 52., 52., 47., 47., 43., 45., 40.])
    ```
* Gradient descent new new example:
    ```
    x1s=tensor([-0.4792, -0.1857, -1.1063, -1.1962,  0.8125,  1.3562, -0.0720,  1.0035,  0.3616, -0.6451,  0.3614,  1.5380, -0.0358,  1.5646, -2.6197,  0.8219,  0.0870, -0.2990,  0.0918, -1.9876])
    x2s=tensor([2.7803, 3.3571, 4.4779, 2.4817, 2.1915, 2.4982, 3.9154, 3.3288, 2.4702, 3.5133, 3.0971, 3.9686, 2.2979, 2.6723, 2.6079, 1.5365, 3.2961, 3.2611, 3.0051, 2.7654])
    x3s=tensor([12.9231, 17.8968, 18.2864, 15.9886, 19.1936, 22.0203, 29.4309, 20.8729, 21.2878, 19.6278, 10.4061, 19.8674, 20.3012, 32.3162, 19.0382, 21.5077, 19.8264, 14.1566, 25.7141, 23.7597])
    ys=tensor([0., 0., 0., 0., 1., 1., 1., 1., 1., 0., 0., 1., 1., 1., 0., 1., 0., 0., 1., 0.])
    ```        