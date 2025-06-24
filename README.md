# Fingerprint

### Dataset 설명
- 본 데이터셋은 공유가 불가능하기에 아래 표로 나타냄

![image](https://github.com/user-attachments/assets/f08f4fd4-6a15-4064-b1be-5014f7d8ced3)
![image](https://github.com/user-attachments/assets/9199bd0f-1857-40b2-bfc6-d31f5b3fccbc)

### Augmentation
- Center crop
- Left Right Flip
- Up Down Flip
- Rotation

**총 16배로 증강**

- Resize (192, 192)
  - 처음 교수님이 공유해주신 예시 모델이 192x192 size로 되어 있었기에 (192, 192)로 Resize 진행

### Model
- 첫 Custom Model을 실행해 볼때는 원본 이미지로만 실행해보았음
- 하이퍼파라미터를 변경하며 학습해본 결과 Conv2d layer의 kernel의 size는 (3, 3)이 최적이며 Maxpooling의 pool size는 (2, 2)가 최적이라는 것을 알게됨
- layer를 깊게 쌓으니 Acurracy 성능이 향상되었지만 너무 깊게 쌓이니 parameter가 0으로만 계산되면 성능이 오르지 않음
- Augmentation을 진행 후 다시 실행해본 결과 Acurracy 성능 소폭 상승
- 이미지를 Resize 하는 과정에서 이미지의 화질이 뭉개지는 현상이 있으며 이로 인해 특징이 불분명해짐
- Resize를 하지 않고 Crop size를 설정하여 진행해본 결과 Acurracy 성능 대폭 상승
- 더 이상 성능이 오르지 않으며 Augmentation을 더 진행하기에는 연구실 PC의 메모리 부족으로인해 타 모델을 실험
- 타 모델에 input으로 넣기 위해 이미지 사이즈를 (224, 224)로 Center crop
- 대표적인 모델인 VGG와 ResNet을 직접 구현하여 실해해본결과 성능이 94%까지 상승
- 적은 데이터셋에 최적인 SlimResNet을 활용하여 96% 달성
