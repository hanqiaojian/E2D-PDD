# An Easy-to-Deploy Product Defect Detection (E2D-PDD) System with End-Edge-Cloud Collaboration


## Introductiion

An Easy-to-Deploy Product Defect Detection system (E2D-PDD) with end-edge-cloud collaboration is developed to defect the detection of product in industrial scenarios. 

<div align=center><img src="figs/E2D_PDD_Video.gif" width="1000"></div>

**The main contributions are summarized as follows:**
  - An Easy-to-Deploy lightweight defect detection Network (E2DNet) is proposed that can solve the different detection problems in a unified model.
  - An Easy-to-Deploy PDD (E2D-PDD) system with end-edge-cloud collaboration are proposed to accelerate the detection speed of edge nodes, which realizes the plug-and-play of edge nodes while improving the detection speed.
  - E2D-PDD offers a 5\% improvement in detection accuracy over current state-of-the-art (SOTA) models and an average 64\% reduction in detection time.
  - Two PDD datasets of AC manufacturing (SDU-Haier-AQD and SDU-Haier-ND) are open sourced to accelerate related research progress.

[//]: # (<img src="https://github.com/liangdaojun/MHCE/blob/main/Images/MHCE.jpg">)   

 ![E2D-PDD System](figs/E2D_PDD_Arch.jpg)

## E2DNet

Considering together with the \``where are the defects'' problem existing in image type, we propose a Easy-to-Deploy defect detection Network (E2DNet) that can solve the \``what'' and \``where'' detection problems in a unified network. 

**The innovations of E2DNet include:** 
- A Up-Down (UD) module is designed to quickly obtain feature maps of various sizes; 
- The lightweight deep architecture can be easily obtained by stacking UD module;
- Numerous shortcut path is added between the feature maps in UD modules to reduce model over-fitting；
- E2DNet is a lightweight network architecture that can be deployed on Raspberry Pi. 

 ![The architecture of E2DNet](figs/E2DNet.jpg)

## ACDO algorithm for End-Edge-Could Collaboration

An Actor-Critic based Dynamic Offloading (ACDO) is designed to reduce the overall delay of E2DNet on end devices.
Ultrasonic sensors, scanners and cameras are used to obtain the location, type and appearance of AC, respectively. 
They are connected with Raspberry Pi, an end device deployed with E2DNet, to form a closed-loop process of perception, decision-making and control. 
In this end-edge-cloud collaboration scenario, the cloud has abundant computing capabilities but is far away from the end devices, and the edge servers are relatively close to the end devices but need to be connected to the end device via 5G network. 

![The architecture of E2DNet](figs/EEC_System.jpg)

## E2D-PDD System Implementation

We built an assembly line for industrial production detection to implement the E2D-PDD system with end-edge-cloud collaboration. In this E2D-PDD system, Raspberry Pi (4B) is used as the edge node to connect end devices such as ultrasonic sensors, scanners and cameras to realize low-cost and flexible deployment of the PDD algorithm.
Subsequently, the edge nodes are connected to the cloud via 5G to offload and schedule PDD tasks to further improve the speed of the detection algorithm. 
This makes the deployment of PDD detection units in complex industrial scenarios with high convenience and low cost.
Finally, the negative detection results are sent to PLC to sort out the unqualified products. 

![Hardware System](figs/Hardware_System.jpg)


## Experiments 

### AAD tasks
E2DNet achieves the best performance and fast runing speed compared to other SOTA models, realizing
the best trade-off between performance and speed. 
As shown in following figure, the performance (mAP), runing speed (FLOPs) and model size (parameters, indicated by bubble size) comparisons of different SOTA models on AAD tasks. 

<div align=center><img src="figs/mAP_AAD.jpg" width="800"></div>


### ADD tasks

The average mAP of E2DNet is much better than that of other lightweight object detection models. 
As shown in following figure,  mAP of different models when IoU ≥ 0.75.

<div align=center><img src="figs/mAP75_ADD.jpg" width="800"></div>

<div align=center><img src="figs/mAP_11_ADD.jpg" width="800"></div>

### Performance of ACDO Algorithms

AAD and ADD tasks with 3 priorities reach the lowest delay at different time intervals when ACDO is adopted. 

<div align=center><img src="figs/EEC_Perform.jpg"></div>
