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
To reproduce our work, clone the whole repository onto your own local machine. In your terminal, run this code:
```
python neural_style.py --content Pics/Content/boston.jpg --styles Pics/Styles/composition_vii.jpg --iterations 500 --output [your output path and output name]
```
Please make sure you download the pre-trained VGG19 mat model into the 'pretrained_VGG19' folder, and then run above code.

### **Contribution statement**: ([default](doc/a_note_on_contributions.md)) All team members contributed equally in all stages of this project. All team members approve our work presented in this repository including this contributions statement. 


## Requirements

### Data Files

* [Pre-trained VGG network][net] (MD5 `8ee3263992981a1d26e73b3ca028a123`) - put it in the top level of this repository, or specify its location using the `--network` option.
