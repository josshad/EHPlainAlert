# EHPlainAlert

This is simple extension for presenting multiple system-wide notifications from bottom of device screen.

<img src="http://josshad.github.io/EHPlainAlert/EHPlainAlert.gif">

## Requirements

- Requires iOS 7.1 or later
- Requires Automatic Reference Counting (ARC)

##Features

- Supports multiple messages on one screen
- Simple use actions
- Highly customizable
- Call from anywhere in app

## Installation

### CocoaPods
To install EHPlainAlert using CocoaPods, please integrate it in your existing Podfile, or create a new Podfile:

```ruby
platform :ios, '7.1'

target 'MyApp' do
  pod 'EHPlainAlert'
end
```
Then run `pod install`.

## Usage

	#import <EHPlainAlert/EHPlainAlert.h>

### Presenting notification

All messages can simply presented via static method call:

	[EHPlainAlert showAlertWithTitle:@"Success" message:@"Something works!" type:EHPlainAlertSuccess];

Messages can be displayed from any location in app, even not associated with UI. 

    [[NetHelper sharedInstance] postRequestWithURLString:URL data:data withSuccess:^(id responseObject) {
            [EHPlainAlert showAlertWithTitle:@"Success" message:@"Data successfully uploaded" type:EHPlainAlertSuccess];
        } failure:^(NSError *error)
        {
            [EHPlainAlert showError:error];
        }];


### Presenting error notification

For simplifying error handling you can use:

	- (void)someError:(NSError *)myError
	{
		[EHPlainAlert showError:error];
	}

### Hiding Messages

Notifications will hidden automatically after 4 seconds. 

To change default delay use static method:
    [EHPlainAlert updateHidingDelay:2.5f];

Also you can just tap on message to hide it.

### On Tap Actions

You can change the default behavior for tapping on the notification:

    EHPlainAlert * ehAlert = [[EHPlainAlert alloc] initWithTitle:@"Hmm..." message:@"Tap for information" type:EHPlainAlertInfo];
    ehAlert.action = ^{
        [[UIApplication sharedApplication] openURL:[NSURL URLWithString:@"https://github.com/josshad/EHPlainAlert"]];
    };
    [ehAlert show];

### Customization

#### Fonts:

Change font of one alert

	EHPlainAlert * ehAlert = [[EHPlainAlert alloc] initWithTitle:@"Info" message:@"This is info message" type:EHPlainAlertInfo];
    ehAlert.titleFont = [UIFont fontWithName:@"TrebuchetMS" size:15];
    ehAlert.subTitleFont = [UIFont fontWithName:@"TrebuchetMS-Italic" size:12];
    [ehAlert show];

Change fonts for alert type

    [EHPlainAlert updateTitleFont:[UIFont fontWithName:@"TrebuchetMS" size:18]];
    [EHPlainAlert updateSubTitleFont:[UIFont fontWithName:@"TrebuchetMS" size:10]];

#### Colors:

Change background color of one alert

	EHPlainAlert * ehAlert = [[EHPlainAlert alloc] initWithTitle:@"Hmm..." message:@"Blue color alert" type:EHPlainAlertInfo];
    ehAlert.messageColor = [UIColor blueColor];
    [ehAlert show];

Change color for alert type

    [EHPlainAlert updateAlertColor:[UIColor colorWithWhite:0 alpha:0.5] forType:EHPlainAlertPanic];

#### Appearance

    [EHPlainAlert updateAlertPosition:ViewAlertPositionTop];

#### Icons:

Change icon of one alert

    EHPlainAlert * ehAlert = [[EHPlainAlert alloc] initWithTitle:@"Hmm..." message:@"Blue color alert" type:EHPlainAlertInfo];
    ehAlert.iconImage = image;
    [ehAlert show];

Change icon for alert type

    [EHPlainAlert updateAlertIcon:image forType:EHPlainAlertInfo]; 

#### Number of messages
    
    [EHPlainAlert updateNumberOfAlerts:4];

#### Display time

    [EHPlainAlert updateHidingDelay:2.5f];

## Author
Danila Gusev

<a href="mailto:jos.shad@gmail.com">jos.shad@gmail.com</a>

## License

Usage is provided under the <a href="http://opensource.org/licenses/MIT" target="_blank">MIT</a> License. See <a href="https://github.com/josshad/EHPlainAlert/blob/master/LICENSE">LICENSE</a> for full details.
