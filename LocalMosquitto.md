
### Locally deployed mosquitto + JMeter

Driving events into the system with a locally deployed mosquitto running JMeter on the same docker container

<br>

#### Naive approach

Place a water-sensor in the basement and send me a push notification on my smartphone if it detects moisture.<br>

A single sensor might not be enough! <br>

#### [More-is-better](http://www.energy2engage.com/hs-fs/hub/129961/file-296483410-jpeg/images/more_is_better.jpeg?t=1490990984108&width=400&height=300&name=more_is_better.jpeg) approach

Place a couple of water-sensors and notify me ... <br>

More sensors increase the chance of false positives. <br>

#### [Less-is-more](http://68.media.tumblr.com/9f38b8043253a41c401142e573dfa400/tumblr_inline_njlongROsx1szr6tl.jpg) approach  

What about a sequence of events: If sensors are signalling one-by-one ... maybe that is a good indicator for 'water in my basement'<br>

However, there's more ...

[for example, thunderstorms](WaterSensorsWeather.md)


