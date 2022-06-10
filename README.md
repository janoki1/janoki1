- 👋 Hi, I’m @janoki1
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
janoki1/janoki1 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
Permission in manifest
<uses-permission android:name="android.permission.CALL_PHONE"></uses-permission>
Execute a phone call
Intent intent = new Intent(Intent.ACTION_CALL);
intent.setData(Uri.parse("tel:+436641234567"));
startActivity(intent);
Call a contact
Intent intent = new Intent(Intent.ACTION_CALL);
intent.setData(Uri.parse("content://contacts/people/"+contact_id));
startActivity(intent);
Display the dialer with a number
Intent intent = new Intent(Intent.ACTION_DIAL);
intent.setData(Uri.parse("tel:+436641234567"));
startActivity(intent);
Listen to incoming/outgoing phone calls
Permission in manifest file
<uses-permission android:name="android.permission.READ_PHONE_STATE">
   </uses-permission>
Extend the phone state listener
class MyPhoneStateListener extends PhoneStateListener{
          public void onCallStateChanged(int state, String incomingNumber){
                   super.onCallStateChanged(state, incomingNumber);
                   switch (state){
                             case TelephonyManager.CALL_STATE_IDLE:
                                      //phone in idle state
                                      break;
                             case TelephonyManager.CALL_STATE_OFFHOOK:
                                      //phone in offhook state
                                      break;
                             case TelephonyManager.CALL_STATE_RINGING:
                                      //phone is ringing
                                      break;
                             default:
                                      break;
                   }
          }
}
Register the listener
TelephonyManager mTelephonyMgr = (TelephonyManager)getSystemService(Context.TELEPHONY_SERVICE);
mTelephonyMgr.listen(new MyPhoneStateListener(), PhoneStateListenermedia.LISTEN_CALL_STATE);

 
 
