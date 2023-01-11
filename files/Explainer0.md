# Explainer0

Your job is to write a shortish notebook explaining your chosen concept(s). Communicate the concepts as best as you can.


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
## Getting started

* Go to [google colab](https://colab.research.google.com)
* Open new notebook
* Name it FirstnameExplainer0 (where Firstname is replaced with your actual first name)
* Share the notebook with me (nolan.donoghue@viewpoint.org)
* Make cells!
* Go [here](https://docs.google.com/spreadsheets/d/1oZ4ZAtPQ9-fkB8_r6QfIMmAdO4iFZCZhmdSenTunu-8/edit?usp=sharing) and choose a lil topic. Talk to me if you'd like a topic that isn't listed.

## Tips
* Your notebook should NOT be just code cells
* You are encouraged to use chatgpt to help write your explainer. Make sure you save the chats you use to show me.
* Extra cool if your notebook contains questions a learner could attempt to answer