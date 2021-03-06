# DPSlideMenuKit-Swift
simple slide menu kit with different colors

[![Cocoapods](https://img.shields.io/cocoapods/v/DPSlideMenuKit.svg)](http://cocoapods.org/?q=DPSlideMenuKit)
[![Pod License](http://img.shields.io/cocoapods/l/DPSlideMenuKit.svg)](https://github.com/HongliYu/DPSlideMenuKit-Swift/blob/master/LICENSE)

![screenshot](https://github.com/HongliYu/DPSlideMenuKit-Swift/blob/master/DPSlideMenuKit.gif?raw=true)

# Usage

```  swift
  override func viewDidLoad() {
    super.viewDidLoad()
    
    // 1. get the drawer
    // embed in storyboard
    var drawer: DPDrawerViewController?
    self.childViewControllers.forEach { (viewController) in
      if viewController is DPDrawerViewController {
        drawer = viewController as? DPDrawerViewController
      }
    }
    // not embed in storyboard? add it manually
    // let drawer: DPDrawerViewController? = self.storyboard?.instantiateViewController(withIdentifier: "DPDrawerViewController") as? DPDrawerViewController
    //  self.addChildViewController(drawer!)
    //  self.view.addSubview(drawer!.view)
    
    // 2. create the first view controller
    let homeViewController: DPHomeViewController? = self.storyboard?.instantiateViewController(withIdentifier: "DPHomeViewController") as? DPHomeViewController
    
    // 3. create DPSlideMenuModel for every view controller
    let slideMenuModelProjects: DPSlideMenuModel = DPSlideMenuModel(
      color: UIColor(colorLiteralRed: 237.0 / 255.0, green: 140.0 / 255.0,
                     blue: 52.0 / 255.0,
                     alpha: 1.0),
      controllerClassName: "DPHomeViewController",
      title: "Projects",
      cellHeight: 108.0,
      actionBlock: nil)
    let slideMenuModelSupport: DPSlideMenuModel = DPSlideMenuModel(
      color: UIColor(colorLiteralRed: 140.0 / 255.0, green: 155.0 / 255.0,
                     blue: 237.0 / 255.0,
                     alpha: 1.0),
      controllerClassName: "DPSupportViewController",
      title: "Support",
      cellHeight: 88.0,
      actionBlock: nil)
    let slideMenuModelRate: DPSlideMenuModel = DPSlideMenuModel(
      color: UIColor(colorLiteralRed: 237.0 / 255.0, green: 140 / 255.0,
                     blue: 200.0 / 255.0,
                     alpha: 1.0),
      controllerClassName: nil,
      title: "Rate",
      cellHeight: 88.0,
      actionBlock: {
        let urlString: String = "itms-apps://itunes.apple.com/WebObjects/MZStore.woa/wa/viewSoftware?id=910117892" // replace 910117892 with your appid
        UIApplication.shared.openURL(URL(string: urlString)!)
    })
    let slideMenuModelDonate: DPSlideMenuModel = DPSlideMenuModel(
      color: UIColor(colorLiteralRed: 237.0 / 255.0, green: 100.0 / 255.0,
                     blue: 100.0 / 255.0,
                     alpha: 1.0),
      controllerClassName: nil,
      title: "Donate",
      cellHeight: 88.0,
      actionBlock: {
        let targetURL: String = "https://qr.alipay.com/apeez0tpttrt2yove2"
        UIApplication.shared.openURL(URL(string: targetURL)!) // Donate with alipay
    })
    let slideMenuModels: [DPSlideMenuModel] = [slideMenuModelProjects, slideMenuModelSupport,
                                               slideMenuModelRate, slideMenuModelDonate]
    
    // 4. create leftMenuViewController with DPSlideMenuModel array, then reset the drawer
    let leftMenuViewController: DPLeftMenuViewController = DPLeftMenuViewController(slideMenuModels: slideMenuModels, storyboard: self.storyboard)
    drawer?.reset(leftViewController: leftMenuViewController,
                  centerViewController: homeViewController)
  }

```

# Storyboard
![screenshot](https://github.com/HongliYu/DPSlideMenuKit-Swift/blob/master/skitch.png?raw=true)
![screenshot](https://github.com/HongliYu/DPSlideMenuKit-Swift/blob/master/skitch1.png?raw=true)
![screenshot](https://github.com/HongliYu/DPSlideMenuKit-Swift/blob/master/skitch2.png?raw=true)
