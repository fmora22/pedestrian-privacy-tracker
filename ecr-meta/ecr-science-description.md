# **Science**

This application is designed primarily as an educational activity that teaches students how edge computing systems perform real-time video analysis. It combines YOLOv8 person detection, simple motion tracking, and a privacy-preserving Gaussian blur technique, allowing learners to explore multiple concepts in computer vision while keeping the workflow easy to understand.

The privacy component uses a lightweight **Gaussian blur “privacy strip”** applied only to the upper region of each detected person’s bounding box. This demonstrates how edge devices can enforce privacy at the source by masking sensitive regions *before* any data leaves the device. Students can adjust parameters such as blur strength and the portion of the box that is blurred to see how basic image-processing kernels change the output. This makes Gaussian blurring a practical and approachable introduction to privacy techniques in AI systems.

Beyond learning, the application also shows how edge devices can monitor simple pedestrian movement in real time. By estimating whether each person moves left or right, the system offers continuous insight into how people navigate hallways, sidewalks, or campus spaces — without sending full video feeds to the cloud.

This tool is scientifically relevant for research in:

* privacy-aware sensing
* crowd safety and congestion monitoring
* space-usage analysis in buildings and outdoor environments
* behavior and movement studies
* design of intelligent, distributed sensor networks

---

# **AI@Edge**

The application uses **YOLOv8 with Ultralytics ByteTrack** to detect and track people on a frame-by-frame basis.

Workflow:

1. A frame is captured from a video file, RTSP stream, or Waggle camera.
2. YOLOv8 detects each person and returns bounding boxes.
3. ByteTrack assigns stable track IDs to follow each person over time.
4. The system computes how far each track has moved horizontally and classifies movement as left or right.
5. If privacy is enabled, a Gaussian blur strip is applied over the upper region of each bounding box before anything is saved or published.
6. Movement counts and system stats are logged locally or published as Waggle metadata.

Running the workload directly at the edge shows students why edge computing enables real-time analysis even in low-bandwidth environments — and how privacy can be enforced *before* data ever leaves the node.

---

# **Model Capabilities**

**YOLOv8 (n, s, m, l, x)**

* Fast, configurable object detection models
* Lightweight options for small devices
* Strong performance on indoor and outdoor pedestrians
* Compatible with ByteTrack for simple multi-object tracking

---

# **Ontology**

Each logged movement event includes:

* direction (left or right)
* starting + ending X coordinates
* timestamp
* CPU/GPU usage
* RAM usage
* device temperature (when available)
* total accumulated counts

These metadata provide a clear record of movement patterns and allow analysis of device performance — while keeping both video and blurred frames local to the device.

