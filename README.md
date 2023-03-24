# admob-adapter

Add the following implementation dependency with the latest version of the adapter in the app-level build.gradle file:

repositories {
    maven {url "https://github.com/Ad4GameTech/admob-adapter/raw/main" }
}

// ...
dependencies {
    implementation fileTree(dir: 'libs', include: ['*.jar'])
    //21+
    implementation 'com.google.android.gms:play-services-ads:21.4.0'
    implementation 'com.reklamup:admanager-adapter:1.0.5'
}
// ...


GDPR Compliance
If you are not using any Consent Management Platform to handle privacy issues and managing user consent with your own solution, you have to inform admob mediation and mediation partners about the consent. The following code snippet is sample for gdpr consent usage for admob mediation. If you already have the snippet like below you need to add all these extras bundles for the reklamup custom event adapter as well.

AdRequest.Builder builder = new AdRequest.Builder();
Bundle extras = new Bundle();
extras.putString("npa", "1");
builder.addNetworkExtrasBundle(AdMobAdapter.class, extras);

// Add this for Reklamup
builder.addNetworkExtrasBundle(type.equals("banner") ? AdmobCustomEventBanner.class :
                type.equals("rewarded") ? AdmobCustomEventRewarded.class :
                        AdmobCustomEventInterstitial.class,
        extras);
