# Synthetic-Dataset-for-Adaptive-Testing
Dataset for "Test pattern prioritization and outlier detection for large-scale IC datasets(대규모 집적회로 데이터셋을 위한 테스트 패턴 우선순위 부여 및 outlier 검출 방법)", KTC 2024


> **Abstract**
>
> As the semiconductor manufacturing process has been scaling down, the integration of ICs has increased significantly. Also, test costs and complexity have increased exponentially. Therefore, it is required to reduce unnecessary test patterns by analyzing the importance of each test pattern and identifying outliers. In the adaptive testing process, the utilization of artificial neural network models can be used to reduce the test processing and storage costs of test patterns and results. To this end, this study releases a dataset that consists of test patterns generated by ATPG based on the ISCAS’85 benchmark circuit. Experimental results on the dataset show that the importance of test patterns can be determined with high accuracy and reliability.

* Authors: Wan Soo Kim, Dae Ryong Shin, Ji Soo Shin, Gyeong Dong Yang, Su Min Oh, Hyun Jin Kim

## 1. 데이터 구성

데이터셋은 총 110장의 wafer로 구성되어 있다.
11개의 조합회로에 대해 11개의 wafer 단위 데이터로 구성되며, 각 조합회로는 서로 다른 10개의 Fault 발생 확률분포를 가진 wafer 10장으로 구성된다.

![images](https://github.com/EmPasLab/Synthetic-Dataset-for-Adaptive-Testing/blob/main/pattern_list.png)


1. Cosine: Cosine 함수를 따르는 확률 분포

2. Cosine abs: 3개의 fault peak point를 갖는Cosine 분포의 절대값을 따르는 확률 분포

3. Sin abs: 3개의 fault peak point를 갖는 Sine 분포의 절대값을 따르는 확률 분포

4. Geometric: 초반에 높은 확률을 갖으며 비례적으로 개수가 감소하는 분포

5. Log normal: 로그를 취한 값이 정규 분포를 이루는 확률 변수의 분포

6. Multimodal: 하나의 확률 변수에 대해 여러 개의 fault peak point를 갖는 분포

7. Normal: 표준 정규 분포

8. Sparse: 대부분의 데이터가 0 또는 근접한 값에 집중되어 있는 확률 분포

9. Dense: 데이터가 공간적으로 높은 밀도를 가지고 분포해 있는 확률 분포

10. Step: 특정 지역에 집중적인 fault peak point를 갖는 확률 분포


## 2. 데이터 분할

110장의 wafer가 존재하므로, 총 110K의 회로로 구성된다. 
인공지능 모델 학습을 위한 Train data 및 Test data는 7:3의 비율로 분할하였다. 

# 3. 데이터 형식(예시)
'''
0001110000001011001110011001100100000111111 1
0011110010011001001111000110000100111011010 0
1101001111110111110100111100100000000110100 1
1100000000011011011010110001011101010110000 0
0110100010010101010101010100011010111000001 2
1000010110110010010000111011001111011111100 0
0001011111000101000001000000000110001111101 0
0011111111010000001111000011011010100111110 0
0111000011011010010110001101101110111101110 0
0000100011010000001001110010100101011111110 1
'''

테스트 패턴 및 출력 결과는 input으로, 검출 fault 개수는 label로 구성하였다.
