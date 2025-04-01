### Table 1: Time and Memory Benchmarking on 1 RTX6000 with k=1000 classes and a ResNet50 backbone for a batch size of 1

| Model Head        | # Prototypes | Time per Batch (s) | GPU Memory (GB) |
|-------------------|-------------|--------------------|----------------|
| DPE              | 15          | 0.0031            | 0.2032         |
| DPE              | 20          | 0.0033            | 0.2413         |
| DPE              | 30          | 0.0033            | 0.3176         |
| DPE              | 100         | 0.0045            | 0.8517         |
| Linear (Baseline) | N/A         | 0.0032            | 0.104          |

## 

### Table 2a - Model Worst Group Accuracy Performance (no attribute annotation):

| Algorithm       | WATERBIRDS   | CELEBA       | CIVILCOMMENTS | MULTINLI    | METASHIFT   | CHEXPERT    | IMAGENETBG  | NICO++      | LIVING17    |
|---------------|--------------|-------------|--------------|------------|------------|------------|------------|------------|------------|
| ERM          | 69.1±4.7      | 57.6±0.8    | 63.2±1.2     | 66.4±2.3   | 82.1±0.8   | 41.7±3.4   | 76.8±0.9   | 35.0±4.1   | 48.0±1.5   |
| CRT          | 76.3±0.8      | 69.6±0.7    | 67.8±0.3     | 65.4±0.2   | 83.1±0.0   | -          | 74.6±0.4   | 78.2±0.5   | 33.3±0.0   |
| ReWeightCRT  | 76.3±0.2      | 70.7±0.6    | 64.7±0.2     | 65.2±0.2   | 85.1±0.4   | -          | 75.1±0.2   | 77.5±0.7   | 33.3±0.0   | 
| DFR          | 89.0±0.2      | 73.7±0.8    | 64.4±0.1     | 63.8±0.0   | 81.4±0.1   | -          | 75.8±0.3   | 74.4±1.8   | 38.0±3.8   | 
| ERM + DPE    | 91.0±0.5      | 81.9±0.2    | 69.9±0.9     | 69.3±0.8   | 84.1±1.5   | -          | 87.9±0.6   | 50.0±0.0   | 54.0±4.0   | 

---

### Table 2b - Model Worst Group Accuracy Performance (no attribute annotation):

| Algorithm       | WATERBIRDS   | CELEBA       | CIVILCOMMENTS | MULTINLI    | METASHIFT   | CHEXPERT    | IMAGENETBG  | NICO++      | LIVING17    |
|---------------|--------------|-------------|--------------|------------|------------|------------|------------|------------|------------|
| ERM*         | 77.9±3.0      | 66.5±2.6    | 69.4±1.2     | 66.5±0.7   | 80.0±0.0   | 75.6±0.4   | 86.4±0.8   | 33.3±0.0   | 53.3±0.9   |
| RWY          | 86.1±0.7      | 82.9±2.2    | 67.5±0.6     | 68.0±1.9   | -          | -          | -          | -          | -          |
| AFR          | 90.4±1.1      | 82.0±0.5    | 68.7±0.6     | 73.4±0.6   | -          | -          | -          | -          | -          |
| ERM* + DPE   | 94.1±0.2      | 84.6±0.8    | 68.9±0.6     | 70.9±0.8   | 83.6±0.9   | 76.8±0.1   | 88.1±0.7   | 50.0±0.0   | 63.0±1.7   |

---

### Table 3a - Model Worst Group Accuracy Performance (no attribute annotation):

#### ✗: no group info is required  
#### ✓: group info is required for hyperparameter tuning  
#### ✓✓: validation data is required for training and hyperparameter tuning  

| Algorithm         | Group Info (Train / Val) | WATERBIRDS   | CELEBA       | CIVILCOMMENTS | MULTINLI    | METASHIFT   | CHEXPERT    |
|------------------|------------------------|--------------|-------------|--------------|------------|------------|------------|
| ERM             | ✗/✗                      | 69.1±4.7      | 57.6±0.8    | 63.2±1.2     | 66.4±2.3   | 82.1±0.8   | 41.7±3.4   |
| CRT             | ✗/✓                      | 76.3±0.8      | 70.4±0.4    | 68.5±0.0     | 65.4±0.1   | 83.1±0.0   | 74.0±0.2   |
| ReWeightCRT     | ✗/✓                      | 76.3±0.2      | 71.1±0.5    | 68.2±0.4     | 65.3±0.1   | 85.1±0.4   | 73.9±0.2   |
| DFR             | ✗/✓✓                     | 89.0±0.2      | 86.3±0.3    | 66.5±0.2     | 63.8±0.0   | 81.5±0.0   | 75.4±0.6   |
| ERM + DPE (ours)| ✗/✓✓                     | 91.0±0.4      | 87.7±0.6    | 71.5±0.6     | 74.8±0.3   | 87.9±0.7   | -          |

### Table 3b - Model Worst Group Accuracy Performance (no attribute annotation):

| Algorithm         | Group Info (Train / Val) | WATERBIRDS   | CELEBA       | CIVILCOMMENTS | MULTINLI    | METASHIFT   | CHEXPERT    |
|------------------|------------------------|--------------|-------------|--------------|------------|------------|------------|
| ERM*            | ✗/✗                      | 77.9±3.0      | 66.5±2.6    | 69.4±1.2     | 66.5±0.7   | 80.0±0.0   | 75.6±0.4   |
| Group DRO       | ✓/✓                      | 91.4±1.1      | 88.9±2.3    | 70.0±2.0     | 77.7±1.4   | -          | -          |
| RWG             | ✓/✓                      | 87.6±1.6      | 84.3±1.8    | 72.0±1.9     | 69.6±1.0   | -          | -          |
| JTT             | ✗/✓                      | 86.7          | 81.1        | 69.3         | 72.6       | -          | -          |
| CnC             | ✗/✓                      | 88.5±0.3      | 88.8±0.9    | 68.9±2.1     | -          | -          | -          |
| SSA             | ✗/✓✓                     | 89.0±0.6      | 89.8±1.3    | 69.9±2.0     | 76.6±0.7   | -          | -          |
| DFR*            | ✗/✓✓                     | 92.9±0.2      | 88.3±1.1    | 70.1±0.8     | 74.7±0.7   | -          | -          |
| GAP (Last Layer)| ✗/✓✓                     | 93.2±0.2      | 90.2±0.3    | -            | 74.3±0.2   | -          | -          |
| GAP (All Layer) | ✗/✓✓                     | 93.8±0.1      | 90.2±0.3    | -            | 77.8±0.6   | -          | -          |
| ERM* + DPE (ours) | ✗/✓✓                   | 94.1±0.4      | 90.3±0.7    | 70.8±0.8     | 75.3±0.5   | 91.7±1.3   | 76.0±0.3   |

### Table 4 - Additional BREEDS Datasets Worst Group Accuracy Results (Source Domain)

| Algorithm   | ImageNet Pre-training | Living-17 WGA | Living-17 Mean Accuracy | Non-living-26 WGA | Non-living-26 Mean Accuracy | Entity-30 WGA | Entity-30 Mean Accuracy |
|------------|----------------------|--------------|--------------------|----------------|--------------------|--------------|--------------------|
| ERM        | ✓                    | -            | -                  | 87.7±0.8       | 95.8±0.1           | 84.3±0.1     | 96.1±0.0           |
| ERM + DPE  | -                    | -            | -                  | 89.0±1.0       | 95.5±0.2           | 86.4±0.3     | 96.0±0.0           |

---

### Table 5 - Additional BREEDS Datasets Worst Group Accuracy Results (Target Domain)

| Algorithm   | ImageNet Pre-training | Living-17 WGA | Living-17 Mean Accuracy | Non-living-26 WGA | Non-living-26 Mean Accuracy | Entity-30 WGA | Entity-30 Mean Accuracy |
|------------|----------------------|--------------|--------------------|----------------|--------------------|--------------|--------------------|
| ERM        | ✗                    | 6.7±1.5      | 27.8±0.6           | 5.0±1.0        | 23.9±0.6           | 5.8±1.5      | 24.8±1.0           |
| ERM + DPE  | ✗                    | 9.0±1.0      | 30.2±1.5           | 8.0±1.0        | 24.7±0.6           | 8.8±0.2      | 29.6±0.0           |
| ERM        | ✓                    | 48.0±1.5     | 87.4±0.5           | 1.7±0.0        | 62.0±0.4           | 19.2±2.0     | 68.7±0.5           |
| ERM + DPE  | ✓                    | 54.0±4.0     | 87.4±0.3           | 7.7±0.0        | 61.5±0.4           | 28.8±1.5     | 70.1±0.3           |

### Table 6 - Standard Accuracy for All Methods

### Group Info Legend:
- **✗/✗**: No group information required
- **✗/✓**: Group information required for hyperparameter tuning
- **✗/✓✓**: Validation data required for training and hyperparameter tuning
- **✓/✓**: Full group information required

| Algorithm        | Group Info (Train / Val) | WATERBIRDS  | CELEBA      | CIVILCOMMENTS | MULTINLI    | METASHIFT   | CHEXPERT    |
|-----------------|------------------------|-------------|------------|--------------|------------|------------|------------|
| ERM            | ✗/✗                      | 84.1±1.7    | 95.0±0.1   | 85.4±0.2     | 80.9±0.3   | 91.5±0.2   | 88.6±0.7   |
| CRT            | ✗/✓                      | 89.2±0.1    | 94.1±0.1   | 83.0±0.0     | 80.2±0.0   | 91.5±0.0   | 79.1±0.1   |
| ReWeightCRT    | ✗/✓                      | 89.4±0.3    | 94.2±0.1   | 83.4±0.0     | 80.2±0.0   | 91.3±0.1   | 79.0±0.0   |
| DFR            | ✗/✓✓                     | 92.2±0.2    | 91.2±0.1   | 81.3±0.0     | 80.2±0.0   | 90.5±0.4   | 78.9±0.2   |
| ERM + DPE      | ✗/✓✓                     | 92.5±0.2    | 89.8±0.2   | 82.2±0.2     | 81.3±0.2   | 91.2±0.1   | -          |
| ERM*           | ✗/✗                      | 92.1±0.2    | 94.0±0.2   | 83.3±1.4     | 81.9±0.2   | 93.2±0.1   | 79.4±0.3   |
| Group DRO      | ✓/✓                      | 93.5        | 92.9       | 88.9         | 81.4       | -          | -          |
| RWG            | ✓/✓                      | -           | -          | -            | -          | -          | -          |
| JTT            | ✗/✓                      | 93.3        | 88.0       | 91.1         | 78.6       | -          | -          |
| CnC            | ✗/✓                      | 90.9±0.1    | 89.9±0.5   | 81.7±0.5     | -          | -          | -          |
| SSA            | ✗/✓✓                     | 92.2±0.9    | 92.8±0.1   | 88.2±2.0     | 79.9±0.87  | -          | -          |
| DFR            | ✗/✓✓                     | 94.2±0.4    | 91.3±0.3   | 87.2±0.3     | 82.1±0.2   | -          | -          |
| GAP (Last Layer) | ✗/✓✓                   | 94.6±0.2    | 91.7±0.2   | -            | 81.9±0.0   | -          | -          |
| GAP (All Layer)  | ✗/✓✓                   | 95.6±0.1    | 91.5±0.1   | -            | 82.5±0.1   | -          | -          |
| ERM* + DPE     | ✗/✓✓                     | 96.0±0.1    | 91.9±0.3   | 81.6±0.2     | 81.6±0.2   | 93.8±0.5   | 79.0±0.2   |

### Table 7 - Sensitivity Analysis to the Entropic Scale (i.e, inverse temperature, 1/τ) - Worst Group Accuracy 

| Dataset    | Inverse Temperature (1/τ) | 10    | 20    | 30    | 40    | Mean  | STD  |
|------------|--------------------------|-------|-------|-------|-------|-------|------|
| Waterbirds |                           | 93.6  | 93.9  | 94.1  | 94.5  | 94.03 | 0.38 |
| MetaShift  |                           | 89.7  | 91.7  | 90.8  | 91.3  | 90.88 | 0.87 |
| Living17   |                           | 63.0  | 58.7  | 57.3  | 55.3  | 58.58 | 3.26 |

### Table 8 - Sensitivity Analysis to the Entropic Scale (i.e, inverse temperature, 1/τ) - Overall Accuracy 

| Dataset    | Inverse Temperature (1/τ) | 10    | 20    | 30    | 40    | Mean  | STD  |
|------------|--------------------------|-------|-------|-------|-------|-------|------|
| Waterbirds |                           | 96.4  | 96.2  | 96.0  | 95.9  | 96.13 | 0.22 |
| MetaShift  |                           | 93.8  | 93.7  | 93.9  | 93.9  | 93.83 | 0.10 |
| Living17   |                           | 87.0  | 87.2  | 87.1  | 86.9  | 87.05 | 0.13 |

---

### Table 9 - Sensitivity Analysis to the IPS Loss Coefficient - Worst Group Accuracy

| Dataset    | IPS Loss Coefficient | 1e4   | 5e4   | 1e5   | 5e5   | Mean  | STD  |
|------------|----------------------|-------|-------|-------|-------|-------|------|
| Waterbirds |                      | 93.6  | 94.4  | 94.1  | 94.1  | 94.05 | 0.33 |
| MetaShift  |                      | 90.5  | 91.7  | 90.7  | 90.8  | 90.93 | 0.53 |
| Living17   |                      | 63.0  | 61.7  | 61.7  | 62.0  | 62.10 | 0.62 |


### Table 10 - Sensitivity Analysis to the IPS Loss Coefficient - Overall Accuracy 

| Dataset    | IPS Loss Coefficient | 1e4   | 5e4   | 1e5   | 5e5   | Mean  | STD  |
|------------|----------------------|-------|-------|-------|-------|-------|------|
| Waterbirds |                      | 96.3  | 95.9  | 96.0  | 95.9  | 96.03 | 0.19 |
| MetaShift  |                      | 93.9  | 93.9  | 93.7  | 93.7  | 93.80 | 0.12 |
| Living17   |                      | 87.2  | 87.0  | 87.0  | 87.1  | 87.08 | 0.10 |


