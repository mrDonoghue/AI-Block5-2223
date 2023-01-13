
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