# KivMob-Error-AttributeError-AndroidBridge-object-has-no-attribute-_interstitial-

Hello All! I've created this repository to share with you solution to problem with KivMob. When you follow<br />
the KivMob instruction you can end up with error :  AttributeError: 'AndroidBridge' object has no attribute '_interstitial'.<br />
There not much information about that on the internet. But there was some one guy, that created a great solution to this. But unfortunely<br />
it is all in Japanese. Here the link : https://vucavucalife.com/kivy-trials-and-tribulations-of-integrating-admob-ads-into-an-android-app/ .<br />

I do not know any of Japanese, but i used translator and try a few things. It worked. So now i introduce to you, solution, CREATED by this great <br />
guy from Japan. If you ever gonna see this. Thank you so much, for such a great job. And the last thing. Everything i will write here it is not my code.<br />
This code belong to the author of article above. Thank you once again!<br />

So basically there are some changes made in com.google.firebase:firebase-ads:21.4.0 . Since that, names of Classes in Java are changed. And that is why <br />
vucavucalife made a great job, because he changed the code accordingly to the newest firebase. Here is what you need to do.<br />

Create a folder called "src" in your location when the main.py and main.kv belongs. Put there two java files. InterstitialAdLoadCallback4kivy.java <br />
and RewardedAdLoadCallback4kivy.java. Next copy kivmob_mod.py to folder with main.py and main.kv. Then, make some changes to your buildozer.spec file :<br />

>source.exclude_dirs = tests, bin, venv, .gitignore, .DS_Store, .idea, .git<br />
requirements = python3,kivy,android,jnius <br />
android.permissions = INTERNET, ACCESS_NETWORK_STATE<br />
android.api = 33<br />
android.minapi = 21<br />
android.sdk = 33<br />
android.ndk = 25b<br />
android.add_src = ./src #### This a folder with modified java files<br />
android.gradle_dependencies = com.google.firebase:firebase-ads:21.4.0, androidx.appcompat:appcompat:1.6.1, androidx.activity:activity:1.6.1 <br />
android.enable_androidx = True<br />
android.meta_data = com.google.android.gms.ads.APPLICATION_ID=ca-app-pub-3940256099942544~3347511713<br />
android.archs = arm64-v8a, armeabi-v7a<br />
android.allow_backup = True<br />
p4a.branch = master<br />

And last to do : buildozer -v android debug<br />

GOOD LUCK!<br />
