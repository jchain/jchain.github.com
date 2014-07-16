---
comments: true
date: 2012-09-26 02:33:42
layout: post
slug: perl-script-retrieve-current-weather-condition-and-forecast
title: 'Perl script: retrieve current weather condition and forecast'
wordpress_id: 373
categories:
- Perl
tags:
- Perl
---

I'm a little tired of checking out the weather condition via the web browser. In many cases I just
want to see a short report in my terminal. After
reading [http://blogs.perl.org/users/zengargoyle/2012/08/not-to-hot-for-mojo.html](http://blogs.perl.org/users/zengargoyle/2012/08/not-to-hot-for-mojo.html),
which shows how to use Mojolicious to retrieve the current condition and
[http://www.commandlinefu.com/commands/view/4821/get-the-weather-forecast-for-the-next-24-to-48-for-your-location](http://www.commandlinefu.com/commands/view/4821/get-the-weather-forecast-for-the-next-24-to-48-for-your-location.),
which shows how to retried the forecast, I finally wrote something like this

```perl
#!/usr/bin/env perl
#===============================================================================
#
# FILE: weather.pl
#
# USAGE: ./weather.pl
#
# VERSION: 1.0
# CREATED: 09/13/2012 10:31:39 PM
# REVISION: ---
#===============================================================================

use strict;
use warnings;
use feature 'say';

use Mojolicious;

my $ua = Mojo::UserAgent->new;
my $dom = $ua->get('http://w1.weather.gov/xml/current_obs/KCID.xml')->res->dom;
my $temp = $dom->find('temperature_string')->[0]->text;
my $weather = $dom->find('weather')->[0]->text;
say "KCID ", $temp, " ", $weather, "\n";

$dom =
$ua->get('http://api.wunderground.com/auto/wui/geo/ForecastXML/index.xml?query=Cedar%20Rapids')->res->dom;

for my $e ($dom->find('simpleforecast forecastday')->each) {
 my $day = $e->date->day->text;
 my $month = substr $e->date->monthname->text, 0, 3;
 my $weekday = substr $e->date->weekday->text, 0, 3;
 my $condition = $e->conditions->text;
 my $high = $e->high->fahrenheit->text;
 my $low = $e->low->fahrenheit->text;

printf "%s %s %s, Low: %d, High: %d, %s\n", $weekday, $month, $day, $low, $high, $condition;
}
```


This is how it runs from the terminal:

```bash
[zandyware@zandyware] bin $ ./weather.pl
KCID 63.0 F (17.2 C) Fair

Tue Sep 25, Low: 46, High: 81, Clear
Wed Sep 26, Low: 39, High: 70, Clear
Thu Sep 27, Low: 45, High: 70, Clear
Fri Sep 28, Low: 46, High: 70, Partly Cloudy
Sat Sep 29, Low: 45, High: 72, Clear
Sun Sep 30, Low: 41, High: 73, Clear
```
