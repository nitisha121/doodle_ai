# Doodle AI NST

Contributors: Amirmehdi Sharifzad & Nitisha Agarwal 
Resources: <a href="https://www.coursera.org/learn/convolutional-neural-networks/home/welcome">Coursera CNN course</a>, <a href="https://arxiv.org/pdf/1508.06576.pdf">Gatsy's NST Algorithm</a>

Neural Style Transfer (NST) is an artistic use of Convolutional Neural Networks that allows for the merge of a content image C and a style image S. An example of its use is shown below: 

<img src="https://github.com/nitisha121/doodle_ai/blob/master/style_transfer/images/ex_cnn.PNG">

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

**C**: An image of a flower 
**S**: Doodle of an elephant
**G** (generated): Flower image - more greyscale and some transposed details. 

## How does Style Transfer Work?

The NST algorithm:
- Image is inputted into CNN 
- Activation values are sampled in a late layer of the model and stored in a Gram Matrix 
- The Style image cost and the Content image cost are calculated to sum to total cost
- The total cost of each generated image G is calculated and minimized at each iteration 
- The generated image G is optimized until max number of iterations specified is reached
