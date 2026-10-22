# गोमत पशु बाजार — Google Play रिलीज़ तैयारी

## तैयार किया गया
- Android ऐप का पैकेज: `com.gomat.pashubazaar`
- Android 16 (API 36): `compileSdk 36`, `targetSdk 36`
- `versionCode 2`, `versionName 1.1`
- GitHub Actions से `:app:bundleRelease` AAB तैयार होता है।
- **बिना सुरक्षित upload key के AAB को जानबूझकर `UNSIGNED-PREVIEW` नाम मिलता है। उसे Play Console पर प्रकाशित न करें।**

## अब आवश्यक निजी कार्य
1. कम-से-कम 18 वर्ष का खाता-मालिक Play Console में खाता सत्यापित करे और लागू शुल्क/शर्तें पूरी करे। 
2. उसी जिम्मेदार खाता-मालिक को सुरक्षित upload keystore बनाकर अपने पास रखना चाहिए। `*.jks` फ़ाइल GitHub रिपॉज़िटरी या सार्वजनिक चैट में न डालें।
3. GitHub रिपॉज़िटरी के **Settings → Secrets and variables → Actions** में चार secrets सुरक्षित रखें:
   - `GOMAT_UPLOAD_KEYSTORE_BASE64`: निजी keystore की base64 सामग्री
   - `GOMAT_KEYSTORE_PASSWORD`: keystore password
   - `GOMAT_KEY_ALIAS`: upload key का alias
   - `GOMAT_KEY_PASSWORD`: upload key का password
4. Secrets जोड़ने के बाद `Play Store release bundle preparation` workflow चलाएँ। तब Artifact का नाम `Gomat-Play-Store-SIGNED-AAB` होगा।
5. Play Console में signed AAB अपलोड कर **Play App Signing** पूरा करें; phone पर AAB सीधे इंस्टॉल नहीं होता।
6. `Privacy Policy` का वास्तविक सार्वजनिक URL, सही `Data safety` घोषणाएँ, सामग्री रेटिंग, सपोर्ट ईमेल, स्क्रीनशॉट, आइकन और स्टोर जानकारी भरें।
7. यदि किसान/व्यापारी खाते बन सकते हैं, तो ऐप और वेबसाइट, दोनों से **खाता और संबंधित डेटा हटाने का अनुरोध** संभव होना चाहिए।
8. यदि ऐप में उपयोगकर्ता के विज्ञापन/फोटो/वीडियो प्रदर्शित होते हैं, तो रिपोर्टिंग, मॉडरेशन और आपत्तिजनक सामग्री रोकने की व्यवस्था जाँचें।
9. आवश्यक खाते के प्रकार के अनुसार बंद परीक्षण पूरा करें; नए personal डेवलपर खातों में आम तौर पर कम-से-कम 12 परीक्षक लगातार 14 दिन आवश्यक हैं।
10. Google के Play review और production approval के बिना ऐप **लाइव प्रकाशित नहीं** माना जाएगा।

## पहले जाँचें
- Samsung सहित असली Android फोन पर लॉगिन, बिक्री विज्ञापन, फोटो/वीडियो चयन, बैक बटन और नेटवर्क त्रुटि पर व्यवहार जाँचें।
- वेबसाइट का लाइव URL https://dev786682.github.io/gomat-pashu-bazaar/ है; ऐप को इंटरनेट चाहिए।
- उपयोगकर्ता डेटा का वास्तविक संग्रहण/साझाकरण जाँचे बिना Data safety में 'कोई डेटा एकत्र नहीं' न लिखें।
- यह रिपॉज़िटरी किसी निजी upload key/password को संग्रहित नहीं करती।
