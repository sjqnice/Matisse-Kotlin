# Matisse

[![](https://jitpack.io/v/sjqnice/Matisse-Kotlin.svg)](https://jitpack.io/#sjqnice/Matisse-Kotlin)

Convert Java to Kotlin

## Usage
Gradle:
```
Step 1.Add it in your root build.gradle at the end of repositories:
allprojects {
    repositories {
        ...
        maven { url 'https://jitpack.io' }
    }
}

Step 2. Add the dependency
dependencies {
    implementation 'com.github.sjqnice:Matisse-Kotlin:1.0.0'
}
```
### picker
```
// pickerLauncher
private val pickerLauncher = registerForActivityResult(StartActivityForResult()) { result ->
    if (RESULT_OK == result.resultCode) {
        val data = result.data
        adapter!!.setData(Matisse.obtainResult(data), Matisse.obtainPathResult(data))
    }
}

Matisse.from(this)
       .choose(MimeType.ofImage())
       // ....
       .forResult(pickerLauncher);
```


### capture
you can directly call capture
```
// captureLauncher
    private val captureLauncher = registerForActivityResult(StartActivityForResult()) { result ->
        if (RESULT_OK == result.resultCode) {
            val data = result.data
            adapter!!.setData(Matisse.obtainResult(data), Matisse.obtainPathResult(data))
        }
    }

Matisse.from(SampleActivity.this)
       .performCapture(new CaptureStrategy(true, "com.zhihu.matisse.sample.kt.fileprovider", "test"), captureLauncher);
```
