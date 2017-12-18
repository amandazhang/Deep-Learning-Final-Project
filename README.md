# ECBM E4040 Fall 2017 Final Project 

## Project Title: A Neural Algorithm of Artistic Style

+ Term: Fall 2017

+ Team ID: AAAA

### Team Members 

+ Qingyuan Zhang qz2283
+ Yike Peng yp2425
+ Renjie Li rl2928
 

### Link to original paper: https://arxiv.org/pdf/1508.06576v2.pdf

### Project summary

This project explores and visualizes 272 universities in America by using the data on ([College Scorecard Database](https://collegescorecard.ed.gov/data/documentation/)), ([2016 Forbes Ranking](data/ranking_forbes_2016.csv)), ([HappyScore Data](data/Happinessdata.csv)) and ([Crime Data](data/CrimeData_final.csv)). We created a Shiny App to help users discover and compare universities. 

+ Filter & Rank——easily discover and compare the universities that meet user's requirements

Two filter parts. One part is the basic filter: the user can choose universities based on "Major", "Type of School" and "Type of City". The other part is the advanced filter: they can give their weights to "Academic Performance", "Average Cost", "Earning & Jobs", "Social Security" and "Life Quality", based on how important they think these factors matter to them. 

Two ranking options. One option is based on the Forbes University Rankings. The other one is using the weights the user gave to calculate the rank of these universities - ultimately producing a personalized ranking. 

+ Map & Plot——visualization of relevant features of the universities 

Map: Every university that meet the user's requirments will show on the map. After clicking on the university, both the URL and Forbes rank of the school will be in view.

Plots: There will be four interacitve density plots based on the filtered data. These will show the average of "Admission Rate", "Average Cost", "Crime Rate" and "Earnings" of the selected(filtered) universities.

### Outlook

![Output](Pics/Outputs/Mixed.jpg)


### Note 
To reproduce our work, clone the whole repository onto your own local machine and then set the working directory to [`app`] folder, in your R console, run this code:
```
python neural_style.py --content Pics/Content/boston.jpg --styles Pics/Styles/composition_vii.jpg --iterations 500 --output [your output path and output name]
```


### **Contribution statement**: ([default](doc/a_note_on_contributions.md)) All team members contributed equally in all stages of this project. All team members approve our work presented in this repository including this contributions statement. 

This folder is organized as follows.

```
proj/
├── app/
├── lib/
├── data/
├── doc/
└── output/
```




## Running



Use `--iterations` to change the number of iterations (default 1000).  For a 512×512 pixel content file, 1000 iterations take 2.5 minutes on a GeForce GTX Titan X GPU, or 90 minutes on an Intel Core i7-5930K CPU.

## Example 1

Running it for 500-2000 iterations seems to produce nice results. With certain
images or output sizes, you might need some hyperparameter tuning (especially
`--content-weight`, `--style-weight`, and `--learning-rate`).

The following example was run for 1000 iterations to produce the result (with
default parameters):

![output](examples/1-output.jpg)

These were the input images used (me sleeping at a hackathon and Starry Night):

![input-content](examples/1-content.jpg)

![input-style](examples/1-style.jpg)

## Example 2

The following example demonstrates style blending, and was run for 1000
iterations to produce the result (with style blend weight parameters 0.8 and
0.2):

![output](examples/2-output.jpg)

The content input image was a picture of the Stata Center at MIT:

![input-content](examples/2-content.jpg)

The style input images were Picasso's "Dora Maar" and Starry Night, with the
Picasso image having a style blend weight of 0.8 and Starry Night having a
style blend weight of 0.2:

![input-style](examples/2-style1.jpg)
![input-style](examples/2-style2.jpg)

## Tweaking

`--style-layer-weight-exp` command line argument could be used to tweak how "abstract"
the style transfer should be. Lower values mean that style transfer of a finer features
will be favored over style transfer of a more coarse features, and vice versa. Default
value is 1.0 - all layers treated equally. Somewhat extreme examples of what you can achieve:

![--style-layer-weight-exp 0.2](examples/tweaks/swe02.jpg)
![--style-layer-weight-exp 2.0](examples/tweaks/swe20.jpg)

(**left**: 0.2 - finer features style transfer; **right**: 2.0 - coarser features style trasnfer)

`--content-weight-blend` specifies the coefficient of content transfer layers. Default value -
1.0, style transfer tries to preserve finer grain content details. The value should be
in range [0.0; 1.0].

![--content-weight-blend 1.0](examples/tweaks/cwe10_default.jpg)
![--content-weight-blend 0.1](examples/tweaks/cwe01.jpg)

(**left**: 1.0 - default value; **right**: 0.1 - more abstract picture)

`--pooling` allows to select which pooling layers to use (specify either `max` or `avg`).
Original VGG topology uses max pooling, but the [style transfer paper][paper] suggests
replacing it with average pooling. The outputs are perceptually differnt, max pool in
general tends to have finer detail style trasnfer, but could have troubles at
lower-freqency detail level:

![--pooling max](examples/tweaks/swe14_pmax.jpg)
![--pooling avg](examples/tweaks/swe14_pavg.jpg)

(**left**: max pooling; **right**: average pooling)

`--preserve-colors` boolean command line argument adds post-processing step, which
combines colors from the original image and luma from the stylized image (YCbCr color
space), thus producing color-preserving style trasnfer:

![--pooling max](examples/tweaks/swe14_pmax.jpg)
![--pooling max](examples/tweaks/swe14_pmax_pcyuv.jpg)

(**left**: original stylized image; **right**: color-preserving style transfer)

## Requirements

### Data Files

* [Pre-trained VGG network][net] (MD5 `8ee3263992981a1d26e73b3ca028a123`) - put it in the top level of this repository, or specify its location using the `--network` option.
