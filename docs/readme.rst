
import time
from pynput import keyboard

# Initialize the keyboard controller to simulate key presses
controller = keyboard.Controller()

def on_press(key):
    try:
        # Check if the pressed key is 'r'
        if key.char == 'r':
            print("R pressed: Holding E for 339ms...")
            
            # Press and hold 'e'
            controller.press('e')
            
            # Wait exactly 339 milliseconds
            time.sleep(0.339)
            
            # Release 'e'
            controller.release('e')
            print("E released.")
            
    except AttributeError:
        # Ignore special keys like Shift, Ctrl, etc.
        pass

# Start listening to your keyboard inputs
with keyboard.Listener(on_press=on_press) as listener:
    listener.join()
