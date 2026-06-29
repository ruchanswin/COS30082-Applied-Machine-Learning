* Lab 5 - Transfer Learning Report

** Pre-trained model
- **MobileNetV2** with ImageNet weights (`include_top=False`)
- Head: GlobalAveragePooling2D → Dropout(0.2) → Dense(num_classes, softmax)

** Architecture
Full Keras `model.summary()` for `transfer_mobilenetv2` (state after fine-tuning).
Model: "transfer_mobilenetv2"
┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━┓
┃ Layer (type)                    ┃ Output Shape           ┃       Param # ┃
┡━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━┩
│ input_layer_1 (InputLayer)      │ (None, 224, 224, 3)    │             0 │
├─────────────────────────────────┼────────────────────────┼───────────────┤
│ mobilenetv2_1.00_224            │ (None, 7, 7, 1280)     │     2,257,984 │
│ (Functional)                    │                        │               │
├─────────────────────────────────┼────────────────────────┼───────────────┤
│ global_average_pooling2d        │ (None, 1280)           │             0 │
│ (GlobalAveragePooling2D)        │                        │               │
├─────────────────────────────────┼────────────────────────┼───────────────┤
│ dropout (Dropout)               │ (None, 1280)           │             0 │
├─────────────────────────────────┼────────────────────────┼───────────────┤
│ dense (Dense)                   │ (None, 10)             │        12,810 │
└─────────────────────────────────┴────────────────────────┴───────────────┘
 Total params: 5,659,488 (21.59 MB)
 Trainable params: 1,694,346 (6.46 MB)
 Non-trainable params: 576,448 (2.20 MB)
 Optimizer params: 3,388,694 (12.93 MB)
** Feature extraction vs fine-tuning
Stage | Val accuracy (last epoch) | Training time (s)
Feature extraction | 0.7476 | 1525.37
Fine-tuning | 0.7606 | 1860.15
Final validation accuracy after fine-tuning: 0.7606
