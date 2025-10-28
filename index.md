# Ball Tracking Robot
I built a ball-tracking robot that uses a Raspberry Pi camera and computer vision to detect, follow, and stop in front of a red ball. It processes live video to locate the ball’s position and distance, then adjusts its motors in real time to keep the ball centered and maintain the correct following distance.

<!--You should comment out all portions of your portfolio that you have not completed yet, as well as any instructions:
```HTML 
<!--- This is an HTML comment in Markdown -->
<!--- Anything between these symbols will not render on the published site -->
```-->

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Vishal Sankaranarayanan | JP Stevens | Mechanical Engineering | Incoming Senior

**Replace the BlueStamp logo below with an image of yourself and your completed project. Follow the guide [here](https://tomcam.github.io/least-github-pages/adding-images-github-pages-site.html) if you need help.**

![Headstone Image](logo.svg)
  
# Final Milestone

<iframe width="560" height="315" src="https://www.youtube.com/embed/lhMH3puVH-s?si=5qKdQKWR6ZSVkvtA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

Since my second milestone, I have completed the full ball-tracking robot. I integrated the Raspberry Pi camera with motor controls so that the robot could follow a red ball in real time. The robot now detects the ball’s position using computer vision, calculates whether it’s centered or off to the side, and adjusts the motors proportionally to move forward or turn smoothly. I also implemented a stopping mechanism so the robot halts when it reaches the ball, preventing collisions. This milestone represents the first fully functional system combining vision and motion control.

One major challenge was fine-tuning the HSV thresholds for the red ball under different lighting conditions. The robot would occasionally detect other red objects or lose track of the ball entirely. Another challenge was achieving smooth motor control. Initially, the robot would overshoot or only turn in one direction. By testing each motor independently and implementing proportional turning, I overcame these issues. My biggest challenge was seeing the robot successfully follow the ball in real time. It was extremely satisfying after all the trial and error.

Throughout this project, I gained experience in multiple areas of engineering. I learned how to use computer vision to process images and detect objects in real time, how to control motors using GPIO pins and the gpiozero library, and how to calibrate a camera to estimate distance from an object. I also improved my troubleshooting skills, learning to debug both hardware and software simultaneously, and how small adjustments can drastically improve performance.

After everything I’ve learned at BSE, I hope to expand my skills in robotics even further. I want to explore adding ultrasonic sensors for obstacle detection, advanced shape recognition, and autonomous navigation. Beyond robotics, I’m want to apply these skills to other fields of engineering, such as aerospace where real-time sensing and control are critical. BSE has given me the foundation to tackle more complex, hands-on engineering projects in the future.



# Second Milestone

<iframe width="560" height="315" src="https://www.youtube.com/embed/6Bf7_-hM-nk?si=zCgov5mG5xRJdPSH" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

Since my first milestone, I’ve expanded my project to include real-time object detection using the Raspberry Pi Camera and OpenCV. I wrote a program that allows the robot to detect and locate a red-colored object in its field of view, which is a key step toward enabling autonomous ball tracking and following.

The code begins by initializing the Raspberry Pi Camera through the picamera2 library and setting it to capture images at 640×480 resolution in RGB format. Each incoming frame is converted from BGR to HSV color space, which is better for color filtering because hue, saturation, and brightness are handled separately. To capture the full range of red shades, I defined two hue ranges — one at the lower end of the hue spectrum (lower_red1 to upper_red1) and one at the higher end (lower_red2 to upper_red2).

These two ranges are applied as binary masks using cv2.inRange, then combined into a single mask showing only pixels that match the target red color. I use cv2.findContours to locate distinct shapes in the mask and select the largest one (which should be the red ball). Using image moments (cv2.moments), the code calculates the contour’s centroid (cx, cy), which represents the ball’s position. I draw a green circle at this location in the original frame and save both the original and mask images for debugging purposes.

One challenge I faced was fine-tuning the HSV thresholds for reliable detection. Lighting changes had a big impact. A small shift in brightness or shadow could cause false detections or complete misses. I overcame this by systematically testing in different lighting setups and adjusting the ranges for more tolerance.

Another major challenge was with the robot’s motion control. At one stage, it kept turning right continuously without turning left. I discovered this was due to a motor control imbalance, where the left motor wasn’t receiving the correct signal. I fixed this by testing each motor independently, identifying the wiring and control issue, and rebalancing the movement logic so both motors respond evenly.

Before my final milestone, I plan to:
- Integrate ultrasonic sensors to measure the distance to obstacles or the target ball.

- Add distance tracking so the robot can adjust its speed and stop at a safe range from the object.

- Implement shape tracking in addition to color detection, so the robot can better distinguish the ball from similarly colored backgrounds.

# First Milestone

<iframe width="560" height="315" src="https://www.youtube.com/embed/U72xngeip3c?si=YS2BSfhBftbgAVuk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

The main goal of the Ball Tracking Robot is to create a robot that can detect and follow a red-colored ball in real time. The main components of this project include:
- Car Chassis + Motors: Serve as the structure and movement system of the robot.
- Raspberry Pi: Acts as the "brain" of the robot, running the code and processing the camera input.
- H-Bridge: Supplies power to all of the motors, allowing control over the robot's direction.
- Camera: Captures live video for ball detection and tracking 
- Breadboard and Jumper Wires: Breadboard and LED's are mainly used for aesthetics, and jumper wires to connect all of the parts to the Raspberry Pi

How it Works:
The camera captures frames continuously, being able to detect and track a red ball using Open CV. Once the position of the ball has been identified, the Raspberry Pi sends a signal to the motors to move. If the ball is centered, the robot will move slightly forward. If it is slightly off to the side(either left or right), the robot turns to that respective direction until the ball is re-centered. If the ball is not detected by the camera at all, it will simply spin until it detects the ball.

Progress:
- Successfully set up Raspberry Pi
- Set up circuit with LED's
- Wrote Python code for the circuit and the motors, enabling the LED's to blink at my own pace and enabling the motors to spin both forward and backward
- Built car chassis
- Sucessfully connected the H Bridge, motors, breadboard to the Raspberry Pi

Challenges:
Throughout the process of reaching the first milestone, I faced several challenges. The first challenge that I faced was creating the circuit. Since I had never done it before, I often wired it incorrectly. Once I got that complete I moved on to assembling the car chassis where another issue popped up. One of the pieces was missing. As a result, I lost valuable time because I couldn't test whether the robot would respond to the motor commands properly without the car chassis. The final challenge was building the new car chassis after receiving the replacement part. The assemly process was difficult because the spaces were very tight and it took a long time to put the entire car chassis together.


# Schematics 
<img width="984" height="741" alt="image" src="https://github.com/user-attachments/assets/c08258da-0c20-4a24-8a84-10be448fc841" />


# Code
```from picamera2 import Picamera2
import cv2
import numpy as np
from gpiozero import Motor
from time import sleep

# --------------------
# Initialize camera
# --------------------
picam2 = Picamera2()
picam2.configure(picam2.create_preview_configuration(
    main={"format": "RGB888", "size": (640, 480)}
))
picam2.start()
sleep(1)

# --------------------
# Motors
# --------------------
motorA = Motor(forward=24, backward=25, pwm=True)
motorB = Motor(forward=23, backward=18, pwm=True)

# --------------------
# Constants
# --------------------
r_ball = 4.25
z_ball = 10
frame_width = 640
center_tolerance = 60   # pixels for small offsets
stop_distance = 6       # inches
max_forward_speed = 0.6
max_turn_speed = 0.3    # reduced turn speed for smoother motion
min_turn_speed = 0.1

# --------------------
# Image processing
# --------------------
def processimage(frame):
    hsv = cv2.cvtColor(frame, cv2.COLOR_BGR2HSV)
    lower_red1 = np.array([0, 100, 100])
    upper_red1 = np.array([10, 255, 255])
    lower_red2 = np.array([160, 100, 100])
    upper_red2 = np.array([179, 255, 255])

    mask1 = cv2.inRange(hsv, lower_red1, upper_red1)
    mask2 = cv2.inRange(hsv, lower_red2, upper_red2)
    mask = cv2.bitwise_or(mask1, mask2)
    mask = cv2.erode(mask, None, iterations=2)
    mask = cv2.dilate(mask, None, iterations=2)

    contours, _ = cv2.findContours(mask, cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_SIMPLE)
    if contours:
        (x, y), radius = cv2.minEnclosingCircle(max(contours, key=cv2.contourArea))
        return radius, x
    return None, None

# --------------------
# Camera calibration
# --------------------
f_camera = None
while f_camera is None:
    image = picam2.capture_array()
    r_image, x_ball = processimage(image)
    if r_image:
        f_camera = (z_ball * r_image) / r_ball
        print(f"Camera calibrated: focal length = {f_camera:.2f}")
    else:
        print("Looking for ball to calibrate...")
        motorA.forward(max_turn_speed)
        motorB.backward(max_turn_speed)
        sleep(0.1)

motorA.stop()
motorB.stop()
sleep(0.1)

# --------------------
# Main loop
# --------------------
last_offset = 0  # Remember last seen direction

while True:
    frame = picam2.capture_array()
    r_image, x_ball = processimage(frame)

    if r_image:
        z_current = (r_ball * f_camera) / r_image
        center_x = frame_width / 2
        offset = x_ball - center_x  # negative = left, positive = right
        last_offset = offset  # update last known direction
        print(f"Distance: {z_current:.2f} in, Offset: {offset:.2f}")

        if z_current <= stop_distance:
            motorA.stop()
            motorB.stop()
            print("Ball within 6 inches → stopped")
        else:
            # Proportional turning
            if abs(offset) > center_tolerance:
                turn_speed = max_turn_speed * (abs(offset) / center_x)
                turn_speed = min(turn_speed, max_turn_speed)
                turn_speed = max(turn_speed, min_turn_speed)  # ensure minimum turn speed
                if offset < 0:  # ball is left
                    motorA.backward(turn_speed)
                    motorB.forward(turn_speed)
                    print("Turning left")
                    print(turn_speed)
                else:  # ball is right
                    motorA.forward(turn_speed)
                    motorB.backward(turn_speed)
                    print("Turning right")
                    print(turn_speed)
            else:
                # Ball roughly centered → move forward
                motorA.forward(max_forward_speed)
                motorB.forward(max_forward_speed)
                print("Moving forward")
    else:
        # Ball lost → spin toward last known direction
        print("Ball lost → spinning to relocate")
        if last_offset < 0:
            motorA.backward(max_turn_speed)
            motorB.forward(max_turn_speed)
        else:
            motorA.forward(max_turn_speed)                                                                                                                                                                                                          
            motorB.backward(max_turn_speed)

    sleep(0.1)
```

# Bill of Materials
| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Raspberry Pi Kit | What the item is used for | $95.19 | <a href="https://www.amazon.com/RasTech-Raspberry-Starter-Heatsink-Screwdriver/dp/B0C8LV6VNZ/ref=sr_1_4?crid=3506HY00MCGVM&dib=eyJ2IjoiMSJ9._zkM62vSQ8p7tNr88715LdMv_qHh72Je-tkF9PXEa3chDE53QT4aZu4AGAb4ihE61QY4ZD55nKF6Fp2Kfs8t7AbafM_JrlJFfHo9OB4eAVGqa0EB-7aoBQHPmhKHZ2MW8ny-Kd44bMVlVxPlTWVk5YHIN5P3uKVqrE5Dcal0rKkHny-O6Xyb5ux2AOU6OwVbkag_bqBX66RQNRrgBuz-0pS43mcx93IZTQA9R8NaJJypYU2HAycp-XicTFmyU60a01Nfm9iuyo6B9yA8ppN3OQQyJ-NQ9xyNPxfTLwkqtng.yAYpU6outhQcZmOZhN9Wb6yTw7A85CNUbXZguGInZNg&dib_tag=se&keywords=raspberry%2Bpi%2Bkit&qid=1718848547&s=electronics&sprefix=rasbperry%2Bpi%2Bkit%2Celectronics%2C83&sr=1-4&th=1"> Link </a> |
| Robot Chassis | What the item is used for | $18.99 | <a href="https://www.amazon.com/Smart-Chassis-Motors-Encoder-Battery/dp/B01LXY7CM3/ref=sr_1_5?crid=373Y5YK6JWMD&keywords=robot+chassis&qid=1687740144&sprefix=robot+chassi%2Caps%2C93&sr=8-5"> Link </a> |
| Screwdriver Kit | What the item is used for | $5.94 | <a href="https://www.amazon.com/Small-Screwdriver-Set-Mini-Magnetic/dp/B08RYXKJW9/"> Link </a> |
| Ultrasonic Sensor | What the item is used for | $9.99 | <a href="https://www.amazon.com/WWZMDiB-HC-SR04-Ultrasonic-Distance-Measuring/dp/B0CQCCGXCP/ref=sr_1_1_sspa?crid=3J2JR973WKPHO&dib=eyJ2IjoiMSJ9.E2SIkElJhtFWCJCHL5Q6Y73Ys_HCMPRVFCIrG_zKv4Og7BdZNtr69Mkju140lhlfzFGQuY542jpsp8FMrtV9d2hCBI7D8lYTH9bcgDXZhs4941uj-d1D69ZYdKmAI1Jig3VmYXOl3axVQ8Jq5L3nGRymNMtNbxkaFqGNyzkq4p37hhxU6jheuoaMo3Onz2FE9ILThkjUbdxRNW3rrZgZ7bYj9mf-yav85hBAmNduYyo.EneY3GmHDfDjDwhdUdDQ4Ktk6fECH62Adb42cEkehRc&dib_tag=se&keywords=ultrasonic%2Bsensor&qid=1715961326&sprefix=ultrasonic%2Bsensor%2Caps%2C72&sr=8-1-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9hdGY&th=1"> Link </a> |
| H Bridges | What the item is used for | $8.99 | <a href="https://www.amazon.com/ACEIRMC-Stepper-Controller-2-5-12V-H-Bridge/dp/B0923VMKSZ/"> Link </a> |
| Pi Cam | What the item is used for | $12.86 | <a href="https://www.amazon.com/gp/product/B07RWCGX5K/ref=ox_sc_act_title_1?smid=A2IAB2RW3LLT8D&psc=1"> Link </a> |
| Electronics Kit | What the item is used for | $11.98 | <a href="https://www.amazon.com/EL-CK-002-Electronic-Breadboard-Capacitor-Potentiometer/dp/B01ERP6WL4/ref=sr_1_4?crid=30T5LTYVQLQ7Z&dib=eyJ2IjoiMSJ9.XZtpck6Llt4UIuYeKM4X3BoXzDuzolZMTCtFDj-oTh1vuIi0HYJZJEdpS-MCdGCK1AWUbUmgoEswoRPxGUSKeGRTzsciRE_l2Vrp8FGX1SxK-HmibPNyHBEtkFJKo_OYmMhkhdCJ4OIH38ALRfFvrXZ7OU5faZVvkTBqod8p7UZYwNwdLCcimwFWGWKaDa-gbbx_TGk7lYQmEbrzeL4UXM-gW3RDtuOV0dCykxwyvYJKCCcOhrK3f18N4NZjiqL_Y5noE1rQTmwyFcG67DzgpNaUPanwIQaYfCe5mgD-njY.v6mU1wYX4M5ShCiyrZMey0hbOwvqLszD8axpHbKlA6I&dib_tag=se&keywords=mini+breadboard+kit&qid=1716419767&s=electronics&sprefix=mini+breadboard+kit%2Celectronics%2C106&sr=1-4"> Link </a> |
| Motors | What the item is used for | $11.98 | <a href="https://www.amazon.com/AEDIKO-Motor-Gearbox-200RPM-Ratio/dp/B09N6NXP4H/ref=sr_1_4?crid=1JP29NIWBLH2M&dib=eyJ2IjoiMSJ9.Wq3jKgOLbqtEP772vMD4pV5f-w3PLBdEpKqguykXOb0JFO14f4Dq0m_VDVUMUFtR8WFINUEticI3GXcoGqwXPqK9yIh04PhCktgccMz9zAUiKXMJPwmOTUp_6av3XuFD0lXo9WngN9iKI6YgZrhEEs9qnqbcB1GnvgntCdKz8Q1dFuNu61NgSE6Z8vBk3FRpaNcr1lCI7FApTiNi0Qce8gbfmMn6oUggZQHpIOKKZ6s.M7WsZ_ZZtm3rm93kKgw0NOxt1McVBYX6m55oGxu1xxI&dib_tag=se&keywords=dc+motor+with+gearbox&qid=1715911706&sprefix=dc+motor+with+gearbox%2Caps%2C126&sr=8-4"> Link </a> |
| SD Card Adapter | What the item is used for | $9.99 | <a href="https://www.amazon.com/dp/B081VHSB2V?ref=ppx_yo2ov_dt_b_fed_asin_title&th=1"> Link </a> |
| DMM | What the item is used for | $11 | <a href="https://www.amazon.com/AstroAI-Digital-Multimeter-Voltage-Tester/dp/B01ISAMUA6/ref=sxin_17_pa_sp_search_thematic_sspa?content-id=amzn1.sym.e8da13fc-7baf-46c3-926a-e7e8f63a520b%3Aamzn1.sym.e8da13fc-7baf-46c3-926a-e7e8f63a520b&cv_ct_cx=digital+multimeter&dib=eyJ2IjoiMSJ9.5LQumrfBR8l0mKnJCJlRg73dxpou0gqYD_ffU3srgs0Utegwth8GcQCSVXVzeZeLSJx5J3itz5TLdmJHsrVITQ.-00jRPoT-bBy26YC4LzQ-S4cYdztgmSMGb83_WEm6HY&dib_tag=se&keywords=digital+multimeter&pd_rd_i=B01ISAMUA6&pd_rd_r=e1ff2570-7e4a-4906-bc55-6f819d48d1bc&pd_rd_w=h7HgL&pd_rd_wg=0ZcFH&pf_rd_p=e8da13fc-7baf-46c3-926a-e7e8f63a520b&pf_rd_r=R6YKX3NXTDQ1PQP4H8RM&qid=1715911879&sbo=RZvfv%2F%2FHxDF%2BO5021pAnSA%3D%3D&sr=1-1-7efdef4d-9875-47e1-927f-8c2c1c47ed49-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9zZWFyY2hfdGhlbWF0aWM&psc=1"> Link </a> |
| Champion sports ball | What the item is used for | $16.73 | <a href="https://www.amazon.com/Champion-Sports-Inch-Coated-Density/dp/B000KYTTYO/ref=sr_1_2_sspa?dib=eyJ2IjoiMSJ9.TLCeZ2jjYwnvK3RiJf14C4RstYOZXhRWTRbHkmLGiNfm5Vd8mVjvtsbUnBFk0S4d6cW9cPT7XDdhwMcPC30nsNwer7Uim0JVF49R8Od82u3RH4TY4mO1uP5LtqdvIEcW7CaOm7AzQ6xOvWQ4say1Ci9eGOxETDRWJP5rewLnqARbrvbe4kh-b2d5NHCLEsarPl16pM1UVlmQCXfMRksXigf_GpckmWPjeUM1AC8iiU0.lGUWr3-ZcZJNl0nJ2JaU6JEUOF9oR26lf0kUvETdmtM&dib_tag=se&keywords=7+inch+red+ball&qid=1748284272&sr=8-2-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9hdGY&psc=1"> Link </a> |
| AA batteries | What the item is used for | $18.74 | <a href="https://www.amazon.com/Duracell-Coppertop-AA-Ingredients-Long-lasting/dp/B0035LCFNQ/ref=sr_1_2_sspa?crid=2YR65MVXWA50C&dib=eyJ2IjoiMSJ9.Y7LKJBX-6tZ05fw4EcW76nu14zklVu0uDSTwj-0-cV44GfYvoaYnLKVwcPIB1rWt_qVnpkZnwoqkvrQmMFQ1qiTWN_rokxCgCagwBWaAIiv9PAbMqrwOrkGuvfWfklSZi5Y9W6AaUUspAaSMBZuUyS4cUoJB-s35FE-4seDyYIxfOaNAZggr154hcf3CR015QRyanTdKe1P3g2-fihntxqYoU2ek7H01s8toH4MNd-E.Mnyne8z1KkhvfDMnfFLgjUB9WgjdkdMcYRL591Pngbk&dib_tag=se&keywords=aa+batteries&qid=1748284893&refinements=p_85%3A2470955011&refresh=1&rnid=2470954011&rps=1&sprefix=aa+batterie%2Caps%2C122&sr=8-2-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9hdGY&psc=1"> Link </a> |
| USB power bank & cable | What the item is used for | $16.19 | <a href="https://www.amazon.com/SIXTHGU-Portable-Charging-Compatible-Earphones/dp/B0FJG8YKQH/"> Link </a> |

