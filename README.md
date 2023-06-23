# PHM For Sound

# 목차

1. 문제

2. MFCC와 Mel-Spectogram
   - MFCC
   - Mel-Spectogram

3. librosa 모듈의 MFCC 파라미터


# 문제와 배경지식

이 산업 시설에 적용되는 AI 기술은 대부분 이미지 데이터에 기반하고 있다. 그러나 이미지 데이터는 크기가 클수록 이동, 분석, 그리고 적용에 많은 비용이 발생한다는 단점이 있다. 따라서 상대적으로 데이터 크기가 작은 음향 데이터를 활용할 수 있다면, 보다 적은 비용으로 예측할 수 있을 것이다.


# MFCC와 Mel-Spectogram

기존의 컴퓨팅 파워가 부족할 때에는 연산량이 적인 MFCC를 무조건적으로 선호하였다면, 최근에는 학습에 GPU 이용이 가능해짐에 따라 Mel-Spectogram을 특징으로 뽑아서 쓰는 경우도 많다.

둘의 차이점은 Correlate와 De-Correlate이다. Mel Spectogram의 경우 주파수끼리 연관하기 때문에 도메인이 한정적인 문제에서 더 좋은 성능을 보이고 MFCC는 연관하지 않기 때문에 일반적인 상황에서 더 좋은 성능을 보인다.

## Mel-Spectogram

![Example instance](https://github.com/bloodmage1/PHM_sound/blob/main/mel_filter1.png)

달팽이관의 특성을 고려해서 낮은 주파수에서는 작은 삼각형의 필터를 가지고, 고주파 대역으로 갈수록 넓은 삼각형의 필터를 가진다고 생각하면 된다.

![Example instance](https://github.com/bloodmage1/PHM_sound/blob/main/mel_filter2.png)

그래서 위와 같은 삼각형 필터 n개를 모두 적용한 필터를 멜 필터 뱅크라고 부른다. 그래서 멜 스펙토그램이라는 특징이 만들어 진다.

# librosa 모듈의 MFCC 파라미터

[librosa.feature.mfcc](https://librosa.org/doc/latest/index.html)

y: time domain audio signal

sr: sampling rate

S: log mel-spectogram

n_mfcc: mfcc coefficient 개수

dct_type: 1 or 2 or 3

norm: if dct type == 1 -> ortho else, 없어도 됨

mfcc는 음성데이터를 특징벡터화 해주는 알고리즘으로 머신러닝에서 어떤 데이터를 벡터화하는 것은 곧 학습이 가능하다는 의미이기 때문에 상당히 중요한 부분이라고 할 수 있다.