Hand Gesture Controller using OpenCV & MediaPipe

This project enables touchless control of your computer using hand gestures captured through a webcam.
It supports controlling mouse movement, left/right click, scrolling, double click, system volume, and system brightness—all with simple intuitive gestures.

The system uses:

OpenCV – camera input & frame processing

MediaPipe Hands – real-time hand landmark detection

PyAutoGUI – controlling mouse actions

PyCAW – controlling system audio

screen_brightness_control – brightness management

Mathematical gesture mapping – identifying finger positions & gestures


Features
Mouse Control
Gesture	Action
✌️ V-Gesture	Enable pointer movement
✊ Fist	Drag (click & hold)
☝️ Index finger	Right click
👆 Middle finger	Left click
Two-finger closed	Double Click
Scrolling
Gesture	Action
Minor-hand pinch	Scroll (vertical or horizontal)

Brightness & Volume
Gesture	Action
Major-hand pinch	Brightness / Volume control (auto-detect horizontal/vertical pinch direction)

The program automatically classifies major hand (right) and minor hand (left) using MediaPipe’s handedness estimation.

Project Structure
main.py          # Main script for gesture recognition & control
README.md        # Documentation file

🛠️ Installation
1. Clone the Repository
git clone <your-repository-link>
cd gesture-controller

2. Install Dependencies

Make sure you have Python 3.7+.

pip install opencv-python mediapipe pyautogui comtypes pycaw screen-brightness-control


If pycaw causes issues:

pip install pycaw==20230407

▶️ How to Run

Just run the script using Python:

python main.py


NOTE: This is not a Streamlit app.
No streamlit run command is needed.
Use: python main.py

🎯 How It Works
1. Hand Detection

The script uses MediaPipe Hands to obtain 21 landmark points per hand.

2. Gesture Encoding

Finger openness is converted into a binary number, mapped to custom gesture enums such as:

FIST, INDEX, V_GEST, PINCH_MAJOR, etc.

3. Gesture Stabilization

To avoid jitter, gestures are confirmed only after several consecutive frames match.

4. Action Execution

Based on the detected gesture:

Mouse position → via pyautogui.moveTo()

Scroll actions → pyautogui.scroll()

Volume → via IAudioEndpointVolume

Brightness → via screen_brightness_control

📸 Starting the Program

When main.py runs:

A webcam feed opens

Hand landmarks are drawn

Gestures are recognized in real-time

Actions are executed instantly

Press Enter (↵) to exit.

⚠️ Safety & Notes

Ensure good lighting for accurate tracking.

Keep your hand within the camera’s view.

Disable PyAutoGUI failsafe (pyautogui.FAILSAFE = False) is already handled in the script—so be cautious when moving the cursor fast.

Works best on systems with a high-quality webcam.

🔧 Requirements

Windows OS (for PyCAW audio control)

Webcam

Python 3.7+

📌 Future Improvements

Add gesture customization UI

Add multi-gesture recording

Add support for Linux & macOS

Integrate AI-based gesture classification
