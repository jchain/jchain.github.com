---
comments: true
date: 2010-12-06 21:34:32
layout: post
slug: iterative-closest-pointsicp-demo
title: Iterative closest points(ICP) demo
wordpress_id: 41
tags:
- OpenMP
- VTK
---

[youtube=http://www.youtube.com/watch?v=igb8mAJ6F5I]

[caption id="attachment_44" align="alignnone" width="640" caption="Benchmark of Iterative Closest Points with OpenMP"][![](http://zandyware.files.wordpress.com/2010/12/out.png)](http://zandyware.files.wordpress.com/2010/12/out.png)[/caption]

The Perl code generating the plot is listed below

[sourcecode language="perl"]
#!/usr/bin/perl

use strict;
use warnings;
use Chart::Gnuplot;

### Write running time  
open my $IN, '<', "benchmark.dat" or die $!;

# Data
my @x;
my @y;

while( <$IN> ) {
    chomp;
    my ($t1, $t2) = split /\s/;
    push @x, $t1;
    push @y, $t2;
}

# Create chart object and specify the properties of the chart
my $chart = Chart::Gnuplot->new(
    output => "out.eps",
    title  => "Iterative Closest Points with Stanford Bunny",
    xlabel => "Number of threads",
    ylabel => "Time(s)",
    boxwidth => "0.8 relative"
);

# Create dataset object and specify the properties of the dataset
my $dataSet = Chart::Gnuplot::DataSet->new(
    xdata => \@x,
    ydata => \@y,
    title => "Time",
    #style => "linespoints",
    style => "boxes",
    fill => "0.75",
);
 
# Plot the data set on the chart
$chart->plot2d($dataSet);
 
##################################################
 
# Plot many data sets on a single chart
#$chart->plot2d($dataSet1, $dataSet2, ...); 
[/sourcecode]



