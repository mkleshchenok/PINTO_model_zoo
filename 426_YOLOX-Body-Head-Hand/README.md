# Note (Body + Head + Hand)

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.10229410.svg)](https://doi.org/10.5281/zenodo.10229410)

Lightweight human detection model generated using a high-quality human dataset. I annotated all the data by myself. Extreme resistance to blur and occlusion. In addition, the recognition rate at short, medium, and long distances has been greatly enhanced. The camera's resistance to darkness and halation has been greatly improved.

`Head` does not mean `Face`. Thus, the entire head is detected rather than a narrow region of the face. This makes it possible to detect all 360° head orientations.

## 1. Dataset
  - COCO-Hand (14,667 Images, 66,903 labels, All re-annotated manually)
  - http://vision.cs.stonybrook.edu/~supreeth/COCO-Hand.zip
  - I am adding my own enhancement data to COCO-Hand and re-annotating all images. In other words, only COCO images were cited and no annotation data were cited.
  - I have no plans to publish my own dataset.
    ```
    body_label_count: 30,729 labels
    head_label_count: 26,268 labels
    hand_label_count: 18,087 labels
    ===============================
               Total: 66,903 labels
               Total: 14,667 images
    ```
    ![image](https://github.com/PINTO0309/PINTO_model_zoo/assets/33194443/22b56779-928b-44d8-944c-25431b83e24f)

## 2. Annotation

  Halfway compromises are never acceptable.

  ![000000000544](https://github.com/PINTO0309/PINTO_model_zoo/assets/33194443/557b932b-767b-4f8c-87f5-75f403fa9c50)

  ![000000000716](https://github.com/PINTO0309/PINTO_model_zoo/assets/33194443/9acb2308-eba1-4a05-91ed-ccbb6e122f67)

  ![000000002470](https://github.com/PINTO0309/PINTO_model_zoo/assets/33194443/c1809eeb-7b2c-41de-a519-9834c804c656)

  ![icon_design drawio (3)](https://github.com/PINTO0309/PINTO_model_zoo/assets/33194443/72740ed3-ae9f-4ab7-9b20-bea62c58c7ac)

## 3. Test
  - Python 3.10
  - onnxruntime-gpu v1.16.1 (TensorRT Execution Provider Enabled Binary)
  - opencv-contrib-python 4.8.0.76
  - numpy 1.24.3
  - TensorRT 8.5.3-1+cuda11.8

  ```
  usage: demo_yolox_onnx.py [-h] [-m MODEL] [-v VIDEO]

  options:
    -h, --help            show this help message and exit
    -m MODEL, --model MODEL
    -v VIDEO, --video VIDEO
  ```

  - 320x256 CPU Corei9

    ```bash
    python demo/demo_yolox_onnx.py \
    -m yolox_s_body_head_hand_post_0299_0.4983_1x3x256x320.onnx \
    -v 0
    ```

    https://github.com/PINTO0309/PINTO_model_zoo/assets/33194443/5d14b76e-daea-473f-8730-e3b0da0d0164

  - 160x128 CPU Corei9

    ```bash
    python demo/demo_yolox_onnx.py \
    -m yolox_s_body_head_hand_post_0299_0.4983_1x3x128x160.onnx \
    -v 0
    ```

    https://github.com/PINTO0309/PINTO_model_zoo/assets/33194443/9be1e3e0-afba-45b7-8f4f-24f4fb7e9340

  - [Gold-YOLO-n 320x256 CPU](https://github.com/PINTO0309/PINTO_model_zoo/tree/main/425_Gold-YOLO-Body-Head-Hand) vs YOLOX-Nano 320x256 CPU

    https://github.com/PINTO0309/PINTO_model_zoo/assets/33194443/9444e5ab-a8d3-4290-81e7-7d1701abca16

- Body-Head-Hand - Nano
  ```
  Average Precision  (AP) @[ IoU=0.50:0.95 | area=   all | maxDets=100 ] = 0.409
  Average Precision  (AP) @[ IoU=0.50      | area=   all | maxDets=100 ] = 0.717
  Average Precision  (AP) @[ IoU=0.75      | area=   all | maxDets=100 ] = 0.407
  Average Precision  (AP) @[ IoU=0.50:0.95 | area= small | maxDets=100 ] = 0.277
  Average Precision  (AP) @[ IoU=0.50:0.95 | area=medium | maxDets=100 ] = 0.554
  Average Precision  (AP) @[ IoU=0.50:0.95 | area= large | maxDets=100 ] = 0.687
  Average Recall     (AR) @[ IoU=0.50:0.95 | area=   all | maxDets=  1 ] = 0.135
  Average Recall     (AR) @[ IoU=0.50:0.95 | area=   all | maxDets= 10 ] = 0.380
  Average Recall     (AR) @[ IoU=0.50:0.95 | area=   all | maxDets=100 ] = 0.483
  Average Recall     (AR) @[ IoU=0.50:0.95 | area= small | maxDets=100 ] = 0.365
  Average Recall     (AR) @[ IoU=0.50:0.95 | area=medium | maxDets=100 ] = 0.632
  Average Recall     (AR) @[ IoU=0.50:0.95 | area= large | maxDets=100 ] = 0.729
  ```

- Body-Head-Hand - Tiny
  ```
  Average Precision  (AP) @[ IoU=0.50:0.95 | area=   all | maxDets=100 ] = 0.452
  Average Precision  (AP) @[ IoU=0.50      | area=   all | maxDets=100 ] = 0.756
  Average Precision  (AP) @[ IoU=0.75      | area=   all | maxDets=100 ] = 0.473
  Average Precision  (AP) @[ IoU=0.50:0.95 | area= small | maxDets=100 ] = 0.317
  Average Precision  (AP) @[ IoU=0.50:0.95 | area=medium | maxDets=100 ] = 0.601
  Average Precision  (AP) @[ IoU=0.50:0.95 | area= large | maxDets=100 ] = 0.718
  Average Recall     (AR) @[ IoU=0.50:0.95 | area=   all | maxDets=  1 ] = 0.143
  Average Recall     (AR) @[ IoU=0.50:0.95 | area=   all | maxDets= 10 ] = 0.410
  Average Recall     (AR) @[ IoU=0.50:0.95 | area=   all | maxDets=100 ] = 0.514
  Average Recall     (AR) @[ IoU=0.50:0.95 | area= small | maxDets=100 ] = 0.395
  Average Recall     (AR) @[ IoU=0.50:0.95 | area=medium | maxDets=100 ] = 0.662
  Average Recall     (AR) @[ IoU=0.50:0.95 | area= large | maxDets=100 ] = 0.759
  ```

- Body-Head-Hand - S
  ```
  Average Precision  (AP) @[ IoU=0.50:0.95 | area=   all | maxDets=100 ] = 0.498
  Average Precision  (AP) @[ IoU=0.50      | area=   all | maxDets=100 ] = 0.790
  Average Precision  (AP) @[ IoU=0.75      | area=   all | maxDets=100 ] = 0.522
  Average Precision  (AP) @[ IoU=0.50:0.95 | area= small | maxDets=100 ] = 0.343
  Average Precision  (AP) @[ IoU=0.50:0.95 | area=medium | maxDets=100 ] = 0.672
  Average Precision  (AP) @[ IoU=0.50:0.95 | area= large | maxDets=100 ] = 0.806
  Average Recall     (AR) @[ IoU=0.50:0.95 | area=   all | maxDets=  1 ] = 0.154
  Average Recall     (AR) @[ IoU=0.50:0.95 | area=   all | maxDets= 10 ] = 0.443
  Average Recall     (AR) @[ IoU=0.50:0.95 | area=   all | maxDets=100 ] = 0.557
  Average Recall     (AR) @[ IoU=0.50:0.95 | area= small | maxDets=100 ] = 0.425
  Average Recall     (AR) @[ IoU=0.50:0.95 | area=medium | maxDets=100 ] = 0.726
  Average Recall     (AR) @[ IoU=0.50:0.95 | area= large | maxDets=100 ] = 0.836
  ```

- Body-Head-Hand - M
  ```
  Average Precision  (AP) @[ IoU=0.50:0.95 | area=   all | maxDets=100 ] = 0.526
  Average Precision  (AP) @[ IoU=0.50      | area=   all | maxDets=100 ] = 0.809
  Average Precision  (AP) @[ IoU=0.75      | area=   all | maxDets=100 ] = 0.556
  Average Precision  (AP) @[ IoU=0.50:0.95 | area= small | maxDets=100 ] = 0.361
  Average Precision  (AP) @[ IoU=0.50:0.95 | area=medium | maxDets=100 ] = 0.703
  Average Precision  (AP) @[ IoU=0.50:0.95 | area= large | maxDets=100 ] = 0.860
  Average Recall     (AR) @[ IoU=0.50:0.95 | area=   all | maxDets=  1 ] = 0.160
  Average Recall     (AR) @[ IoU=0.50:0.95 | area=   all | maxDets= 10 ] = 0.464
  Average Recall     (AR) @[ IoU=0.50:0.95 | area=   all | maxDets=100 ] = 0.576
  Average Recall     (AR) @[ IoU=0.50:0.95 | area= small | maxDets=100 ] = 0.437
  Average Recall     (AR) @[ IoU=0.50:0.95 | area=medium | maxDets=100 ] = 0.751
  Average Recall     (AR) @[ IoU=0.50:0.95 | area= large | maxDets=100 ] = 0.885
  ```

- Post-Process

  Because I add my own post-processing to the end of the model, which can be inferred by TensorRT, CUDA, and CPU, the benchmarked inference speed is the end-to-end processing speed including all pre-processing and post-processing. EfficientNMS in TensorRT is very slow and should be offloaded to the CPU.

  ![image](https://github.com/PINTO0309/PINTO_model_zoo/assets/33194443/db5d5e1f-056c-45ea-9250-07559a7f57f1)

## 4. Citiation
  If this work has contributed in any way to your research or business, I would be happy to be cited in your literature.
  ```
  @software{YOLOX-Body-Head-Hand,
    author={Katsuya Hyodo},
    title={Lightweight human detection model generated using a high-quality human dataset},
    url={https://github.com/PINTO0309/PINTO_model_zoo/tree/main/426_YOLOX-Body-Head-Hand},
    year={2023},
    month={12},
    doi={10.5281/zenodo.10229410},
  }
  ```

## 5. Cited
  I am very grateful for their excellent work.
  - COCO-Hand

    https://vision.cs.stonybrook.edu/~supreeth/

    ```
    @article{Hand-CNN,
      title={Contextual Attention for Hand Detection in the Wild},
      author={Supreeth Narasimhaswamy and Zhengwei Wei and Yang Wang and Justin Zhang and Minh Hoai},
      booktitle={International Conference on Computer Vision (ICCV)},
      year={2019},
      url={https://arxiv.org/pdf/1904.04882.pdf}
    }
    ```
  - YOLOX

    https://github.com/Megvii-BaseDetection/YOLOX

    ```
    @article{yolox2021,
      title={YOLOX: Exceeding YOLO Series in 2021},
      author={Ge, Zheng and Liu, Songtao and Wang, Feng and Li, Zeming and Sun, Jian},
      journal={arXiv preprint arXiv:2107.08430},
      year={2021}
    }
    ```
  - YOLOX-Colaboratory-Training-Sample

    高橋かずひと https://github.com/Kazuhito00

    https://github.com/Kazuhito00/YOLOX-Colaboratory-Training-Sample


## 6. TODO
- [ ] Synthesize and retrain the dataset to further improve model performance. [CD-COCO: Complex Distorted COCO database for Scene-Context-Aware computer vision](https://github.com/aymanbegh/cd-coco)
  ![image](https://github.com/PINTO0309/PINTO_model_zoo/assets/33194443/69603b9b-ab9f-455c-a9c9-c818edc41dba)
  ```
  @INPROCEEDINGS{10323035,
    author={Beghdadi, Ayman and Beghdadi, Azeddine and Mallem, Malik and Beji, Lotfi and Cheikh, Faouzi Alaya},
    booktitle={2023 11th European Workshop on Visual Information Processing (EUVIP)},
    title={CD-COCO: A Versatile Complex Distorted COCO Database for Scene-Context-Aware Computer Vision},
    year={2023},
    volume={},
    number={},
    pages={1-6},
    doi={10.1109/EUVIP58404.2023.10323035}}
  ```