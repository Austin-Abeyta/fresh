---
layout: post
title:  "What is RythmGAN?"
date:   2018-09-05 00:00:00
img: RYTHMGAN_RESULTS.jpg
feature-image: "fresh/assets/img/screenshot.jpg"
description: RythmGAN is a program that uses state of the art machine learning algorithms to interpret and recreate music.
---
# RythmGAN
RythmGAN is a program that uses state of the art machine learning algorithms to interpret and recreate drum rhythms. It transforms random numbers into drum patterns, that are complex and of near human quality. These rhythms are generated in a file format called midi. Midi can be played back on almost all computers and edited using any standard music software. My end goal with RythmGAN is to develop a program that uses artificial intelligence to create full song loops that sound as good as, or better than, the results from RythmGAN. My hope is that these midi loops will assist musicians in their creative process by providing templates and complimentary tracks for songs, allowing artists to focus on their instrument of choice or overcome writers block. This project was inspired by Hao-Wen Dong’s project titled MuseGAN, which was aimed at creating music with multiple instrument parts including melody and rhytmn.

RythmGAN uses a machine learning arcitecture called a deep neural network. Artificial neural networks are inspired by the workings of the human brain, and have proven to be very successful in solving very complex problems previously proven difficult to other techniques. Things like speech recognition, and self driving cars are examples of the amazing applications of deep neural networks. RythmGAN uses a Generative Adversarial Network(GAN) to generate it’s samples. These networks were developed by Ian Goodfellow in 2014 and have generated very realistic images. 

![Fake Celebrities]({{site.url}}{{site.baseurl}}/assets/img/imaginary_celebritiespng.png)


Two imaginary celebrites genrated by Nvidia GAN
# Model
A GAN consists of two separate networks, the discriminator, and the generator. Both are in constant competition with each other. The generator generates outputs which are then classified by the discriminator as either real or fake. The generator tries to improve until it can trick the discriminator into thinking the generated ouput is real.  The discriminator gets rewarded when it successfully catches the generator trying to fool it, and the generator gets rewarded when it tricks the discriminator. This competition between the generator and discriminator fuels the models improvement

The generator starts from a collection of random numbers and uses the decisions of the discriminator to improve itself to become more "real". Meanwhile the discriminator is improving by using it’s own error on the correct classification of generated samples. As the discriminator gets better so does the generator and vice versa until the generated data is as close to real as possible. 

<img src = "{{site.url}}{{site.baseurl}}/assets/img/GAN.jpg">
# Training Data
RythmGAN learns from 7 million data points in 17,715 midi files to extract meaningful patterns present in the drums track of songs. The midi files used to train RythmGAN were taken from the Lakhn Pianoroll Dataset. These files were then encoded into a binary array, then passed into a decoder I created that reduced the dimensionality of the samples by 98.6%. Each sample had three elements:
* Number of bars
* Timesteps per bar
* Elements in bar

Most drum loops have only a few elements, I used this to my advantage to simplify the data as much as possible. The elements present were encoded into 7 possible drum parts:
* Closed High hat
* Kick
* Snare
* Open high hat
* Crash
* Tom
* Percussion

Using these 7 elements in a 3d array RythmGAN was able to extract meaningful drum information the most condensed form I imagined possible. It is important to note that as result of it’s simplification, triples are unable to be expressed in my model. 
 
# Results
The results below are unmodified outputs from RythmGAN that have been cherry picked from a batch of outputs for their human like sound. More results, including assisted creativity results can be found by clicking the results tab. 

<iframe width="100%" height="300" scrolling="no" frameborder="no" allow="autoplay" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/498185277&color=%23d9d0ca&auto_play=false&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true&visual=true"></iframe>

For a more in-depth description of the RythmGAN model please check out my technical paper written on it.
