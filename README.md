# Keypad-Servo-Motor-2
Keypad , Servo Motor 2
This Python code imports the necessary libraries and defines some functions to handle input from a keypad and control a servo motor. The program initializes a keypad and listens for input from the user. If the user enters a valid code, the servo motor opens a lock.

Here's a brief description of each part of the code:

```
import RPi.GPIO as GPIO
import time
import drivers
from pad4pi import rpi_gpio
```
This imports the necessary libraries for the program to work. `RPi.GPIO` and `pad4pi` are used to control the keypad, `time` is used to add delays, and `drivers` is used to display output on an LCD screen.

```
KEYPAD = [
    [1, 2, 3, "A"],
    [4, 5, 6, "B"],
    [7, 8, 9, "C"],
    ["*", 0, "#", "D"]
]
ROW_PINS = [17, 27, 22, 5] # BCM numbering
COL_PINS = [23, 24, 25, 16] # BCM numbering
```
This defines the layout of the keypad and assigns BCM pin numbers to the rows and columns of the keypad.

```
GPIO.setwarnings(False)    
servo_pin = 12
GPIO.setmode(GPIO.BCM)
GPIO.setup(servo_pin,GPIO.OUT)
pwm = GPIO.PWM(servo_pin,50) 
pwm.start(0)
```
This sets up the servo motor by turning off warnings, setting the GPIO mode, and initializing the PWM signal.

```
DEFAULT_INDENT = "     "
input_key_codes = DEFAULT_INDENT
DEFAULT_KEYCODE_LENGTH = 6
```
These define some constants used in the program.

```
def open_lock():
    ...
def close_lock():
    ...
def cleanup():
    ...
```
These are helper functions to control the servo motor and clean up resources when the program ends.

```
def display_to_lcd(data, position = 2, show_input_keycode = False, duration = 1):
    ...
```
This function displays output on the LCD screen. It takes in the data to display, the position on the screen, whether to display the input keycode, and the duration to display the message.

```
def init_keypad_driver():
    ...
def handle_keypad_press(key):
    ...
```
These functions handle input from the keypad. `init_keypad_driver()` initializes the keypad and `handle_keypad_press(key)` is called when a key is pressed. It updates the input keycode and displays it on the LCD screen.

```
def validate_keycode(keycode):
    ...
```
This function checks if the input keycode is valid. It compares the input to a pre-defined password and returns `True` if they match.

```
def main():
    ...
```
This is the main function thatinitializes the program. It displays a message on the LCD screen and sets up the keypad driver.

```
if __name__ == "__main__":
    try:
        while True:
            time.sleep(1)
            main()
    except KeyboardInterrupt:
        pass
    finally:
        cleanup()
```
This is the main flow of the program. It runs the `main()` function continuously until the user interrupts the program. When the program ends, it calls the `cleanup()` function to release resources and stop the program.

Overall, this program sets up a security system using a keypad and a servo motor to control a lock. When the user enters a valid code, the servo motor opens the lock, and when the user enters an invalid code, the program displays an error message on the LCD screen.
