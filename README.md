# ERROR_OPENCV


https://opencv.org/releases/

![image](https://github.com/jose-jhr/ERROR_OPENCV/assets/66834393/d1c5d4fc-6b21-4fb4-8386-52f30017eda9)

Adicionar en error de namespace

```
plugins {
    id 'org.jetbrains.kotlin.android' version '1.7.10'
}
```

![image](https://github.com/jose-jhr/ERROR_OPENCV/assets/66834393/5b9483a4-594c-473e-8b15-9d159071f30b)


en MyApplication/opencv/build.gradle (fix from this):
```

namespace 'org.opencv'
    
buildFeatures{
      aidl true
      buildConfig true
}
```

aidl true: Esto indica que se habilitará el soporte para la interfaz de definición de lenguaje de Android (AIDL). AIDL se utiliza para la comunicación entre procesos en Android y es útil cuando se desarrollan aplicaciones que involucran múltiples componentes o servicios.

buildConfig true: Esta configuración permite generar una clase de configuración durante el proceso de compilación. Esta clase, llamada BuildConfig, contiene valores estáticos que se pueden utilizar para condicionar la compilación de diferentes partes de tu código en función de la configuración de compilación (por ejemplo, si estás compilando para depuración o lanzamiento).

![image](https://github.com/jose-jhr/ERROR_OPENCV/assets/66834393/0cc02394-7131-4ecb-9116-fbe632ee83bb)

``` JAVA
private void starCamera() {
        cameraJhr.addlistenerBitmap(new BitmapResponse() {
            @Override
            public void bitmapReturn(@Nullable Bitmap bitmap) {
                Mat mat = new Mat();
                Utils.bitmapToMat(bitmap,mat);
                Imgproc.cvtColor(mat,mat,Imgproc.COLOR_BGR2GRAY);
                Utils.matToBitmap(mat,bitmap);
                runOnUiThread(new Runnable() {
                    @Override
                    public void run() {
                        imgBitmap.setImageBitmap(bitmap);
                    }
                });
            }
        });
        cameraJhr.initBitmap();
        cameraJhr.start(0,0,previewImg,true,false,true);
    }
```


```Kotlin
    //Implementation CameraJhr
    implementation 'com.github.jose-jhr:Library-CameraX:1.0.8'

    // If you want to additionally use the CameraX View class
    implementation "androidx.camera:camera-view:1.0.0-alpha21"
```

settings.gradle
``` Kotlin
pluginManagement {
    repositories {
        google()
        mavenCentral()
        gradlePluginPortal()
        maven { url 'https://jitpack.io' }
    }
}
dependencyResolutionManagement {
    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
    repositories {
        google()
        mavenCentral()
        maven { url 'https://jitpack.io' }
    }
}
rootProject.name = "VisualControll"
include ':app'
include ':OpenCv'
```
