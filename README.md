This method (used first by tunip3) allows apps to be installed to an Xbox in retail mode that would normally only be available in dev mode.
I think I have fixed the issues with the guide.  If you do run into a problem, feel free to create an issue.  You could also fork the guide and submit a pull request.

## Guide to Installing Apps to an Xbox in Retail Mode

### Table of Contents
* [Introduction](#introduction)

* [Requirements](#requirements)

* [Step 1: Sign up for a developer account](#step-1-sign-up-for-a-developer-account)

* [Step 2: Create an application in Microsoft Partner Center](#step-2-create-an-application-in-microsoft-partner-center)
    
    * [Step 2.1: Enter availability settings](#step-21-enter-availability-settings)
    
    * [Step 2.2: Enter properties settings](#step-22-enter-properties-settings)
    
    * [Step 2.3: Enter age ratings settings](#step-23-enter-age-ratings-settings)
    
    * [Step 2.4: Enter store listing settings](#step-24-enter-store-listing-settings)

* [Step 3: Prepare the application's package for upload](#step-3-prepare-the-applications-package-for-upload)

* [Step 4: Upload the application to the Microsoft Store](#step-4-upload-the-application-to-the-microsoft-store)

* [Step 5: Create a website that links to the app](#step-5-create-a-website-that-links-to-the-app)

* [Step 6: Install the app to your Xbox in retail mode](#step-6-install-the-app-to-your-xbox-in-retail-mode)

### Introduction

This guide will describe the process of uploading a Universal Windows Platform (UWP) app to the Microsoft Store for use on an Xbox in retail mode.  Apps that you install to your Xbox in this way will not need to be sideloaded in dev mode.  This is useful for several reasons: allowing use of Xbox remote play, avoiding having to restart the Xbox, and bypassing the 2 GB file size limit imposed on dev mode.  Currently, only apps for which the source code is freely available can be installed in this way to retail mode.

There are some things you should be aware of if you choose to follow this guide.  Installing emulation apps to an Xbox in retail mode is against Microsoft’s terms of service.  For example, it is possible to install RetroArch and PPSSPP to an Xbox in retail mode.  The consequences of breaking these terms of service, if any, are unknown.  In addition, you will need to pay $20 in order to acquire a developer account from Microsoft.  If you can currently sideload apps in dev mode, you have already paid and you don’t need to pay again.  For the purposes of this guide, an FTP app will be uploaded for use in retail mode.

To summarize what must be done, you must first create a template for an app on Microsoft Partner Center (used for releasing UWP apps to the Microsoft Store), indicate that the app will only be available to a private audience (so that it doesn’t need to pass certification), add your email address to that private audience, associate the app’s source code with the project you created in Partner Center, generate a package that can be uploaded to Partner Center, upload the package to Partner Center, submit the Partner Center project to Microsoft, create a website with a link to your app’s Microsoft Store page, and then click on that link using your Xbox’s Edge browser.

### Requirements

To follow this guide, you will need $20 (unless you already have a Microsoft developer account), a computer running Windows, git, and Visual Studio 2017 or 2019.  The installation of Visual Studio and git is not within the scope of this guide.

### Step 1: Sign up for a developer account

If you have a Microsoft account that you log into on your Xbox and $20, you have everything you need to complete this step.  If you have a developer account already, skip this step.

**1.**  Go to this URL (https://developer.microsoft.com/en-us/store/register/) and click on the “sign up” button.

**2.**  If you are not already signed in with your Xbox’s Microsoft account, sign in using the prompt displayed.

**3.**  On the next page, select the “individual” account type option.
![AccountType](https://i.imgur.com/3M84Ydq.png "Sign up for an individual account")

**4.**  Scroll down to the “publisher display name (company name)” textbox and enter your desired publisher name.  This can be anything as long as it hasn’t already been claimed by someone else.

**5.**  Scroll down and fill in the “contact info” textboxes.  Then, press the “next” button at the bottom of the page.

**6.**  On the next page, click on “add a new payment method.”

**7.**  Enter your payment information, go to the Review page, and complete the purchase.  You now have a Microsoft developer account.

### Step 2: Create an application in Microsoft Partner Center

Now we will use the Partner Center to create an app that you can submit to your own private Microsoft Store.  This will be the bulk of the required work.

#### Step 2.1: Enter availability settings

**1.**  Navigate to this URL (https://partner.microsoft.com/overview).

**2.**  Press the "create a new app" button.

**3.**  Enter an app name into the "name" field and click on the "reserve product name" button.  Like the publisher name, your app's name can be anything that has not already been reserved.

**4.**  The application overview page is now displayed.  Click on the "start your submission" button.

**5.**  All these sections will need to be completed in order to create your app.  Click on the "pricing and availability" link first.

![availability](https://i.imgur.com/x6ke1zS.png "Click on the topmost link")

**6.**  In the visibility section of the next page, click on the "private audience" radio button, and then click on the "create a new group" link.

**7.**  Enter anything you desire in the "group name" textbox, and then enter your email address into the bottom textbox.

**8.**  Click on the "save" button.

**9.**  First, place your cursor on the symbol with three squares on the left-hand portion of the page.  Then, click on the name of your app.

![return](https://i.imgur.com/hdQBnNN.png "Return to the product overview page")

**10.**  Click on the "submission 1" link under the "submissions" heading.

**11.**  Click on the "pricing and availability" link again.

**12.**  Select "private audience" again in the visibility section.

**13.**  Click on the checkbox for the customer group that you just created.

![customers](https://i.imgur.com/gIQLTjb.png "click on the checkbox")

**14.**  Scroll down to the discoverability section and click on the radio button for "make this product available but not discoverable in the Microsoft Store."

**15.**  Make sure the "direct link only" radio button is also selected.

![directlink](https://i.imgur.com/ui18qor.png "make sure the app is for a private audience")

**16.** Scroll down to the pricing section and choose "free" in the base price dropdown list.

**17.** Scroll all the way down and click on the "save draft" button.

#### Step 2.2: Enter properties settings

**1.**  Click on the "properties" link.

![properties](https://i.imgur.com/qXiNnAi.png "fill out the properties section")

**2.**  In the topmost dropdown list, select "games" for the category.

**3.**  Click on the checkbox for any genre.

**4.**  Click on the "yes" button for the privacy policy section and enter a valid URL.

![policy](https://i.imgur.com/mQFNZDZ.png "select the appropriate radio button for your app")

**5.**  Scroll down to the display mode section and click on both Xbox checkboxes.

![display](https://i.imgur.com/AgcQQQD.png "display mode checkboxes")

**6.**  No further input is required.  Scroll all the way down and click on the "save" button.

#### Step 2.3: Enter age ratings settings

**1.** Click on the "age ratings" link

![ageratings](https://i.imgur.com/Fmop4y7.png "age ratings")

**2.**  Go ahead and select the radio buttons that best describe your app.  Nothing specific is required here except for the last question.

**3.**  Scroll down and select the "no" radio button for the final question.

![ratingsboard](https://i.imgur.com/x6LI0ra.png "select no here")

**4.**  Click on the "save" button.

#### Step 2.4: Enter store listing settings

**1.**  Click on the "add/remove languages" link in the store listings section.

![addlanguage](https://i.imgur.com/ZU4PQXd.png "add a language")

**2.**  Type "English" into the first textbox and press the enter key.

**3.**  A new window is displayed.  Type "English" into the textbox and click on the "English" checkbox.

![languages](https://i.imgur.com/c6auYZU.png "select the appropriate language")

**4.**  Click on the "update" button.

**5.**  Click on the "save" button at the bottom of the screen.

**6.**  Click on the "English" link that is now displayed in the store listings section.

![englishlink](https://i.imgur.com/Ric7fBT.png"click on the language link")

**7.**  Enter the app's description into the required "description" textbox.

**8.**  Scroll down to the screenshots section.  Click on the "Xbox" option.  You will now need to upload at least one .png screenshot with dimensions between 1920x1080 and 3840x2160.

**9.**  Once you have found a suitable image, click on the plus button and upload it.

**10.**  You will also need to upload a store logo image, in the section below the screenshots, with dimensions between 720x1080 and 1440x2160.

**11.**  Once the uploads are complete, no further input is required for this page.  Scroll down and click the "save" button at the bottom of the page.

### Step 3: Prepare the application's package for upload

We will now need to generate a .msixupload or .appxupload file for submission to the Microsoft Store.  This step will involve git and Visual Studio.

**1.**  Enter "cmd" in the Windows search bar and click on the first search result.

**2.**  Using the "cd" command, navigate to the folder that will hold the app's source code.

**3.**  Enter the following into cmd.exe and press the enter key.  Replace the URL I am using with the URL that links to your app's source code.

`git clone --recursive https://github.com/Nun-z/UniversalFtpServer.git`

For RetroArch, use this:

`git clone --recursive https://github.com/libretro/RetroArch.git`

**4.**  Double-click on the resulting .sln file that corresponds to your app.  If the source code has multiple .sln files, make sure to click on the one that is specifically intended for generating a UWP package.

**5.**  For RetroArch, you will need the .sln file in the RetroArch/pkg/msvc-uwp/ directory.

**6.**  For RetroArch, download the cores here (http://www.mediafire.com/file/f0yfmx33x3f0pin/RetroArch_Cores.rar/file) and place them in the RetroArch/pkg/msvc-uwp/RetroArch-msvc2017-UWP/cores/x64/cores/ directory.

**7.**  For RetroArch, download the other .dll files here (https://buildbot.libretro.com/nightly/windows/x86_64/RetroArch_update.7z) and place them in the RetroArch/pkg/msvc-uwp/RetroArch-msvc2017-UWP/cores/x64/ directory.

**8.**  Visual Studio will launch.  Click on the "sign in" button at the top-right of the screen.

![VSsignin](https://i.imgur.com/nHCZj2L.png "click on the sign-in button")

**9.**  Log in with the Microsoft account that is linked to your Xbox.

**10.**  For RetroArch, expand the project in the right-hand solution window.

**11.**  Right-click on "references" in the solution window.

**12.**  Click on the "add references."

**13.**  Click on the "extensions."

**14.**  Click the checkboxes for "Microsoft Visual C++ Runtime Package for Windows Universal," "Visual C++ 2013 UWP Desktop Runtime," and "Visual C++ 2015 UWP Desktop Runtime," and then click on the ok button.

**15.**  Right-click on the UWP project in the Solution Explorer, place the mouse over the "publish" option, and then click on "associate app with the store."

![associate](https://i.imgur.com/bu80QeO.png "Associate the source code with your app")

**16.**  Press the "next" button, click on the name of your app, and then click on the "next" button again.

**17.**  Click on the "associate" button.  The window will close.

**18.**  For RetroArch, select the ReleaseANGLE and x64 configurations.

![configurations](https://i.imgur.com/gSoVFYM.png "choose the correct configurations")

**19.**  Right-click on the UWP project in the Solution Explorer, place the mouse over the "publish" option, and then click on "create app packages."

![createpackage](https://i.imgur.com/tiD1dn0.png "create the package")

**20.**  Click on the topmost radio button next to the text containing your app's name.  Then, click on the "next" button.

**21.**  Click on the checkbox for "automatically increment" and uncheck all checkboxes that are not related to the x64 configuration.

**22.**  Uncheck the checkbox for "generate artifacts to validate..."

![makepackagefile](https://i.imgur.com/c4IVMaF.png "select package options")

**23.**  Click on the "create" button.

**24.**  Click on the "output location" link.

![linktopackage](https://i.imgur.com/kEVgRFW.png "open the package destination")

### Step 4: Upload the application to the Microsoft Store

Now that we have generated the package, we need to upload it to our private Microsoft Store.

**1.**  Navigate to the Partner Center (https://partner.microsoft.com/en-us/dashboard/windows/overview).

**2.**  Click on the "continue submission" button for your app.

**3.**  Click on the "packages" link.

![packagessection](https://i.imgur.com/Wx8RlS6.png "go to the packages section")

**4.**  Drag the .appxupload or .msixupload file into the packages section.

![uploadfile](https://i.imgur.com/lhf3CIp.png "add the package file to the app")

**5.**  Select the "Windows 10 desktop" and "Windows 10 Xbox" checkboxes in the device family availability section.

**6.**  Scroll all the way down and click on the "save" button.

**7.**  Remove any languages in the store listings section that you don't want to include in your app.

**8.**  Click on the "Xbox Live creator's program" link.

![XboxLive](https://i.imgur.com/xyK5RK2.png "enter the xbox live program")

**8.**  Click on the "enable" button on the top-right of the page.

**9.**  Click on the "confirm" button.

**10.**  Scroll all the way down and click on the "test" button.

**11.**  Once "success" is displayed, return to the app overview page.

**12.**  Scroll down and click on the "submit to the store" button.

![submit](https://i.imgur.com/Ajj1Nrz.png "submit to the store")

**13.**  Scroll all the way down and click on the "save" button.

**14.**  If necessary, click on the "submit to the store" button again.

**15.**  The app has now been submitted to the store.  Wait to receive an email indicating that the app was published.

### Step 5: Create a website that links to the app

Once the app has been published, it is time to create a website that will link to your app in the Microsoft Store.  This step is required in order to get the app onto your Xbox in retail mode.  I will not detail this process extensively, but I will say what the website must contain.

**1.**  Return to the Partner Center (https://partner.microsoft.com/en-us/dashboard/home) and go to your app's overview page.

**2.**  Click on "product management" and then on "product identity."

![identity](https://i.imgur.com/o6M3ktF.png "go to the product identity pge")

**3.**  Scroll down and write down the URL labeled as "URL if your app is only visible to certain people (requires authentication)."

![URL](https://i.imgur.com/EgdIQw3.png "copy down the URL")

**4.**  Create a new text file with the following contents and save it as index.html.

```
<HTML>
    <BODY>
         <p>
            <a href="ms-windows-store://pdp/?productid=##">App Name</a>
         </p>
    </BODY>
</HTML>
```

**5.**  Replace the "##" characters in the above file with the product ID from your URL.  It should look something like this:

```
 <a href="ms-windows-store://pdp/?productid=9NC9ZRXZWPXS">App Name</a>
```

**6.**  You will now need to host the index.html file.  One common choice for creating websites like these is github.io (https://pages.github.com/).

### Step 6: Install the app to your Xbox in retail mode

**1.**  Turn on your Xbox and open the Edge app.

**2.**  Navigate to the URL of your website.

**3.**  Click on the link you created for your app.

**4.**  The Microsoft Store will launch.  Select the install button to add your app to your Xbox in retail mode.
