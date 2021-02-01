# Android_Review_1_findViewById
Kotlin means no more findViewById, haha

從小被嫌到大的 findViewById，歷經 ButterKnife 和 Data Binding 的改革，
在Kotlin又更上一層樓，只要 import layout 之後就可以直接用裡面全部的元件，不須任何宣告。


no more dummy code as below:


  
    classNmae: Activity(){
    
        
          var btn: Button ? = null

          override onCreate(){

              val btn = findviewById(R.id.xoxoxox)

          }

   
    }
   
    

1. go to module level build gradle, and then apply the plugins as same as following hightlight top 3 plugins.

  ![](https://raw.githubusercontent.com/QueenieCplusplus/Android_Review_3_app/main/2_module_level.png)


2. code for BFragment class in kotlin.


        package com.katepatty.pk_downloader

        import android.os.Bundle
        import androidx.fragment.app.Fragment
        import android.view.LayoutInflater
        import android.view.View
        import android.view.ViewGroup
        import androidx.navigation.findNavController
        
        // import module
        
        import kotlinx.android.synthetic.main.fragment_b.*


        class BFragment : Fragment() {

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

3. layout for fragment_b.xml

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

4. prepare for before mentioned step (2) & (3)

  * upper object 's layout id

![](https://raw.githubusercontent.com/QueenieCplusplus/Android_Review_1_findViewById/main/obj_1.png)


  * import

![](https://raw.githubusercontent.com/QueenieCplusplus/Android_Review_1_findViewById/main/obj_2.png)

  * layout id

![](https://raw.githubusercontent.com/QueenieCplusplus/Android_Review_1_findViewById/main/obj_3.png)

  * object id

![](https://raw.githubusercontent.com/QueenieCplusplus/Android_Review_1_findViewById/main/obj_4.png)

