

#Ads #AdMob

To integrate <b> AdMob </b> in a Unity Project, follow these full steps. AdMob is Google's mobile Advertising platform, and it can be used to display ads in your Unity mobile game or app. 

## 1. Set up an AdMob Account 

First, ensure that you have a valid AdMob account.
 1. Go to #Admob and sign in or create an account if you don't have 
 2.  Create a new AdMob app. Afterward, you'll get an App ID for the app and Ad Unity Ids for various ad types ( like banner, interstitial, and rewarded ads).
## 2. Create Your Unity Project

if you don't already have a unity project, create a new one.
1. Open unity and create a new project.
2. Ensure you're building for the correct platform ( Android or iOS).
## 3. Set Up Unity for Mobile Development
Ensure Unity is properly set up for mobile development.
1. Go to Edit > Project Setting.
2. In player, choose your target platform : Android or iOS.
3. Ensure you have the necessary build tools installed:
	1.  For Android, make sure you have the Android Build Support and JDK installed.
	2. For iOS, ensure you have the correct version of Xcode.
## 4. Import the Google Mobile Ads SDK into Unity
AdMob requires the Google Mobile Ads SDK for unity. here's how to import it :

1. Go to the Google Admob Unity SDK GitHub page or download the unity package directly from the Google developers site.
2.  Open Unity and go to Assets > Import package > Custom Package.
3. Select the downloaded `.unitypackage` file and click Open.
4. Unity will ask you to import the necessary assets. click Import.
## 5. Configure Google Mobile Ads in Unity

For Android. 
1. Set your AdMob App ID in Unity:
	-  Go to Edit > project Setting  > Player.
	- Select Android and scroll Down to other settings. 
	- Add your AdMob App ID in the Bundle  Identifier under Advertising Indentifier. ( Format ` ca-app-pub-XXXXXXXXX~YYYYYYY`).
2. Enable Internet Permission ( Android only):
	-  Go to Assets > plugin > Android.
	- open the `AndroidManifest.xml` and ensure that the INTERNET and ACCESS_NETWORK_STATE permission are declared.
## 6. Write Scripts to Display Ads

Create scripts to display ads. Here is an example of a script to show a Banner Ad, Interstitial Ad, and Rewarded Ad.

```Csharp 
using GoogleMobileAds.Api;
using UnityEngine ;

public class Admanager : MonoBehaviour
{
	private BannerView bannerView;
	private InterstitialAd interstitial;
	private RewardedAd rewardedAd;

	// replace with Ad Unit ID

	private string adUnitId = " ca-app-pub-XXXXXXX/XXXXXXXXX";

	private void Start()
	{
		MobileAds.Initialize(initStatus => {});

		// Load Banner Ad
		RequestBanner();

		// Load Interstitial Ad
		RequestInterstitial();

		// Load Rewarded Ad
		RequestRewardedAd();
	}

	// Banner Ad
	private void RequestBanner()
	{
		bannerView = new BannerView( adUnitId, adSize.Banner , Adposition.Bottom);
		AdRequest request = new AdRequest();
		bannerView.LoadAd(request);
		banerView.Show();
	}
	// Interstitial Ad
	private void RequestInterstitial()
	{
		interstitial = new InterstitialAd(adUnitId);
		AdRequest request = new Adrequest();
		interstitial.LoadAd(request);
	}
	// Rewarded Ad 
	private void RequestRewardedAd()
	
	{
		rewardedAd = new RewardedAd(adUnitId);
		rewardedAd.OnAdClosed += HandleOnAdClosed;
		Adrequest request = new Adrequest();
		rewardedAd.LoadAd(request);
	}
public void ShowInterstitial()
{
	if(interstital.IsLoaded())
	{
		interstital.Show();
	}
}
public void ShowRewardedAd()
{
	if(rewarded.IsLoaded())
	{
		rewardedAd.Show();
	}
}
private void HandleOnAdCloase( object sender , System.EventArgs e)
{
	RequestRewardedAd(); 
	// PreLoad the next rewarded ad 
}

}
```

