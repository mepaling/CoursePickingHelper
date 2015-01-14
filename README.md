選課小幫手 CoursePickingHelper
==============================

## Introduction

This small windows application is to let students picks and view their course in a better way combined with notification gadgets like alarm clock, countdown timer...etc.  
In the past semasters, we (might) draw class table on a papper and fill it with our desired course. After that, we may modify it very frequently which is not very convenient.  
This tool is here to help, after importing a json-formated course information database, you can easily choose your course to fill to table.  
After this, you can even set some alarm clocks to notify you when it's time to choose course online.
And, this is a final project of 103 windows programming course by team 8, built in MFC.  

#### Feature

 * implemented in MFC which doesn't depend on .NET things.
 * Json-formated course information importing and exporting.
 * alarm clock, countdown timer, stop watch to notify the user to choose course online.

## Author & Member contribution

We are 103 windows programming course final project team 8  

 * 4101056017 資工三 邱冠喻
    * Course picking part
        * [Json-formated course information generater (also a parser)](https://github.com/chgu82837/university_course_parser/blob/for_WP_proj/subjects/nchu/dept_parser.py) using python
        * Json-formated course information importing using [Jsoncpp](https://github.com/open-source-parsers/jsoncpp)
        * Course picking state saving to Json file using [Jsoncpp](https://github.com/open-source-parsers/jsoncpp)
 * 4101040018 資工三 王建舜
    * Alarm clock part
        * alarm clock
        * countdown timer
        * shutdown timer
        * stop watch
        * music playing function

> Completed on 2015/1/15

## Goal

#### Course Picking Part

First, import the course imformation from a json file.  
Let user pick their course from the json and simulate the class table.  
After this, user can save the class they picked to another json file.  

#### Alarm clock Part

The alarm clock has four functions.  
First one is the alarm clock. You can add at most 1000 clocks.  
The second one is a countdown timer. You can countdown from 1 second to 24 hours.  
The third is a shutdown timer. You can choose either shutdown or restart your computer.  
Finally, the fourth is a stop watch.  

## Content & Usage

#### Course Picking Part

 * To use the course function, you must import a json file by clicking on button `匯入課程檔案` or any gadgets displaying `請匯入課程` as shown below

![14.png](http://i.imgur.com/2Ck2fMU.png)

 * After you choose a file, you can ...
    * add a course by choose an item from combobox `從這裡選擇要加入的課程`.
        * it will refuse you when there is a collision.
    * view selected course by click the combobox `按我觀看已選取的課程清單，選取之可清除`, and you can remove it by choosing the item you want to remove.
    * save the selected course state by click the button `儲存選課狀態`.
    * click on the table (report view) to view the course codes of selected courses
    * each time you select or unselect an item, you can view the detial of the course.

![14.png](http://i.imgur.com/kvMJ2FK.png)

#### Alarm clock Part

 * This is the main dialog. Then please click “鬧鐘” to enter the main dialog of alarm clock

![01.png](http://i.imgur.com/98yC3Ee.png)

 * The main dialog of the alarm clock is like the picture of the right. In this dialog, you can add at most 1000 clocks if you want.

![02.png](http://i.imgur.com/u6baul9.png)

 * Just click “加入鬧鐘” and you will open another dialog like the following picture. Then you can set what time to alarm you and what kind of music you expected it to play when the time is out. You can also set whether you want to cycle while playing.

![03.png](http://i.imgur.com/ckTA8dO.png)

 * Note that the media file only supports MP3 files.

![04.png](http://i.imgur.com/HPdsqBK.png)

 * When you have done entering data, then click “確定”. The data you have set will be add to the last row.

![05.png](http://i.imgur.com/5UaOXfX.png)

 * If you want to delete a row, just right click to highlight the row and click “刪除選定鬧鐘”, then you’ve done.

![06.png](http://i.imgur.com/HZigrQA.png)

 * If you want to change a clock in a row, just double right click the row and a changing dialog will display. You can edit your data in the dialog. Finally click “確定” to save the changes.

![07.png](http://i.imgur.com/4BJWgKW.png)

> The time has been changed.

 * Notice that you need to right click the checkbox (the box before time) to check it so that the selected clock will be activated. You can see that the number of “已啟用鬧鐘數量” has been changed.

![08.png](http://i.imgur.com/J8TZa7m.png)

> If you finish adding alarm clocks, please click “確定” button to conform.

 * Then it will choose the approximately next time from that time (now). So it will display 8:10, not 12:00. (refer to the previous step)

![09.png](http://i.imgur.com/9wtvZjt.png)

 * When the time you set comes, it will show a popup message box and start playing your selected song with your settings. To stop the music, click “確定” so that it will stop playing.

![10.png](http://i.imgur.com/ImxWqjK.png)

 * The next is the countdown timer. Just click “倒數定時器” then you’ll enter a dialog to set every parameters you need. Then please “確定” to use this setting.

![11.png](http://i.imgur.com/BBesGmA.png)

 * Then the remaining time is set by your setting. It also appear another two button. The function is just as the symbol say. You now can click start to countdown. After it count over, a pop up dialog will also show up just like the alarm clock.

![12.png](http://i.imgur.com/l0lCjad.png)

 * The function of shut down is like this. You can select when to close or restart your computer.

![13.png](http://i.imgur.com/eyuoQHE.png)

 * When you click the “碼表”, the stop watch will show in the main page. Then you can start using it.

![13.png](http://i.imgur.com/A8HYMdN.png)

## Code description

 * `MFC_FinalProj.cpp / MFC_FinalProj.h`
    * The program automatically generated. The start of the APP.

 * `MFC_FinalProjDlg.cpp / MFC_FinalProjDlg.h`
    * The main dialog. It handles with every input data from any dialog that has sent the data and start the corresponding programs.
    * `void import();`: import the course imformation from a json file
    * `void add_class(int cho);`: add a course to table accroding to `cho` of the index of the course
    * `void update();`: update the credit (學分數) on the title
    * `afx_msg void OnCbnSelchangeUnset();`: unselect a course
    * `afx_msg void OnBnClickedImportSave();`: save selected course to a json
    * `afx_msg void OnNMClickClassTable(NMHDR *pNMHDR, LRESULT *pResult);`: show the course codes of selected courses

 * `ClockChange.cpp / ClockChange.h`
    * These files are associated to the file change dialog. Its function is to change old clock data into new clock data.

 * `ClockSet.cpp / ClockSet.h`
    * These files are associated to the “加入鬧鐘” dialog. The function is like ClockChange but it adds a new clock. The ClockChange edit a current existing clock.

 * `ClockMain.cpp / ClockMain.h`
    * These files are associated with the “鬧鐘設定” dialog. It can decide how to show in this dialog, and what to do when you click the button like “修改鬧鐘” on it. Last but not least, it will send the clock data to main dialog.

 * `CountDown.cpp / CountDown.h`
    * These files are associated with the Countdown timer setting dialog. The data input from the dialog will be sent to main dialog.

 * `CMCI.cpp / CMCI.h`
    * These files are associated with the music file playing. By using the MCI (Media Control Interface) functions provided by Windows, you can easily play any media file as you wish.

 * `ShutDown.cpp / ShutDown.h`
    * These files are associated with Shutdown time setting dialog. The data input from this dialog will send to main dialog.

 * `ConfirmBox.cpp / ConfirmBox.h`
    * A yes/no question dialog

 * `Course.cpp / Course.h`
    * a course information structure class
    * `void to_list(CListCtrl* listView,short* class_table,short value,bool unset = false);`: add/remove the course itself to the table (including backend `class_table` and front-end `listView`)
    * `CString toString();`: get the full information of the course
    * `CString toCodeStr();`: get the code and the title of the course
    * `CString* utf8ToCString(char* utf8str)`: **important!**
        * usually a Json use utf8 to encode (most of internet exchanging file use this encoding), so I need to convert to unicode in order to work (display chinese...)

 * `Course_time.cpp / Course_time.h`
    * a time inteval of a course structure class

## Results

After choosing course desired, you can save it to a file and modify it as you like.  
And here is a demo of a complete course table (some students may think this is too insane)  

![17.png](http://i.imgur.com/2y4H62x.png)  

I also set an alarm clock to notify me when it's time to open my browser to get the course online  

![18.png](http://i.imgur.com/2QIzRqO.png)  

Oh, it is time to get the course online!  

![19.png](http://i.imgur.com/Iiq3gVs.png)

I can also use the code to choose course faster!

## Feedback

#### 4101056017 資工三 邱冠喻：

Although this is not the first time that I write a windows program, this experience is very different. MFC is **really** an underlying classes set that only wraps the windows api. It is also somehow an old thing (There isn't much thing when googling). But now I can feel how a **real** GUI program is created, you have to specify almost every thing to get it work (Thanks to Visual Studio's class wizard, I dont have to do this), this also means that everything is in my control and this feels great. MFC Crafting is under `C++` environment, I can fully control the memory using pointer and combine std and stl into MFC world.  

I have used the C++ library [Jsoncpp](https://github.com/open-source-parsers/jsoncpp). This thing is really useful that I can use it just like using in javascript, I also can use this as my data file saving and loading. The reason I use Json file format is that this format is easy to exchange between platform which is extremely convienent. The course information generator (parser) is written in `python` ([source code is here](https://github.com/chgu82837/university_course_parser/blob/for_WP_proj/subjects/nchu/dept_parser.py)), this is just a case.  

After this semaster is over, I might design a website with a friend who is great in designing to share and choose course just like this project. I program and she design. I think that will be great!

In this class, I learned more things about the OO part of C++, `.NET` languages like `C++/CLI` and the final MFC that create the oringal windows program. Most importantly, I think I learned time control and meet new friend in class. Thank you teacher!

#### 4101040018 資工三 王建舜：

By writing this program, I’ve learn a lot from it. I feel I have made progress on my program designing techniques. Most important of all, my partner use GitHub to deal with version control. I would have liked to learn Git for a long time, but I don’t know how to learn this skill. My partner taught me patiently, and finally I do know the most basic part of Git. I’m really appreciated of his teaching.
