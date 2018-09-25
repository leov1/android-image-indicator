android-image-indicator
=======================

Android image indicator for advertise and user guide(network image support).  

[ ![Download](https://api.bintray.com/packages/panxw/maven/android-image-indicator/images/download.svg) ](https://bintray.com/panxw/maven/android-image-indicator/_latestVersion)  

## 1.Usage
##### for Maven
	<dependency>
		<groupId>com.panxw.imageindicator</groupId>
		<artifactId>library</artifactId>
		<version>1.0.2/version>
	</dependency>

##### for Gradle
	dependencies {
		compile 'com.panxw.imageindicator:library:1.0.2'
	}

## 2.Sample
####1、Advertise mode(auto play if need)
in layout file：

	<com.panxw.android.imageindicator.ImageIndicatorView
	android:id="@+id/indicate_view"
	android:layout_width="match_parent"
	android:layout_height="160dp" />
        
in java setting：

	imageIndicatorView = (ImageIndicatorView) findViewById(R.id.indicate_view);
	final Integer[] resArray = new Integer[] { R.drawable.ic_launcher, R.drawable.ic_launcher };
	imageIndicatorView.setupLayoutByDrawable(resArray);
	imageIndicatorView.setIndicateStyle(ImageIndicatorView.INDICATE_ARROW_ROUND_STYLE);
	imageIndicatorView.show();

set auto play if need：

	AutoPlayManager autoBrocastManager =  new AutoPlayManager(imageIndicatorView);
	autoBrocastManager.setBroadcastEnable(true);
	autoBrocastManager.setBroadCastTimes(5);//loop times
	autoBrocastManager.setBroadcastTimeIntevel(3 * 1000, 3 * 1000);//set first play time and interval
	autoBrocastManager.loop();

![ScreenShot](https://raw.github.com/panxw/android-image-indicator/master/screenshot/poster0.jpg)

#### 2、User guide mode

	this.imageIndicatorView = (ImageIndicatorView) findViewById(R.id.guide_indicate_view);
	final Integer[] resArray = new Integer[] { R.drawable.ic_launcher, R.drawable.ic_launcher };
	imageIndicatorView.setupLayoutByDrawable(resArray);
	imageIndicatorView.setIndicateStyle(ImageIndicatorView.INDICATE_USERGUIDE_STYLE);
	imageIndicatorView.show();

![ScreenShot](https://raw.github.com/panxw/android-image-indicator/master/screenshot/guider_00.jpg)  
![ScreenShot](https://raw.github.com/panxw/android-image-indicator/master/screenshot/guider_01.jpg)

#### 3、NetworkImageIndicatorView(image from network)
add new class extends from ImageIndicatorView:

    public class NetworkImageIndicatorView extends ImageIndicatorView {
        ...

        public void setupLayoutByImageUrl(List<String> urlList) {
            for(String url: urlList) {
                ImageView imageView = new ImageView(getContext());
                //load image from url and set to imageView, you can use UIL or Volley to do this work
                addViewItem(imageView);
            }
        }

    }

layout file：

	<com.yourapp.view.NetworkImageIndicatorView
	android:id="@+id/network_indicate_view"
	android:layout_width="match_parent"
	android:layout_height="160dp" />

in java setting：

	final List<String> urlList= new ArrayList<String>();
	urlList.add("https://github.com/panxw/android-image-indicator/blob/master/screenshot/guider_00.jpg");
	urlList.add("https://github.com/panxw/android-image-indicator/blob/master/screenshot/guider_01.jpg");
	imageIndicatorView = (ImageIndicatorView) findViewById(R.id.network_indicate_view);
	imageIndicatorView.setupLayoutByImageUrl(urlList);
	imageIndicatorView.show();

set auto play if need：

	AutoPlayManager autoBrocastManager =  new AutoPlayManager(imageIndicatorView);
	autoBrocastManager.setBroadcastEnable(true);
	autoBrocastManager.setBroadCastTimes(5);//loop times
	autoBrocastManager.setBroadcastTimeIntevel(3 * 1000, 3 * 1000);//set first play time and interval
	autoBrocastManager.loop();

## 3.联系作者
Email: winfirm(#)163.com  
QQ交流群: 168563980  


## License

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
