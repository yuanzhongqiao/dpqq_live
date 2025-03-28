# Mobile and Web Real-time Live Streaming Digital Human! 
# Real-time Digital Human: The Fastest in the Whole Network

Notes: Currently, the project mainly maintains `DH_live_mini`, which is the fastest digital human solution at present. There is no other solution that can match it. The project includes an example of web inference. It does not rely on any GPU and can run in real-time on any mobile device. The original `DH_live` is no longer supported. Please consider using it carefully. For the usage method of the original version, please refer to [here](https://github.com/kleinlee/DH_live/blob/main/README_DH_live.md).

Direct inference of `DHLive_mini` on mobile browsers [bilibili video](https://www.bilibili.com/video/BV1UgFFeKEpp)

![WeChat Image_20250209153828](https://github.com/user-attachments/assets/32650fac-3885-4c98-886f-66258ef891a7)

# News
- January 26, 2025: Minimized and simplified the web resource package. The gzip resource is less than 2MB. Simplified the video data, reducing the data size by half.
- February 9, 2025: Added an ASR entry and a one-click image switching feature.
- February 27, 2025: Optimized rendering and removed the reference video. Now, only one video is needed for generation.
- March 11, 2025: Added CPU support for `DH_live_mini`.

# Comparison of Digital Human Solutions

| Solution Name | Single-frame Computing Power (Mflops) | Usage Method | Face Resolution | Applicable Devices |
| --- | --- | --- | --- | --- |
| Ultralight - Digital - Human (mobile) | 1100 | Single - person training | 160 | Mid - to high - end mobile phone apps |
| DH_live_mini | 39 | No training required | 128 | All devices, including web pages, apps, and mini - programs |
| DH_live | 55046 | No training required | 256 | Graphics cards of the 30 series and above |
| duix.ai | 1200 | Single - person training | 160 | Mid - to high - end mobile phone apps |

### Checkpoint
All checkpoint files have been moved to [baiduNetDisk](https://pan.baidu.com/s/1jH3WrIAfwI3U5awtnt9KPQ?pwd=ynd7).

### Key Features
- **Lowest computing power**: The computing power required for inferring one frame is 39 Mflops. How small is it? It is less than most face detection algorithms on mobile devices.
- **Smallest storage**: The entire web resource can be compressed to 3MB!
- **No training required**: Ready to use out of the box, no complex training process is needed.

### Platform Support
- **Windows**: Supports video data processing, offline video synthesis, and web servers.
- **Linux & macOS**: Supports video data processing and setting up web servers, but does not support offline video synthesis.
- **Web pages & mini - programs**: Can be directly opened on the client side.
- **Apps**: Can call web pages via the webview method or reconstruct native applications.

| Platform | Windows | Linux/macOS |
| --- | --- | --- |
| Original video processing & web resource preparation | ✅ | ✅ |
| Offline video synthesis | ✅ | ❌ |
| Building a web server | ✅ | ✅ |
| Real - time dialogue | ✅ | ✅ |

## Easy Usage (Gradio)
Run this Gradio if you are using it for the first time or want to get the full process.
```bash
python app.py
```

## Usage

### Create Environment
First, navigate to the `checkpoint` directory and unzip the model file:
```bash
conda create -n dh_live python=3.11
conda activate dh_live
pip install torch --index-url https://download.pytorch.org/whl/cu124
pip install -r requirements.txt
cd checkpoint
```
Note that you can choose to install the CPU version of PyTorch: `pip install torch`

Unzip checkpoint files from [baiduNetDisk](https://pan.baidu.com/s/1jH3WrIAfwI3U5awtnt9KPQ?pwd=ynd7)

### Prepare Your Video
```bash
python data_preparation_mini.py video_data/000002/video.mp4 video_data/000002
python data_preparation_web.py video_data/000002
```
The processed video information will be stored in the `./video_data` directory.

### Run with Audio File (not supported on Linux and macOS!!!)
The audio file must be in the single - channel 16K Hz wav file format.
```bash
python demo_mini.py video_data/000002/assets video_data/audio0.wav 1.mp4
```

### Web demo
Please replace the corresponding files in the `assets` folder with the `assets` files from the new image package (e.g., `video_data/000002/assets`).
```bash
python web_demo/server.py
```
You can open `localhost:8888/static/MiniLive.html`.

## License
`DH_live` is licensed under the MIT License.

## Contact
| Add me as a friend. Please note "Join the group" to be added to the WeChat communication group. | Join the QQ group chat to share opinions and the latest information. |
