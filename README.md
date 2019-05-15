# Doodle AI NST

Contributors: Amirmehdi Sharifzad & Nitisha Agarwal 
Resources: <a href="https://www.coursera.org/learn/convolutional-neural-networks/home/welcome">Coursera CNN course</a>, <a href="https://arxiv.org/pdf/1508.06576.pdf">Gatsy's NST Algorithm</a>

Neural Style Transfer (NST) is an artistic use of Convolutional Neural Networks that allows for the merge of a content image C and a style image S. An example of its use is shown below: 

![alt text]("https://github.com/nitisha121/doodle_ai/blob/master/style_transfer/images/example_circle.png" | width=1000)

We used a pre-trained ConvNet model with 19 layers -  <a href="http://www.vlfeat.org/matconvnet/pretrained/">VGG-19</a> - which is stored as a Python dictionary -- key:variable name, value: tensor with variable value. 

The purpose of this project was to transpose my doodling style onto simple images, such as flowers. This is one of the earlier examples:

<table align="center">
    <tr>
        <td>
            <img src="https://github.com/nitisha121/doodle_ai/blob/master/content/pink_flower.jpg" width="400px">
        </td>
        <td>
            <img src="https://github.com/nitisha121/doodle_ai/blob/master/style_transfer/images/elephant_scaled.jpg" width="400px">
        </td>
        <td>
            <img src="https://github.com/nitisha121/doodle_ai/blob/master/output/generated_image_nini.jpg" width="400px">
        </td>
    </tr>
</table>

## How does Style Transfer Work?


