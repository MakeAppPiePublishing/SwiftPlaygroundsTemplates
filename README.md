# Swift Playgrounds Templates

Here's two swift Playgrounds in Xcode format. One's a UIKit and the other SwiftUI Template file to help with setting up Swift Playgrounds. 

In case you are on an iPad and unable to unzip the files, you can cut and paste the cde as well, that I've written below. Just get a blank Xcode template and cut and paste the code.

## SwiftUI Template 

SwiftUI is so easy to do, you'll probably just type it every time like I do. It is a `View` struct and setting the playground page. 

```swift
/// Basic Template for Swift Playgrounds
/// Save to your playgrounds folder and duplicate it.

import SwiftUI

struct ContentView:View{
    var body: some View{
        Text("Hello, Swift Playgrounds!")
    }
}

import PlaygroundSupport
PlaygroundPage.current.setLiveView(ContentView())

```

## UIKit

The UIKit one has a bit more to it. Apple a few years ago began requiring you to add the `loadView` method yourself to add the view to the view controller. it is three things: 
* Instantiate a view
* Set a background color
* Make the ViewController's view your instantiated view

The problem with this is the actual frame size of the view is a bit odd. It isn't the device's size, but sometime will act like an iPhone 8 375x667. I gave you both possibilite in the code. 

For the quickest programmatic layout, I set a Vertical stack view to recieve all views. Change to frames or to auto layout if that is your vibe. 

```swift
/// A simple template for getting started with UIKit in Playgrounds. see the notes in loadview for setting the frame. Save and duplcate this for  ew projects.
/// Steve Lipton https://makeapppie.com

import UIKit


class ViewController:UIViewController{
    override func viewDidLoad() {
        super.viewDidLoad() //Superflous, but I do it anyway. 
        let label = UILabel()
            //I create a quick and dirty vStack to get coding quickly. change this to your favorite way of programmatically handling UIKit. 
        label.text = "Hello Swift Playgrounds"
        label.textAlignment = .center
        let vStack = UIStackView(frame: view.frame)
        vStack.axis = .vertical
        vStack.alignment = .fill
        vStack.distribution = .fill
        view.addSubview(vStack)
        vStack.addArrangedSubview(label)
        
    }
    /// One of the radars I filed. I was just using `viewDidLoad`, and for some reason my playgrounds started crashing suddenly. Apple changed the playgrounds so it requires `loadView` to load the initial view I usually put this boilerplate code in  and go do the rest in `viewDidLoad`. The actual size of the presented view's frame is a little strange. See my course for playgrounds on LinkedIn Learning for the full story.
    
    override func loadView() {
        //let view = UIView(frame: UIScreen.main.bounds)
            //  On an iPad , the following works well. uncomment it and delete the above. 
        let view = UIView(frame: CGRect(x: 0, y: 0, width: 375, height: 667))
        view.backgroundColor = .systemBackground
        self.view = view
    }
}

import PlaygroundSupport
let vc = ViewController()
PlaygroundPage.current.setLiveView(vc)
```swift
