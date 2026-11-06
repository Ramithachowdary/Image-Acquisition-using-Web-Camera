# EXP-2: Image Acquisition using Web Camera

## Experiment Details

- **Name:** Ramitha Chowdary S
- **Register Number:** 212224240130

## Aim

Write a Python program with OpenCV that takes a picture from the webcam and then:

1. Save that frame as a jpg.
2. Show the video.
3. Show the video again in a smaller window.
4. Rotate the video and show it.

## Software Required

- Anaconda
- Python 3
- Jupyter Notebook
- OpenCV
- Matplotlib

## Algorithm

**Step 1:** Open the webcam.

**Step 2:** Read one frame and save it as a jpg.

**Step 3:** Read the jpg back and display it.

**Step 4:** Read frames in a loop and show them one by one.

**Step 5:** Show the frames again inside a smaller figure.

**Step 6:** Turn each frame 90 degrees clockwise and display it.

**Step 7:** Release the webcam when the loop is done.

## Program

#### 1.

```python
import cv2
import matplotlib.pyplot as plt
from IPython.display import clear_output
import time
```

#### 2.

```python
cap = cv2.VideoCapture(0)
ret, frame = cap.read()
if ret:
    cv2.imwrite("captured_frame.jpg", frame)
cap.release()
```

#### 3.

```python
captured_image = cv2.imread('captured_frame.jpg')
```

#### 4.

```python
plt.imshow(captured_image[:,:,::-1])
plt.title('Captured Frame')
plt.axis('off')
plt.show()
```

#### 5.

```python
cap = cv2.VideoCapture(0)

for i in range(50):
    ret, frame = cap.read()
    if not ret:
        break
    frame_rgb = cv2.cvtColor(frame, cv2.COLOR_BGR2RGB)
    clear_output(wait=True)
    plt.imshow(frame_rgb)
    plt.axis('off')
    plt.show()
    time.sleep(0.05)

cap.release()
```

#### 6.

```python
cap = cv2.VideoCapture(0)

for i in range(50):
    ret, frame = cap.read()
    if not ret:
        break
    resized_frame = cv2.resize(frame, (100, 150))
    frame_rgb = cv2.cvtColor(resized_frame, cv2.COLOR_BGR2RGB)
    clear_output(wait=True)
    plt.imshow(frame_rgb)
    plt.axis('off')
    plt.show()
    time.sleep(0.05)

cap.release()
```

#### 7.

```python
cap = cv2.VideoCapture(0)

for i in range(50):
    ret, frame = cap.read()
    if not ret:
        break
    rotated_frame = cv2.rotate(frame, cv2.ROTATE_90_CLOCKWISE)
    frame_rgb = cv2.cvtColor(rotated_frame, cv2.COLOR_BGR2RGB)
    clear_output(wait=True)
    plt.imshow(frame_rgb)
    plt.axis('off')
    plt.show()
    time.sleep(0.05)

cap.release()
```

## Output

<img width="630" height="384" alt="Captured Frame" src="output/01-captured-frame.png" />

<img width="630" height="384" alt="Video" src="output/02-video-frame.png" />

<img width="100" height="150" alt="Smaller window" src="output/03-resized-window.png" />

<img width="384" height="630" alt="Rotated" src="output/04-rotated.png" />

## Result

The webcam frame was saved as a jpg. The video was shown, shown again in a smaller window, and rotated.
