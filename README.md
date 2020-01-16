# AppBarLayoutBugDemo
Bug: can not inflate xml layout with AppBarLayout using xamarin.google.android.material package.
Demo project to repro this issue: https://github.com/xamarin/AndroidSupportComponents/issues/234
1. Add com.google.android.material.AppBarLayout tag in xml layout.
2. Call AppCompatActivity.SetContentView()
3. Enjoy an exception
Android.Views.InflateException: 'Binary XML file line #1 in com.companyname.appbarlayoutbugdemo:layout/activity_main: Binary XML file line #1 in com.companyname.appbarlayoutbugdemo:layout/activity_main: Error inflating class com.google.android.material.AppBarLayout'
  at Java.Interop.JniEnvironment+InstanceMethods.CallNonvirtualVoidMethod (Java.Interop.JniObjectReference instance, Java.Interop.JniObjectReference type, Java.Interop.JniMethodInfo method, Java.Interop.JniArgumentValue* args) [0x0008e] in <e7e2d009b69d4e5f9a00e6ee600b8a8e>:0 
  at Java.Interop.JniPeerMembers+JniInstanceMethods.InvokeVirtualVoidMethod (System.String encodedMember, Java.Interop.IJavaPeerable self, Java.Interop.JniArgumentValue* parameters) [0x0005d] in <e7e2d009b69d4e5f9a00e6ee600b8a8e>:0 
  at Android.App.Activity.SetContentView (System.Int32 layoutResID) [0x00022] in <d706cf8faf5542949900cf6d57864528>:0 
  at AppBarLayoutBugDemo.MainActivity.OnCreate (Android.OS.Bundle savedInstanceState) [0x00009] in C:\Projects\AppBarLayoutBugDemo\AppBarLayoutBugDemo\MainActivity.cs:14 
  at Android.App.Activity.n_OnCreate_Landroid_os_Bundle_ (System.IntPtr jnienv, System.IntPtr native__this, System.IntPtr native_savedInstanceState) [0x00011] in <d706cf8faf5542949900cf6d57864528>:0 
  at (wrapper dynamic-method) Android.Runtime.DynamicMethodNameCounter.3(intptr,intptr,intptr)
  --- End of managed Android.Views.InflateException stack trace ---
android.view.InflateException: Binary XML file line #1 in com.companyname.appbarlayoutbugdemo:layout/activity_main: Binary XML file line #1 in com.companyname.appbarlayoutbugdemo:layout/activity_main: Error inflating class com.google.android.material.AppBarLayout
Caused by: android.view.InflateException: Binary XML file line #1 in com.companyname.appbarlayoutbugdemo:layout/activity_main: Error inflating class com.google.android.material.AppBarLayout
Caused by: java.lang.ClassNotFoundException: com.google.android.material.AppBarLayout
	at java.lang.Class.classForName(Native Method)
	at java.lang.Class.forName(Class.java:454)
	at android.view.LayoutInflater.createView(LayoutInflater.java:815)
	at android.view.LayoutInflater.createViewFromTag(LayoutInflater.java:1006)
	at android.view.LayoutInflater.createViewFromTag(LayoutInflater.java:961)
	at android.view.LayoutInflater.rInflate(LayoutInflater.java:1123)
	at android.view.LayoutInflater.rInflateChildren(LayoutInflater.java:1084)
	at android.view.LayoutInflater.inflate(LayoutInflater.java:682)
	at android.view.LayoutInflater.inflate(LayoutInflater.java:534)
	at android.view.LayoutInflater.inflate(LayoutInflater.java:481)
	at androidx.appcompat.app.AppCompatDelegateImpl.setContentView(AppCompatDelegateImpl.java:555)
	at androidx.appcompat.app.AppCompatActivity.setContentView(AppCompatActivity.java:161)
	at crc6411d0a0c8bf8511ef.MainActivity.n_onCreate(Native Method)
	at crc6411d0a0c8bf8511ef.MainActivity.onCreate(MainActivity.java:37)
	at android.app.Activity.performCreate(Activity.java:7802)
	at android.app.Activity.performCreate(Activity.java:7791)
	at android.app.Instrumentation.callActivityOnCreate(Instrumentation.java:1299)
	at android.app.ActivityThread.performLaunchActivity(ActivityThread.java:3245)
	at android.app.ActivityThread.handleLaunchActivity(ActivityThread.java:3409)
	at android.app.servertransaction.LaunchActivityItem.execute(LaunchActivityItem.java:83)
	at android.app.servertransaction.TransactionExecutor.executeCallbacks(TransactionExecutor.java:135)
	at android.app.servertransaction.TransactionExecutor.execute(TransactionExecutor.java:95)
	at android.app.ActivityThread$H.handleMessage(ActivityThread.java:2016)
	at android.os.Handler.dispatchMessage(Handler.java:107)
	at android.os.Looper.loop(Looper.java:214)
	at android.app.ActivityThread.main(ActivityThread.java:7356)
	at java.lang.reflect.Method.invoke(Native Method)
	at com.android.internal.os.RuntimeInit$MethodAndArgsCaller.run(RuntimeInit.java:492)
	at com.android.internal.os.ZygoteInit.main(ZygoteInit.java:930)
Caused by: java.lang.ClassNotFoundException: Didn't find class "com.google.android.material.AppBarLayout" on path: DexPathList[[zip file "/data/app/com.companyname.appbarlayoutbugdemo-sJrJulG2TvzUwzP7t8eazA==/base.apk"],nativeLibraryDirectories=[/data/app/com.companyname.appbarlayoutbugdemo-sJrJulG2TvzUwzP7t8eazA==/lib/x86_64, /data/app/com.companyname.appbarlayoutbugdemo-sJrJulG2TvzUwzP7t8eazA==/base.apk!/lib/x86_64, /system/lib64, /system/product/lib64]]
	at dalvik.system.BaseDexClassLoader.findClass(BaseDexClassLoader.java:196)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:379)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:312)
	... 29 more

