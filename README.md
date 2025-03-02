# Video-Labeler

**Summary:**
- This app allows user to label a video by frame or an image. Using this video labeler, one can label their videos or images to train their Computer vision models. The advantage of having your very own video labeler is that you can develop the addiitonal features that can be useful for you. For instance, this video labeler enables you to test models you built using Detectron2 or Pytorch. Please be aware that the main.py may need to be modified further for other models or libraries. 

**Sponsorship/Contributions:**
- This GUI can be improved further. We are open to the idea of further development. If you wish to contribute/sponsor this project and develop additional capabilities or improve upon the existing capabilities that you wish to use, please do not hesitate to contact us directly.

**Installation:** 
- Explained in detail within instructions.txt file.

**How to use:**
There are 3 tabs available for this video labeler. Tab 1 & Tab 2 were developed by both Yavuz Can Kocoglu and Yildirim Kocoglu. Tab 1 is used for to work with videos, Tab 2 is used for to work with images. Tab 3 is developed by Yildirim Kocoglu to show model performance statistics for computer vision models using metrics such as mean average precision (COCO style metrics: COCO mAP50, etc.).

You can insert multiple videos or images to label all at once. Right listbox will show the list of videos or images. You delete selected or all of the items in the listbox. You select item by double clicking it, and it will be showed on canvas.
Videos or images will have different colors and background colors depending on if they are selected, if they haved bbox, polygons or predictions. This feature helps with tracking the available labels.
- $${\color{red}Red:}$$ If item has no bbox or polygon saved.
- $${\color{yellow}Yellow:}$$ It has only polygon saved.
- $${\color{organe}Orange:}$$ It has only bbox saved.
- $${\color{black}White:}$$ It has both the bbox and polygon saved.
- $${\color{blue}Blue:}$$ Selected item.

**Insert Bbox:** You can activate it by clicking show labels checkbox. Insert Bbox allows you add the bbox. You must hold left mouse button, and when you release, it finishes drawing it. You can move, modify the bbox. 
**Show labels**: This checkbox allows you to load bounding boxes (bboxes) that were initially labeled and predicted using your own model. 
**Insert Polygon:** You can activate it by clicking show polygons checkbox. Show labels checkbox allows you to load polygon that are saved and predicted. Insert Polygon allows you add Polygon. When you right mouse button, it finishes drawing polygon and connects the first and last inserted points. Delete button will delete the last point that was added. Esc button will cancel drawing polygon. You can move, modify the polygon.
**Insert Polygon Point:** When you select a polygon, it gets activated. It allows you to add extra point to selected polygon line. This is useful for training instance and semantic segmentation models such as Mask-R-CNN, etc.
**Delete Polygon Point:** When you select a polygon, it gets activated. It allows you to delete that specific polygon point.

Left Side: 
  The number 0 is for class 0 by default. You get the class from a text file "class.txt". The colors switch between ['blue', 'pink', 'cyan', 'green', 'black', 'orange']. For now, there are only 6 classes including class "0". However, one can add more classes themselvess if needed by adding more classes into the "class.txt" file.
  When you click confirm class, your next bbox or polygon will be will be in that class. If you selected an existing polygon or bbox, it will change the class of that bbox or polygon.
  List box will show the list of models you have. It exists in videos/models and images/models folder. By double clicking the model, you activate it. 
  Drop box allows you select between, selected frame, selected video and all the inserted videos options. These options will run prediction when you click detect predictions. Detected predictions will be in red color and can't be modified. They will be saved to [images or videos]/predictions/[bbox or polygon]. Predictions can be converted to normal bbox or polygons. You convert it by selection or all at once.
  Load prediction checkbox will show prediction if it exists on current frame or image.
  Show polygon bbox, will draw a bbox around polygons.
  Zstack labels and predictions are labels that exists and same for one video from beggining frame to end frame.
  By clicking prev, next, play/stop, reset video buttons, you save the bboxes and polygons you drew.

Bbox save:[videos or images]/label_files/[name of the video or image]. Format: "class: x1, y1, x2-x1, y2-y1"
Predictions save:[videos or images]/predictions/[name of the video or image]. Format: "class: polygon cover points (x1, y1, x2, y2), points"

![image](https://user-images.githubusercontent.com/33734353/229110744-3c81ad43-5030-4547-8103-004001259b60.png)


BELOW ARE EXAMPLES OF COMPUTER VISION MODELS DEVELOPED USING THIS VIDEO LABELER:

Example of bounding boxes detected (green boxes) using the Faster R-CNN model. The blue boxes are the labeled boxes. The decision for true positive (TP) or false positive (FP) depends on the selected COCO mAP score (can be changed within the code). In the case below all of the boxes were True positives (TP). The confidence score (in the detection) is given on the top left side of the box. 

![image](https://github.com/yavuzck132/Video-Labeler/blob/master/1691392097452.jpg)

Example of instance segmentation using the Mask R-CNN model. This is a custom designed rotated bounding boxes and in normal applications, the boxes would not be rotated. This is similar to Faster R-CNN for object detection but, also includes the segmentations in additon to the boxes. Additionally, it segments each object separately. Similarly, the classes and the confidence scores will be displayed on the boxes.

![image](https://github.com/yavuzck132/Video-Labeler/blob/master/1691390806339.jpg)

This is an example of semantic segmentation model developed using PointRend. Unlike Faster R-CNN and Mask R-CNN, this model does not differentatiate between multiple objects (especially if they are entangled or intersecting with each other). Rather, it localizes these objects based on the pixels within the images. For instance, in this case below, it segmented the cotton fibers (holographic images) out of the background but, did not differentiate between the background and the fibers. There are two classes in this case (the background and the fibers).

![image](https://github.com/yavuzck132/Video-Labeler/blob/master/1691392047415.jpg)

Finally,the COCO mAP metrics tab is shown below (Tab 3 in app). This tab helps you keep track of your model performance. This tab also allows for Precision-Recall curves to be plotted which gives the user a good idea about the performance of their computer vision model. Additionally, you have the option to track the number of labeled classes to avoid labeling mistakes or to simply have an idea of how many traning examples (instances of objects) are available for model training.

![image](https://github.com/drkocoglu/Video_Labeler/blob/main/1691448861925.jpg) 
