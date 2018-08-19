# WWSegmentControl
一個自訂有QQ動畫的SegmentControl

![一個自訂的SegmentControl (上傳至Cocoapods)](https://raw.githubusercontent.com/William-Weng/Swift-4/master/_Gif_/WWSegmentControl.gif)

# 使用範例![IBOutlet](/Users/william-weng/Desktop/WWSegmentControl/IBOutlet.png)

```swift
import UIKit
import WWSegmentControl

class ViewController: UIViewController {
    
    @IBOutlet weak var myLabel: UILabel!
    @IBOutlet weak var myUIView: UIView!
    @IBOutlet weak var mySegmentControl: WWSegmentControl!
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        initWithIBOutlet()
        initWithFrame()
        initWithAutolayout(with: myUIView)
    }
    
    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
    }
}

extension ViewController {
    
    /// 使用IBOutlet
    private func initWithIBOutlet() {
        mySegmentControl.delegate = self
    }
    
    /// 使用Frame
    private func initWithFrame() {
        let mySegmentControl = WWSegmentControl.init(frame: CGRect.init(x: 50, y: 250, width: 200, height: 50))
        mySegmentControl.countSetting(3)
        mySegmentControl.titleSetting(["A", "B", "C"])
        view.addSubview(mySegmentControl)
    }
    
    /// 使用Autolayout
    private func initWithAutolayout(with view: UIView) {
        let mySegmentControl = WWSegmentControl()
        mySegmentControl.countSetting(3)
        mySegmentControl.titleSetting(["あ", "い", "う"])
        mySegmentControl.autolayoutSetting(to: view)
    }
}

extension ViewController: WWSegmentControlDelegate {
    
    /// 現在選到哪一個
    func wwSegmentControl(_ wwSegmentControl: WWSegmentControl, selectedItemAt index: Int, for button: UIButton) {
        myLabel.text = button.titleLabel?.text
        print(index)
    }
}
```
