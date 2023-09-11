If you have IP cameras that stream video feed over RTSP or have video captured from your laptop's webcam, and you wish to visualize this content in real-time with extremely low latency, securely over TLS, within your web browser or on a grafana dashboard because maybe you want to build an home monitoring dashboard, you can configure *go2rtc*, a server that provides the shortest streaming latency possible and is effortless to set up on any operating system. You can checkout this fantastic project on its official GitHub repository: https://github.com/AlexxIT/go2rtc.

**Demo:** Grafana dashboard showing my home ip camera live feed, on the left I captured the video from a webcam to show you that the latency is imperceptible.

https://github.com/cxnturi0n/grafana-livecamera-rtsp-webrtc/assets/75443422/e8e76821-bb4c-42e5-a239-6d537ad5efd6



In this repository, I demonstrate how you can in 1 minute, see your live camera feed on a grafana dashboard (or just in the browser). Here are the steps:

1. Modify the `go2rtc-config/go2rtc.yaml` file with your desired source. I already left two examples in the file, but you can find additional examples and configuration settings at this link: https://github.com/AlexxIT/go2rtc#source-rtsp.

2. Customize the Grafana dashboard to display the live camera stream using a 'Text' panel and embedding the WebRTC stream inside an Iframe. To do so you can update the content tag within `grafana/dashboard/dashboards/dashboard.json` with your specific Iframe. For example, if your go2rtc server is running on localhost and the web UI is on port 1984, and the stream name you configured in `go2rtc-config/go2rtc.yaml` is 'dahua', the live camera will be shown in the browser at http://localhost:1984/stream.html?src=dahua&mode=webrtc, so you can use the following Iframe:

   ```html
   <iframe width="1000" height="1000"
      src="http://localhost:1984/stream.html?src=dahua&mode=webrtc">
   </iframe>
4. Launch go2rtc and Grafana in separate containers using ```docker-compose up -d```.
5. Access the Grafana dashboard at http://localhost:3000/d/b303f51a-4216-43f3-a57d-0e0d4e9a42bb/livecamerademodashboard?orgId=1 and the go2rtc web UI at http://localhost:1984.


