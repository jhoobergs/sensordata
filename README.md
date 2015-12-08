# sensordata

This library makes it easy to use the sensors of an Android phone in your native Android project.

## Importing the library
Add the following line to the dependencies in your build.gradle (module: app) :
`compile 'com.cw1a3.sensordata:sensordata:1.0.1'`

Make sure you add the following line to the repositories of the allprojects tag in your build.gradle (Project: ...):
`jcenter()`

## Usage of the library
If you want to use the sensordata inside of an activity, your activity has to extend SensorDataActivity:
`public class MyActivity extends SensorDataActivity {`

In the onCreate function you have to enable the sensors your need:
```
enableAccelerometerSensor();
enableLightSensor();
enableProximitySensor();
enableLocationUpdates(1000, 2000); //Fastest updateInterval and updateInterval
```

!! When using LocationUpdates, you have to make sure you add following line to your Manifest:
`<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />`

To handle the sensordata your have to create a listener (probably in the onCreate):
```
          setSensorDataInterface(new SensorDataInterface() {
            @Override
            public void accelerometerChanged(float x, float y, float z) {
                super.accelerometerChanged(x, y, z);
            }

            @Override
            public void lightChanged(float sv) {
                super.lightChanged(sv);
            }

            @Override
            public void locationChanged(Location newLocation) {
                super.locationChanged(newLocation);
            }

            @Override
            public void proximityChanged(float proximity) {
                super.proximityChanged(proximity);
            }
        });
```

## Supported Sensors
For the moment only 3 sensors and google's location Api are supported:
- Proximity sensor
- Light sensor
- Accelerometer
- Location

## License
Copyright 2015

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
