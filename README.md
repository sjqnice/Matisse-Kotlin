# Matisse

Convert Java to Kotlin

## Usage
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
