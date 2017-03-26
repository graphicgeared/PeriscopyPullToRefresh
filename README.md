# PeriscopyPullToRefresh for iOS

Pull-To-Refresh view inspired by Periscope application (written in Swift). It works with UIScrollView and its subclasses.

![](https://raw.github.com/anaglik/PeriscopyPullToRefresh/master/example-pull.gif)

## Usage

Simply create and assign object of PeriscopyTitleView's class as titleView of your current UINavigationItem. 
You can customize font/color of labels presented in that view. Title string is taken from UINavigationItem but you can also assign it directly. 

When you "activate" mechanism, refreshAction block is called.

```swift
override func viewDidLoad() {
    super.viewDidLoad()
    guard let navigationController = self.navigationController else { return }

    let titleView = PeriscopyTitleView(frame: CGRect(x: 0.0, y: 0.0, width: 160.0, height: navigationController.navigationBar.frame.height), attachToScrollView: tableView, refreshAction: {  
	  		//your 'refreshing' code 			  
	})

	//customization
    titleView.titleLabel.textColor = .white
    titleView.releaseLabel.textColor = .white
    titleView.releaseLabel.highlightedTextColor = UIColor(red:207/255.0, green:240/255, blue:158/255, alpha:1.0)

    self.navigationItem.titleView = titleView
}

```
If you would like to use loading animation on UINavigationBar, please use methods from PeriscopyNavBarExtension.swift file.
You don't need to add any png file to your asset catalog, 'stripes' are drawn using CoreGraphics.
Example:

```swift
let view = navigationController.navigationBar.startLoadingAnimation()
//keep reference of 'animating' view
//..
navigationController.navigationBar.stopLoadingAnimationWithView(view)  
```    

Demo app is also included.

## Requirements

Swift 3

## Installation

Just drop PeriscopyTitleView.swift file in your project. If you want to use loading animation on UINavigationBar, please add PeriscopyNavBarExtension.swift file as well.

## Author

Andrzej Naglik, dev.an@icloud.com

## License

PeriscopyPullToRefresh is available under the MIT license. See the LICENSE file for more info.
