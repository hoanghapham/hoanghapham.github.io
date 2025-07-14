---
date: '2025-07-14T15:59:05+07:00'
title: Kitchen Monitoring
draft: false
weight: 2
tags: ["Machine Learning", "Computer Vision"]
cover:
  image: projects/kitchen-monitoring-demo.gif
---

This project simulates a monitoring system for kitchens, using YOLO for object detection and tracking. The detection model is trained to track two types of items (dish, tray), and each item type has a classification model to further categorize them into three sub-classes, depending on the content of the dish or tray.

The system includes a module to perform inference, and a module for users to re-annotate the object detection themselves.

- **Models:** YOLO (for detection, tracking, and classification)
- **Tools:** FastAPI, Gradio, Docker

{{< github "https://github.com/hoanghapham/kitchen-monitoring" "GitHub">}}