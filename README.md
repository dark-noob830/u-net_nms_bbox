# Anchor Boxes
---
Anchor box are predefined bounding boxes of different sizes and aspect ratio used in object detection model like YOLO and SSD. They allow the model to detect object of varying shapes and scales by predicting offsets relative to these anchors.

# 🔍why Anchor Box
---
Instead of predicting bounding box from scratch, models predict:
- Whether an object exists at a specific anchor.
- The offset of actual bounding box from the anchor box

This helps: 
- Detect multiple objects at different locations. 
- Handle different aspect ratios and scales efficiently.

# 🆚Anchor Box VS Region Proposals
---
Anchor Boxes can be seen as a replacement for the " region proposals " used in older object detection method like R-CNN.

- Traditional methods (R-CNN, Fast R-CNN) first generate region proposals using external algorithms (e.g., Selective Search).
- Faster R-CNN introduced Region Proposal Network (RPN) to generate proposal within the network.
- In contrast, models like YOLO and SSD do not explicitly generate proposals, Instead, They use predefined anchor boxes spread uniformly across the image and directly predict object presence and bounding box offsets relative to these anchors.

This approach simplifies and speeds up detection by eliminating the need for a separate proposal stage.



# ⛔Non-Maximum Suppression (NMS)

---

Non-Maximum Suppression (NMS) is a key post-processing step in object detection tasks. It helps eliminate redundant bounding boxes by keeping only the most confident ones and removing others that overlap too much.

  

## ❓Why NMS?

Object detection models often predict multiple overlapping bounding boxes for the same object. NMS reduces this redundancy by:

- Selecting the box with the highest confidence score.
- Removing all boxes that have a high Intersection over Union (IoU) overlap with the selected box.
- Repeating the process until no boxes remain.

  

## How it works (step-by-step):

1. Sort all predicted boxes by their confidence scores in descending order.
2. Pick the box with the highest score and add it to the list of final boxes.
3. Calculate IoU of this box with all other boxes.
4. Remove boxes that have IoU above a defined threshold (e.g., 0.5).
5. Repeat steps 2-4 until no boxes remain.