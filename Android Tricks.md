# Android Tricks

### How to Open Android Studio from the Terminal

On a Mac, enter the following command to launch an Android Studio project from the terminal. 

```
open -a /Applications/Android\ Studio.app ~/location/ofyour/app
```

bash profile function to open android applications from the command line

```
open_android() {
  if [ $# -eq 0 ]
  then
    open -a /Applications/Android\ Studio.app
    echo "Android Studio opened!"
  else
    open -a /Applications/Android\ Studio.app $1
    echo "$1 was opened in Android Studio!"
  fi
}
```

this will simply open up Android Studio

```
$  open_android
```

Simply type the location of the android app directory after `open_android` to open a specific project in android studio. 

```
$  open_android ~/myprojectlocation
```