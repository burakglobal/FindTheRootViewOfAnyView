# FindTheRootViewOfAnyView
This is the example for you to find the Root view of the SubView

      
        var i = 0
 
        let rootView = view
        let allViews: [UIView] = getSubviewsOf(view: rootView!)
        
        for item in allViews {
            print("UIView Tag: \(item.tag) SuperView Tag:\(item.superview?.tag ?? 0)")
         }
    
    
    private func getSubviewsOf<T: UIView>(view: UIView) -> [T] {
        var subviews = [T]()
        
          for subview in view.subviews {
           subviews += getSubviewsOf(view: subview) as [T]
            
            
            if let subview = subview as? T {
                subviews.append(subview)
                subview.tag = i
                i = i + 1
                let addLabel = UILabel(frame: CGRect(x: 5, y: 5, width: 100, height: 130))
                addLabel.text = " viewTag:\(i) :\(subview.superview?.tag ?? 0)"
                addLabel.textColor = UIColor.black
                addLabel.adjustsFontSizeToFitWidth = true
                subview.addSubview(addLabel)
                subview.bringSubview(toFront: addLabel)
                
            }
        }
        
        return subviews
    }
    
    
    
