---
title: "Android ViewModel"
date: 2019-02-06 15:40:00 -0400
---

dependencies {
    implementation 'android.arch.lifecycle:runtime:2.1.0'
    implementation 'android.arch.lifecycle:extensions:2.1.0'
}


xml
<layout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools">

    <data>
        <variable
            name="viewModel"
            type="com.passionvirus.rxandroidsample.viewmodel.LoopViewModel"/>
    </data>
</layout>


viewmodel class
class LoopViewModel : AndroidViewModel {
    val TAG = LoopActivity::class.java.simpleName

    constructor(@NonNull application: Application) : super(application) {
    }
}    

view class
class LoopActivity : AppCompatActivity() {

    private lateinit var binding: ActivityLoopBinding

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        binding = DataBindingUtil.setContentView(this, R.layout.activity_loop)
        binding.viewModel = ViewModelProviders.of(this).get(LoopViewModel::class.java)
    }
}
