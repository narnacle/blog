+++
date = '2025-07-19T14:00:00+03:00'
draft = false
title = 'Raspberry Pi W Surveillance Camera'
tags = ["Rpi", "Selfhosting", "Linux"]
+++

Setting up a security camera using a Raspberry Pi is a popular and budget-friendly way to create a DIY surveillance system. The Raspberry Pi can be equipped with a camera module and configured to stream video or take periodic snapshots. Here's a simple guide to help you set up a basic security camera using a Raspberry Pi:

### Requirements:

- **Raspberry Pi** (any model, but newer models will perform better)
    
- **Raspberry Pi Camera Module** (or a compatible USB camera)
    
- **MicroSD card** (at least 8GB, preferably 16GB or higher)
    
- **Raspberry Pi OS** installed on the SD card
    
- **Power supply** for your Raspberry Pi
    
- **Wi-Fi** or **Ethernet** connection for network access (if remote access is needed)
    
- **Optional**: Motion sensors or PIR (Passive InfraRed) sensor for motion detection
    

### Basic Steps to Set Up the Camera:

1. **Install Raspberry Pi OS**:
    
    - If you don’t already have the Raspberry Pi OS on your microSD card, use [Raspberry Pi Imager](https://www.raspberrypi.org/software/) to install it. Choose the "Raspberry Pi OS" option and follow the prompts.
        
2. **Connect the Camera Module**:
    
    - Attach the **Raspberry Pi Camera Module** to the **camera port** on the Raspberry Pi. If you're using a USB camera, plug it into one of the USB ports.
        
    - To enable the camera, run the following command:
        
        ```bash
        sudo raspi-config
        ```
        
        - Navigate to **Interfacing Options** > **Camera** > **Enable**.
            
        - Reboot the Pi:
            
            ```bash
            sudo reboot
            ```
            
3. **Install MotionEye for Video Streaming**:
    
    - **MotionEye** is a popular software package that allows you to turn your Raspberry Pi into an IP camera with features like motion detection, email alerts, and streaming.
        
        To install **MotionEye**, run the following commands:
        
        ```bash
        sudo apt update
        sudo apt install motion
        sudo apt install libffi-dev libssl-dev python-dev python-pip
        sudo pip install motioneye
        sudo mkdir -p /etc/motioneye
        sudo cp -R /usr/local/lib/python2.7/dist-packages/motioneye/ /etc/motioneye
        ```
        
        Then, enable and start the service:
        
        ```bash
        sudo systemctl enable motioneye
        sudo systemctl start motioneye
        ```
        
4. **Configure MotionEye**:
    
    - Open your browser and go to your Raspberry Pi’s IP address on port 8765. For example:
        
        ```
        http://<your_pi_ip>:8765
        ```
        
    - You'll be prompted with a login screen:
        
        - **Username**: admin
            
        - **Password**: (leave it blank by default)
            
    - Once logged in, you can configure various settings such as resolution, frame rate, motion detection, and storage options (e.g., save video clips or snapshots).
        
5. **Accessing Your Camera Remotely**:
    
    - If you want to view the camera stream remotely, make sure the Raspberry Pi is connected to the internet and use either a **local network** or **VPN** to access the camera from outside your home. If you want to use port forwarding, forward port 8765 to your Pi’s IP address.
        
6. **Optional – Add Motion Detection**:
    
    - You can configure motion detection using the **MotionEye** interface.
        
    - Set up email alerts, FTP uploads, or even record video clips when motion is detected.
        

### Optional Enhancements:

- **Add PIR Sensors for Motion Detection**:
    
    - For a more energy-efficient setup, you can add a **PIR sensor** to only activate the camera when motion is detected.
        
- **Cloud Storage**:
    
    - You can configure MotionEye to upload snapshots or videos to cloud storage services like **Dropbox** or **Google Drive**.
        
- **Add Night Vision**:
    
    - If you're using the official camera module, consider getting a **Night Vision** camera or add IR lights for nighttime monitoring.
        
- **Powering the Pi**:
    
    - If you want to place your Raspberry Pi outside or somewhere that doesn't have easy access to power, consider using a **portable power bank** or **solar panel** to keep it running.
        

### Possible Alternatives:

- **OpenCV**: If you're interested in more advanced features like object detection, face recognition, or analyzing the video feed, you could use **OpenCV** on the Raspberry Pi for these capabilities.
    
- **Home Assistant**: For integration with home automation, **Home Assistant** offers various ways to add a camera feed and even automate actions based on motion detection.