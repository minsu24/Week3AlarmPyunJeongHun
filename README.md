# Week3Alarm
# 게임공학전공 편정훈
week3 project
import UIKit
class ViewController: UIViewController {
    @IBOutlet var lblCurrentTime: UILabel!
    @IBOutlet var lblPickerTime: UILabel!
    @IBOutlet var datePicker: UIDatePicker!
    
    let timeSelector: Selector = #selector(ViewController.updateTime)
    let interval = 1.0
    var alarmTIme = ""
    
    override func viewDidLoad() {
        super.viewDidLoad()
        Timer.scheduledTimer(timeInterval: interval, target: self, selector: timeSelector, userInfo: nil, repeats: true)
        // Do any additional setup after loading the view.
    }

    @IBAction func changeDatePicker(_ sender: UIDatePicker) {
        let datePickerView = sender
        let formatter = DateFormatter()
        formatter.dateFormat = "yyyy-MM-dd HH:mm:ss EEE"
        lblPickerTime.text = formatter.string(from: datePickerView.date)
        alarmTIme = formatter.string(from: datePickerView.date)
    }
    @objc func updateTime() {
        let date = NSDate()
        let dateFormatter = DateFormatter()
        dateFormatter.dateFormat = "yyyy-MM-dd HH:mm:ss EEE"
        lblCurrentTime.text = dateFormatter.string(from: date as Date)
        if(lblCurrentTime.text == alarmTIme){
            view.backgroundColor = UIColor.red
        }
        else{
            view.backgroundColor = UIColor.white
        }
    }
    
}

