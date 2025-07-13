
>im aint going through the famous general packages like `flutter_get` and `SharedPrefrences`or `dio`

# ~={purple}here im listing the packages i used in my own Projects that i found usefull=~

---
## Lottie 
package for animations that runs .json animations that can be found on https://lottiefiles.com

---
## Skeletonizer
an package for 'Shimmer effect on any widget ' with alot of settings 

---
## bounce: ^1.0.2
an package usefull for adding the bouncing animation for buttons or any widget in flutter when tapped , also have a lot of custom settings you can adjust to your liking 

---
## iconify_flutter_plus: ^1.0.4
icons library for flutter with alot of icons that can be viewed here https://andronasef.github.io/iconify_flutter/ 

---
##   logger: ^2.5.0
an logger for the debug console that can be customized and made in the main like this 
```
var debug = Logger(
    printer: PrettyPrinter(
  colors: true,
  methodCount: 0,
  errorMethodCount: 3,
  printEmojis: true,
));
```

usefull for debugging and printing in the terminal 

---
##   fancy_shimmer_image: ^2.0.3 
for any image it gives it the shimmer effect with alot of custom settings also can be adjustable 
and work very well with skeletonizer 

---
##   flutter_screenutil: ^5.9.3 
to make the screens adjust to the screen width and height ,, **But** not responsive it takes the width and height and when the screen is rotate or in windows the canvas size changes it dosent change anything 
```
ScreenUtilInit(
    designSize: const Size(430, 932),
    minTextAdapt: true,
    splitScreenMode: true,
    builder: (context, child) {
    //! the APP
```

##   card_swiper: ^3.0.1
card swiper so adjustable and nice 

---
##   animated_theme_switcher: ^2.0.10
gives the telegram Theme change animation ( its little bit laggy)

---
##   motion: ^2.0.1
for making any widget moving with the geyroscope of the device 

---
## flutter_animate: ^4.5.2
animation package from gskinner team , so cool and easy to use

----
##   webview_flutter: ^4.2.2
for opening web tabs inside the flutter application 

---
## flutter_svg: ^2.0.17
package for using svg images dosent pixelize when zoom

---
##   internet_connection_checker_plus: ^2.6.0
package for checking internet connection 

---
##   confetti: ^0.8.0
for blasting colorful cards as an calibration can be customized alot 

---
##   share_plus: any
package for sharing shi with the device share's system 

---
# for chess 
  bishop: ^1.4.4 : Flutter chess engine 
  square_bishop: ^0.3.0 : an Ui compataple with the engine 
    
---
# for maps 
  flutter_map: ^7.0.2
  latlong2: ^0.9.1
  geocoding: ^2.0.4
  ---
# for QR Codes
  qr_flutter: ^4.1.0 : for showing qr codes
  mobile_scanner: ^6.0.10 : for scanning qr codes 
  ---
  