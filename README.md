# Safety Equipment Detection in Space Stations Using YOLOv8 and Falcon Synthetic Data  
### Prompt Pirates — Hack Beyond 2025 (Duality AI Challenge)

## Overview
This project presents a lightweight computer-vision system designed to detect emergency safety equipment inside space-station environments. Using YOLOv8n trained on Falcon’s domain-randomized synthetic dataset, the model identifies 7 critical objects such as oxygen tanks, fire alarms, and emergency phones. The solution supports automated safety monitoring where real-world data collection is difficult or impossible.

## Dataset
The dataset was fully generated using Falcon’s digital-twin simulation with variation in:
- Lighting  
- Camera angles  
- Occlusions  
- Object placement  

**Classes (7):**  
Oxygen Tank, Nitrogen Tank, First Aid Box, Fire Alarm, Safety Switch Panel, Emergency Phone, Fire Extinguisher.

## Model & Training Configuration
- **Model:** YOLOv8n (nano variant)  
- **Epochs:** 10  
- **Batch Size:** 8  
- **Image Size:** 640×640  
- **Optimizer:** Adam  
- **Losses:** Box Loss, Objectness, Classification  
- **Dataset Config:** `yolo_params.yaml`

**Training Pipeline**
1. Load and prepare dataset  
2. Define dataset YAML  
3. Initialize YOLOv8n  
4. Train for 10 epochs  
5. Validate on val + test sets  
6. Save weights and plots to `runs/`  

## Results
### **Overall Performance**
| Metric | Score |
|-------|--------|
| Precision | 0.7729 |
| Recall | 0.4600 |
| F1 Score | 0.4021 |
| mAP@0.5 | 0.5224 |
| mAP@0.5:0.95 | 0.4021 |

### **Class-wise AP**
| Class | AP |
|--------|------|
| Oxygen Tank | 0.562 |
| Nitrogen Tank | 0.528 |
| First Aid Box | 0.524 |
| Fire Alarm | 0.269 |
| Safety Switch Panel | 0.304 |
| Emergency Phone | 0.251 |
| Fire Extinguisher | 0.378 |

**Key Observations**
- Strong precision → reliable when confident  
- Moderate recall → misses small/occluded objects  
- Performs best on large, high-contrast objects  
- Weakest for small or visually similar objects (Fire Alarm, Emergency Phone)

## Challenges
- Low recall due to small model size and short training (10 epochs)  
- Very low AP for small/rare classes  
- Misclassifications under heavy shadows or occlusions  
- Class imbalance in synthetic dataset  
- Model underfitting due to limited training time  
- Computing/training time constraints  
- Frequent wrong predictions for visually similar equipment  

## Conclusion
We successfully trained a YOLOv8n model using Falcon’s synthetic space-station data, achieving **mAP@0.5 = 0.5224** with strong precision and moderate recall. The system performs reliably for large objects and demonstrates the feasibility of using synthetic digital-twin data to develop safety-critical AI systems in inaccessible environments like orbiting space stations.

## Future Improvements
- Train longer (50+ epochs)  
- Upgrade to YOLOv8m or YOLOv8l  
- Add more domain randomization  
- Improve small-object augmentation  
- Add object tracking for real-time deployment  
- Explore transformer-based detectors (RT-DETR, YOLOv9/YOLOv8-xlarge)  

## Team — Prompt Pirates
- Tanvi Sharma — Lead Coordinator  
- Kunal Kapur — Presentation Curator  
- Sneha Singhal — Insight Developer  
- Saanchi Dandriyal — Insight Developer  

