## Today
## Code drop
```python
!wget https://raw.githubusercontent.com/karpathy/char-rnn/master/data/tinyshakespeare/input.txt
```

## MNIST NN Lab in [nb3](https://colab.research.google.com)
### Videos
Fortunately for you, I have made a series of videos to help you through this process.

0. [Getting Started](https://www.loom.com/share/d26bb53ad2d447049db79f55c20755a6)
1. [Data Adjustments - X](https://www.loom.com/share/183e3cb95ef246a6b13eb4c729add079)
2. [Data Adjustments - y](https://www.loom.com/share/21f59b3a1b00492dbd55689d89be44c7)
3. [Actually make neural network](https://www.loom.com/share/138697d7e4e84ef5ab8fe99ebbd99011)

Please comment on the video for any parts that are unclear!!

### I think I'm done
* Did you compute the accuracy on the testing images?
* Have you tried hard to improve the accuracy?
    * mess with the number of layers
    * mess with the number of nodes in hidden layers
* Do you actually understand what's going on?
    * If not, please please please have a convo with ChatGPT about the code. Paste the code in and ask it to explain! Ask questions. You might * even then try to restate it in your own words and ask it to critique you!
* Does your code actually do SGD or vanilla GD? SGD might also help improve accuracy and it should speed up training
    * remember that we'll want to make a  DataLoaders for this which will require zipping the X and y together
* See if you can figure out how to get this to use the GPU to run extra fast (try using the googles and the ChatGPTs)
## Notebooks


```python
def our_plot(xish):
  c0 = xish[y.squeeze() == 0].detach()
  c1 = xish[y.squeeze() == 1].detach()
  plt.scatter(c0[:, 0], c0[:, 1], label="0", color="red", marker="x")
  plt.scatter(c1[:, 0], c1[:, 1], label="1", color="blue", marker="o")
  plt.xlim([-5,5])
  plt.ylim([-5,5])
  # Label the axes and add a legend
  plt.xlabel("f1")
  plt.ylabel("f2")
  plt.legend()

  # Show the plot
  plt.show()
```

## Old
* [nb0](https://classroom.github.com/a/DF3J9551)
* [nb1](https://classroom.github.com/a/QpcoqLfc)
* [nb2](https://classroom.github.com/a/sm-T03pF)
* [SGD](https://colab.research.google.com/drive/1GkfznyWpRY9UG2KOd5582CW3GNkNAxTq?usp=sharing)
* [Widget](files/Widget.md)
* [Explainer0](files/Explainer0.md)
* [semEnd](files/semEnd.md)
* [MNIST Baseline Lab](files/MNIST%20Baseline%20Lab.md)
