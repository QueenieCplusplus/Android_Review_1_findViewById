# Android_Review_1_findViewById
Kotlin means no more findViewById, haha

從小被嫌到大的 findViewById，歷經 ButterKnife 和 Data Binding 的改革，
在Kotlin又更上一層樓，只要 import layout 之後就可以直接用裡面全部的元件，不須任何宣告。

1. code




        package com.katepatty.pk_downloader

        import android.os.Bundle
        import androidx.fragment.app.Fragment
        import android.view.LayoutInflater
        import android.view.View
        import android.view.ViewGroup
        import androidx.navigation.findNavController
        
        // import module
        
        import kotlinx.android.synthetic.main.fragment_a.*


        class AFragment : Fragment() {

            // kotlin 元件免宣告定義
            //var btn: Button? = null

            override fun onCreateView(
                inflater: LayoutInflater, container: ViewGroup?,
                savedInstanceState: Bundle?
            ): View? {
                // Inflate the layout for this fragment
                return inflater.inflate(R.layout.fragment_a, container, false)

                // no more findviewbyid in Kotlin
                //btn = (Button) findViewById(R.id.navigate_btn);

            }
            override fun onViewCreated(view: View, savedInstanceState: Bundle?) {
                super.onViewCreated(view, savedInstanceState)

                // add this code to do a action-trigger
                //val navController = findNavController(MainActivity, R.id.AFragment)
                //val navHostFragment = supportFragmentManager.findFragmentById(R.id.AFragment) as NavHostFragment
                //val navController = navHostFragment.navController

                //btn!!.setOnClickListener { navController.navigate(R.id.action_AFragment_to_BFragment) }

                                       // this id can be both of the dest-fragment id or action id
                // call btn id directly                       
                navigate_btn!!.setOnClickListener {it.findNavController().navigate(R.id.BFragment)}

            }

        }

2. layout

                        <?xml version="1.0" encoding="utf-8"?>
                        
                        <FrameLayout
                            xmlns:android="http://schemas.android.com/apk/res/android"
                            android:layout_width="match_parent"
                            android:layout_height="match_parent">


                            <ImageButton
                                android:layout_width="wrap_content"
                                android:layout_height="wrap_content"
                                android:src="@drawable/circle"/>

                            <Button
                                android:id="@+id/navigate_btn"
                                android:layout_width="wrap_content"
                                android:layout_height="wrap_content"
                                android:layout_gravity="center_horizontal"
                                android:text="go to => 2" />

                            <TextView
                                android:id="@+id/content_text"
                                android:layout_width="wrap_content"
                                android:layout_height="wrap_content"
                                android:layout_gravity="center"
                                android:text="Welcome to Kate ＆ Pattys Image Castle" />


                        </FrameLayout>

3. prepare for before mentioned step (1) & (2)

  * upper object 's layout id

![](https://raw.githubusercontent.com/QueenieCplusplus/Android_Review_1_findViewById/main/obj_1.png)

![](https://raw.githubusercontent.com/QueenieCplusplus/Android_Review_1_findViewById/main/obj_2.png)

![](https://raw.githubusercontent.com/QueenieCplusplus/Android_Review_1_findViewById/main/obj_3.png)

![](https://raw.githubusercontent.com/QueenieCplusplus/Android_Review_1_findViewById/main/obj_4.png)

