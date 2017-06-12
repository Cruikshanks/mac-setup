# Firefox

I have an entry for [Firefox](https://www.mozilla.org/en-GB/firefox/new/) because I need to install an older version and ensure it does not auto-update in order to support my work on [Quke](https://github.com/DEFRA/quke).

**Quke** is a framework for helping create and run acceptance tests against external sites. It leans heavily on [Selenium web driver](http://www.seleniumhq.org/projects/webdriver/) and [Capybara](https://github.com/teamcapybara/capybara) in order to drive **Firefox**. However the support model changed from version 48 of **firefox**.

It's a bit of a mess and I'm not sure I have it 100% right but my current understanding is

- [Gecko](https://en.wikipedia.org/wiki/Gecko_(software)) is the browser engine **Firefox** uses
- Version 47 of **Firefox** switched to a version of **Gecko** that supported [Electrolysis](https://wiki.mozilla.org/Electrolysis)
- Essentially **Firefox** [went multi-process for the first time](https://arstechnica.co.uk/information-technology/2016/06/firefox-48-electrolysis-download-details/) 
- Though shipped in 47, it was not defaulted to being enabled for all users until version 48 (hence the confusion whether version 47 is in scope)
- It [breaks add-ons](https://developer.mozilla.org/en-US/Add-ons/Working_with_multiprocess_Firefox) which require access to both their own code and the content directly
- [Selenium](https://github.com/SeleniumHQ/selenium) is "an umbrella project encapsulating a variety of tools and libraries enabling web browser automation."
- **Selenium** prior to version 3 uses the [Firefox driver](https://github.com/SeleniumHQ/selenium/wiki/FirefoxDriver)  
- It is an add-on that **Selenium** adds in when you start a test session using **Firefox**
- It is broken by the change to **Firefox**
- It's replacement is [geckodriver](https://github.com/mozilla/geckodriver). This is intended to be a driver for all browsers based on the **Gecko** engine
- It does this via [Marionette](https://developer.mozilla.org/en-US/docs/Mozilla/QA/Marionette) *"an automation driver for Mozilla's Gecko engine. It can remotely control either the UI or the internal JavaScript of a Gecko platform, such as Firefox."*
- At this time however **Marionette** and **Geckodriver** are [not yet feature complete](https://github.com/mozilla/geckodriver#supported-firefoxen). *"This means that they do not yet offer full conformance with the WebDriver standard or complete compatibility with Selenium"*
-  **Quke** is dependent on **Capybara**, whose README states *"If you're using Firefox with selenium-webdriver and want full functionality stay on either Firefox 45.0esr or 47.0.1. [...] Using Firefox 48+ requires geckodriver and selenium-webdriver v3, the combo of which currently has multiple issues and is feature incomplete."*
- Hence this guide covers installing the latest version of **Firefox** that still supports the **Firefox driver**

## Install

- Grab the Mac instance of [version 47.0.1](https://ftp.mozilla.org/pub/firefox/releases/47.0.1/). Direct link: <https://ftp.mozilla.org/pub/firefox/releases/47.0.1/mac/en-GB/Firefox%2047.0.1.dmg>
- Run the installer
- Open the app
- Do not import any settings
- Go to `Preferences -> advanced` and select the `Update`
- Check `Never check for updates`

