## Project : Python tkinter GUI  Alarm Clock

### Structure to build a GUI Alarm clock from tkinter :
<font color = blue>
1. Import all the required libraries and modules<br>
2. Set up main event loop (time & sound) for the functions to be activated(alarm clock will automatically activated when the event is triggered).<br>
3. Create a user input(GUI application) display window 
</font>

#### Step 1 : Import all the required libraries and modules


```
from tkinter import *
from datetime import datetime
import time
import winsound
```

Notes:
- **tkinter** module is the standard GUI library for Python. When Python combined Tkinter will provide a fast and simple way in creating GUI application. Tkinter provides a powerful object-oriented interface to the Tk GUI toolkit.
- **datetime** and **time** modules in python will be set as function for an event to be triggered.
- **winsound** modules enable the access to the Windows platform's basic sound playing machinery. It is activated when the event set when a function is called.  

#### Step 2: Set up event loop


```
def alarm(set_alarm):
    while True:
        time.sleep(1)
        current_time = datetime.date.time.now()
        now = current_time.strftime("%H:%M:%S")
        date = current_time.strftime("%d/%m/%Y")
        print("The Set Date is : ",date)
        print(now)
        if now == set_alarm:
            print("Please WAKE UP!")
            winsound.PlaySound("sound.wav", winsound.SND_ASYNC)
            break
            
def actual_time():
    set_alarm = f"{hour.get()}:{min.get()}:{sec.get()}"
    alarm(set_alarm)
    
```

Notes:
- **alarm()** as a function was defined that take argument of **(set_alarm)**. It consists of a while loop with Boolean function as True to trigger the event automatically.
- **time.sleep(1)** ceases the execution of further commands given unless time value has been input by the user , set in the command code to return the background thread of the clock time going on a regular interval.
- **current_time** acquire the current time via the argument of **datetime.datetime.now()**.
- **now** is set to print for the time and date for the current date via string conversion using **strftime()**.
- **actual_time** which capture the input from user to set the alarm in string format. This is similar argument for the **(set_alarm)** as an alarm before execution in the event while loop which is further use in developing the GUI.
- **Please WAKE UP!** will be printed when the **set_alarm** inout by user matches the while loop ongoing time.
- **winsouns.SND_ASYNC** will be activated immediately to play the sound from the system when the function is called(event is triggered) as a reminder for the alarm clock. 

#### Step 3: Create GUI from tkinter


```
mclock = Tk()

mclock.title("MeiTan Alarm Clock")
mclock.geometry("600x400")
time_format = Label(mclock,text="Please set alarm in 24 hour format!",fg="red",bg="black",font=("Arial",16,"bold")).place(x=135, y=250)
add_time = Label(mclock,text="Hour                 Min                 Sec",font=80).place(x=190,y=120)
set_your_alarm = Label(mclock,text="When to wake up?",fg="blue",bg="yellow",relief="solid",font=("Arial",16,"bold")).place(x=190, y=30)

# Variables used to initiate the alarm
hour = StringVar()
min = StringVar()
sec = StringVar()

# Time used to set the alarm clcok
hour_time = Entry(mclock,textvariable=hour,bg="pink",width=15).place(x=160,y=100)
min_time = Entry(mclock,textvariable=min,bg="pink",width=15).place(x=260,y=100)
sec_time = Entry(mclock,textvariable=sec,bg="pink",width=15).place(x=360,y=100)

# Capture the input from user
submit = Button(mclock, text="Set Alarm",fg="red",font=("arial",16,"bold"),width=15,command=actual_time).place(x=190,y=180)

# Execution for the window
mclock.mainloop()
```
