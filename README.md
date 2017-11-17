# android-offscreen-opengl-shader

## Description
Small library to apply vertex and fragment shaders to an offscreen image using framebuffer

## Installation
Add it in your root build.gradle at the end of repositories:

```
allprojects {
    repositories {
        jcenter()
        maven { url "https://jitpack.io" }
    }
}
```

Add the dependency
```
dependencies {
	      compile 'com.github.Angtrim:android-offscreen-opengl-shader:-SNAPSHOT'
}
```

## Example

```java
public class RealOffScreenRendering extends AppCompatActivity {
    // Files in assets folder
    private static final String   s_VERT_SHADER_FILE = "shaders/gles30/common/directTexture.vert";
    private static final String   s_FRAG_SHADER_FILE = "shaders/gles30/common/directTexture.frag";


    @Override
    protected void onCreate(@Nullable Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.off);
        OffScreenRenderer offScreenRenderer = new OffScreenRenderer(1080,1920,this);
        Bitmap shaded = offScreenRenderer.getShadedBitmap(R.drawable.myImage,s_VERT_SHADER_FILE,s_FRAG_SHADER_FILE);
        ImageView imageView = (ImageView) findViewById(R.id.image);
        imageView.setImageBitmap(shaded);
    }
    
}
```
