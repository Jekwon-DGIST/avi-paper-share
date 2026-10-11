# 목표 저널 및 투고 계획

## 목표 저널

Control Engineering Practice

Special Issue: Precision Motion Systems and Control

투고 마감: 2026년 12월 31일 (첨부 이미지 기준)

## 투고 계획 · 작성란

연구 제목: 작업 영역의 진동 요구조건을 고려한 CPD 기반 6-DOF AVI 제어

투고 일정 및 교수님 검토 요청 사항: 여기에 작성해 주세요.

![Control Engineering Practice 목표 저널 및 특별호 안내](images/figure_01.png)

사용자가 제공한 목표 저널 및 특별호 안내 이미지 · 클릭하여 확대

# Abstract

기존 연구 : 제진대 상판의 기하학적 중심의 제진 성능만 고려하여 제어기를 설계함.제안 연구 : 제진대 상판의 모든 작업 영역의 제진 성능을 고려하여 제어기를 설계함.

정밀 장비를 위한 6-DOF 능동 제진 시스템에서는 상판의 기하학적 중심에서 목표 제진 성능을 만족하더라도, 병진·회전 운동의 결합으로 인해 작업 영역 내 다른 위치에서 동일한 성능을 확보하기 어렵다. 특히 무게 불균형은 Cartesian-domain의 운동 사이에 coupling을 유발하여 위치별 진동 응답과 제어기 설계를 복잡하게 만든다. 본 연구에서는 작업 영역 내 평가 위치에 주어진 Cartesian-domain의 진동 요구조건을 CPD-domain의 모드별 제어기 설계 기준으로 배분하는 방법을 제안한다. 측정 주파수 응답에 CPD 디커플링을 적용하여 제어 채널을 구성하고, 강체의 위치 변환 관계를 이용하여 중심의 병진·회전 응답으로부터 평가 위치의 진동 스펙트럼을 추정한다. 모드 간 cross spectrum을 고려한 기여도에 따라 위치별 요구조건을 배분하고, 각 모드에서 가장 엄격한 조건을 sensitivity weighting으로 설정한다. 제안 방법은 기하학적 중심의 성능만을 고려하는 방법 및 Cartesian-domain에서 제어기를 설계하는 방법과 비교하며, 작업 영역 내 평가 위치의 제어 후 PSD를 바탕으로 목표 진동 기준 충족 여부를 평가한다.

![실험용 제진대와 평가 위치 P1~P5](images/figure_02.png)

실험용 제진대와 평가 위치 P1~P5

![Position 1~5의 XYZ 가속도 PSD: Baseline1, Baseline2 및 Proposed 비교](images/figure_03.png)

Position 1~5의 XYZ 가속도 PSD: Baseline1, Baseline2 및 Proposed 비교

Keywords: Active vibration isolation; CPD decoupling; Evaluation region; Modal requirement allocation; Sensitivity weighting

# Introduction

[시스템 설명] Active Vibration Isolation System의 필요성정밀 장비의 성능을 확보하기 위해서는 지면에서 전달되는 진동을 효과적으로 저감해야 한다. Passive isolation system은 공진 주파수 부근과 그 이하의 저주파수 영역에서 진동 저감에 한계가 있다. AVI system은 센서로 측정한 진동 응답을 바탕으로 actuator의 제어력을 조절하여 이러한 한계를 보완한다. 특히 여러 방향의 제진이 요구되는 시스템에서는 복수의 센서와 actuator를 이용해 상판의 6자유도 운동을 제어하므로, 이를 multi-input multi-output (MIMO) control problem으로 다룬다.

[문제점 언급] Payload 비대칭으로 인해 병진 회전 간 coupling 발생함.또한 실제 vibration isolation system에서는 payload의 위치와 질량 분포가 이상적으로 대칭적이지 않은 경우가 많다. 이 경우 상판의 기하학적 중심과 전체 시스템의 center of mass 및 principal inertia axes가 일치하지 않으며, 병진 운동과 회전 운동 사이에 coupling이 발생한다. 그 결과 Cartesian coordinate에서 특정 방향으로 인가된 generalized force 또는 moment가 다른 방향의 응답까지 함께 유발하므로, 각 Cartesian channel에 독립적으로 controller를 설계하더라도 channel 간 상호작용으로 인해 기대한 성능을 얻기 어려울 수 있다.[선행 연구 설명] 모델 기반 디커플링의 한계점시스템의 결합 동특성을 나타내는 모델이 필요함.여러 입출력 채널의 상호작용을 함께 고려해야 하므로 제어기 설계 복잡도가 증가함.이러한 multichannel interaction을 완화하기 위해 다양한 model-based decoupling approaches가 연구되어 왔다. Lee et al. [1]은 6-DOF AVI의 state-space model을 기반으로, 한 방향의 제어 명령이 다른 방향의 운동을 유발하지 않도록 여러 actuator 입력을 동시에 결정하는 noninteracting MIMO controller를 제안하였다. 이를 위해 closed-loop system의 decoupling condition을 유도하고, stability와 control performance를 만족하는 controller gain을 LMI를 통해 결정하였다. Gong et al. [2]은 payload 교체와 redundant actuation으로 달라지는 nonlinear dynamics에 대응하기 위해 neural-network inverse model을 이용한 decoupling을 제안하였다. 이러한 방법들은 channel interaction을 controller 또는 inverse model의 설계 단계에서 직접 다룰 수 있지만, 시스템의 자유도와 configuration 변화가 커질수록 필요한 모델, 제약조건 및 controller structure도 함께 복잡해질 수 있다.[CPD 관련 선행 연구 설명] Modal space의 장점과 기존 연구들의 한계점장점 :결합된 시스템을 모드별 채널로 분리하여 개별 제어기 설계가 가능함.CPD는 명시적인 시스템 모델 없이 측정 FRF를 이용하여 디커플링 변환을 구함.한계점 :Cartesian-domain의 평가 위치에 주어진 진동 요구조건을 모드별 제어기 설계 기준으로 연결하는 방법이 충분히 다뤄지지 않음.이러한 coupling을 하나의 완전 결합된 MIMO controller에서 직접 처리하는 대신, modal-space decoupling은 결합된 physical coordinates를 modal coordinates로 변환하여 system dynamics를 서로 독립적인 modal channels로 분리한다. 이상적인 decoupling 조건에서는 변환된 dynamics가 대각 구조를 가지므로, 6자유도 MIMO tuning problem을 복수의 SISO loop-shaping problems로 단순화할 수 있다. 이에 따라 각 mode의 stability와 vibration-isolation performance를 개별적으로 설정하고 검증할 수 있다. 따라서 modal-space decoupling은 다변수 상호작용을 controller 설계 과정에서 직접 조정해야 하는 부담을 줄이고, mode별 요구조건에 따라 controller를 체계적으로 설계할 수 있게 한다.이러한 장점을 이용하여 Heertjes et al. [3]은 6자유도 rigid-body system의 질량 및 강성 특성을 모델링하고, 이로부터 구한 mode shapes를 이용하여 Cartesian generalized coordinates와 control inputs를 modal coordinates와 modal forces로 변환하였다. 이를 통해 결합된 system dynamics를 독립적인 modal channels로 분리하고, 불안정 mode의 stability를 확보하는 동시에 각 mode의 vibration-isolation performance를 개별적으로 조정하기 위한 loop shaping을 수행하였다. 그러나 이러한 model-based modal transformation을 구성하기 위해서는 시스템의 질량 및 강성 특성과 modal information이 필요하며, payload 또는 system configuration이 변경되면 transformation을 다시 구성해야 할 수 있다.한편 Stoev et al. [5]은 명시적인 parametric model 대신 측정된 nonparametric frequency response function (FRF)을 이용하는 Canonical Polyadic Decomposition (CPD) 기반 decoupling 방법을 제안하였다. 이 방법은 여러 주파수에서 측정한 MIMO FRF를 하나의 tensor로 구성하고, CPD를 통해 해당 주파수 데이터에 공통으로 적용되는 정적 입출력 transformation을 구한다. 이에 따라 복잡한 물리모델을 직접 식별하지 않고도 MIMO dynamics를 근사적으로 대각화하고, 변환된 CPD channels에서 controller를 개별적으로 설계할 수 있다.

그러나 CPD 기반 decoupling은 측정된 MIMO dynamics를 독립적인 modal channels로 변환하는 방법을 제공하지만, 실제 장비의 평가 위치에서 Cartesian coordinates를 기준으로 정의되고 측정된 performance requirements를 각 modal channel의 controller design conditions와 연결하는 방법까지 제공하지는 않는다.

Heertjes et al. [3]은 질량 및 강성 행렬에 기반하여 시스템을 modal space로 변환한 뒤, 각 모드에 PID와 2차 low-pass filter로 구성된 제어기를 설계하였다. 모드별 loop shaping을 통해 불안정 모드를 안정화하고, 저주파 외란 억제와 공진 부근의 감쇠를 확보하면서 고주파 영역의 passive isolation 특성을 유지하였다. 그러나 이 연구는 모드별 안정성과 주파수 응답의 개선을 중심으로 설계를 수행하였으며, Cartesian space에서 정의되고 측정되는 진동 성능 기준을 modal-space controller의 정량적인 설계 조건으로 변환하는 방법은 제시하지 않았다.
Ding et al. [4]은 6-DOF 시스템을 modal space로 변환한 뒤, 각 모드의 transmissibility와 센서 노이즈의 영향을 고려하여 frequency-shaped sliding surface를 최적화하였다. 이 과정에서 modal transformation을 통해 Cartesian motion에 대한 각 모드의 영향이 간접적으로 반영되며, 각 modal channel에는 공진 peak와 특정 주파수에서의 transmissibility를 제한하는 성능 조건이 부여된다. 이어서 설계된 전달 특성을 구현하고 직접 외력에 대한 compliance를 낮추기 위한 regulator를 설계하였다. 그러나 성능 평가는 상판 중심에서 정의된 6자유도 generalized motion에 한정되며, 중심에서 떨어진 평가 위치의 방향별 진동 기준을 각 modal channel의 정량적인 설계 조건으로 연결하는 문제는 다루지 않았다.
Wu and Chen [7]은 차량 현가장치의 상태공간 모델을 modal coordinates로 변환한 뒤, 관심 모드에 대한 상태 가중치와 제어 입력 가중치를 이용하여 LQR 및 H∞ 상태 피드백 제어기를 설계하였다. 이 접근은 관심 모드에 선택적으로 가중치를 부여하여 해당 공진의 억제를 제어기 설계에 직접 반영하고, control effort를 고려하여 성능을 비교한다. 그러나 modal weight는 설계자가 정하는 상대적인 tuning parameter이며, Cartesian space에서 정의되고 측정되는 정량적인 진동 성능 기준으로부터 도출되지 않는다. 따라서 Cartesian 성능 기준과 modal-space controller의 설계조건 사이의 정량적인 관계는 제시되지 않았다.

본 논문에서는 상판의 성능 평가 영역에서 Cartesian coordinates를 기준으로 정의되는 방향별 vibration requirements를 CPD 기반 modal-space controller의 설계조건으로 연결하는 방법을 제안한다. 단일 target position에 대해서만 제어 성능을 설정하는 대신, 상판의 rigid-body motion과 위치별 좌표변환 관계를 이용하여 평가 영역 내 여러 위치의 방향별 진동 응답을 함께 고려한다. 중심의 센서 신호와 위치 변환으로 추정한 각 평가 위치의 진동 수준과 목표 성능으로부터 주파수별 저감 요구량을 도출하고, 이를 CPD modal channels의 제어기 설계조건으로 변환한다. 이후 채널별 sensitivity weighting을 구성함으로써, 상판의 평가 위치가 달라지는 경우에도 해당 위치에서 요구되는 진동 성능을 일관되게 반영할 수 있도록 modal controller를 설계한다.
[Contribution] 본 연구의 Contribution을 정리함본 논문의 주요 기여는 다음과 같다.

상판의 성능 평가 영역에서 정의된 방향별 요구조건에 기반한 modal-space 제어기 설계 방법을 제안한다. 방향별로 필요한 진동 저감량을 관련 CPD channels에 주파수별로 배분하고, 이를 sensitivity weighting과 연결하여 modal controller의 설계 기준을 설정한다.
단일 target position에 종속되지 않고 상판의 성능 평가 영역을 고려하는 설계 방법을 제안한다. 상판의 rigid-body motion과 위치별 좌표변환 관계를 이용하여 평가 영역 내 위치에 따른 방향별 진동 응답을 설계에 반영함으로써, 평가 위치가 달라지는 경우에도 해당 위치에서 요구되는 진동 성능을 만족하도록 한다.
제안한 설계 방법을 6-DOF AVI 시스템의 실험을 통해 검증한다. 서로 다른 상판 위치에서 방향별 진동 응답을 측정하고, 제안한 modal controller가 위치별 성능 요구조건을 만족하는지 확인한다. 또한 중심만 고려한 CPD 제어 및 동일한 공간 요구조건을 사용하는 Cartesian 대각 제어와 비교하여 진동 저감 성능과 control effort 측면의 효과를 평가한다.
본 논문의 나머지 구성은 다음과 같다. Section 2에서는 6-DOF AVI 시스템의 동역학과 CPD 기반 decoupling 방법을 설명하고, 변환 전후의 FRF를 이용하여 decoupling 성능을 평가한다. Section 3에서는 상판의 성능 평가 영역에 적용되는 방향별 진동 요구조건을 주파수 영역의 설계 기준으로 나타내고, physical-space의 방향별 요구조건을 CPD modal channels에 배분할 때 발생하는 문제를 정식화한다. Section 4에서는 동시 측정한 시계열의 PSD와 cross spectrum을 이용하여 각 CPD channel의 위치·방향별 기여도를 분석하고, 이를 바탕으로 modal requirement를 배분하여 채널별 controller를 설계하는 방법을 제안한다. Section 5에서는 실험 장치와 비교 방법을 설명하고, 6-DOF AVI 시스템에서 제안 방법의 evaluation-region 제진 성능을 검증한다. 마지막으로 Section 6에서 본 연구의 결과를 요약하고 결론을 제시한다.

# System Description

## 2.1 Active Vibration Isolation System and Evaluation Region

[시스템 구조] 모듈형 제진대의 구조 설명본 연구에서 고려하는 6자유도 AVI 시스템은 강체 상판과 base platform 사이에 두 개의 vibration isolation module이 배치된 모듈형 구조로 구성된다. 각 module은 상판의 정적 하중을 지지하는 passive support와 능동 제어력을 발생시키는 actuator 및 상판의 운동을 측정하는 sensor로 구성된다. 두 module에 배치된 actuator의 힘을 조합하여 상판 중심에 세 방향의 병진력과 세 방향의 회전 모멘트를 발생시키고, 이를 통해 상판의 6자유도 운동을 제어한다.
Figure 1. Configuration of the 6-DOF active vibration isolation system, the platform evaluation region, and the coordinate systems associated with the performance-evaluation locations.
[좌표계 정의] 지면·상판 중심·평가 위치의 좌표계와 작업 영역을 정의함.Fig. 1과 같이 지면 진동이 입력되는 위치에는 ground coordinate system {G}를, 제진대 상판의 기하학적 중심에는 center coordinate system {C}를 정의한다. Center coordinate system {C}는 상판의 geometric center에 고정된다. 또한 장비가 설치되거나 진동 성능이 평가될 수 있는 상판의 영역을 𝒜로 정의하고, 이 영역에서 성능 요구조건의 적용 대상이 되는 위치들의 집합을 𝒫={r1,…,rNT}⊂𝒜로 정의한다. 각 위치 rp∈𝒫에는 evaluation coordinate system {Tp}를 두며, 그 축 방향은 center coordinate system {C}와 동일하게 정의한다.
Ground와 상판 중심의 운동은 각각 qG와 qC로 나타내고, 평가 위치 rp∈𝒫에서의 운동은 qT,p로 나타낸다. 각 운동은 다음의 6자유도 generalized coordinate를 사용한다.
\[\boldsymbol{q}_{K}(t)=\begin{bmatrix}x_K & y_K & z_K & \theta_{x,K} & \theta_{y,K} & \theta_{z,K}\end{bmatrix}^{\mathsf{T}},\qquad K\in\{G,C,T_p\},\quad p=1,\ldots,N_T\]
상판 중심의 generalized acceleration은 vibration isolation modules에 배치된 feedback sensors의 측정 신호로부터 산출되어 controller의 feedback signal로 사용된다. Ground coordinate의 진동과 각 평가 위치 rp∈𝒫의 motion은 별도의 evaluation sensors로 측정하며, 이를 이용하여 위치별 제진 성능을 평가한다. 실제 실험에서 측정하는 motion components는 Section 5의 sensor configuration에서 구체적으로 정의한다.
[합차 모드 변환] Generalized coordinate 변환 과정 설명개별 actuator에서 발생하는 force를 모은 vector를 fa(t)로 나타낸다. Actuator의 배치와 작용 방향을 고려하여 개별 actuator forces를 조합하면, 상판 중심의 x, y, z 병진 방향과 roll, pitch, yaw 회전 방향에 대응되는 generalized control input을 구성할 수 있다. 이러한 actuator configuration을 matrix Ba로 나타내면, actuator force vector와 상판 중심의 6자유도 generalized control input 사이의 관계는 다음과 같이 표현된다.
\[\boldsymbol{f}_{a}(t)=\begin{bmatrix}f_{a,1}(t)&\cdots&f_{a,N_a}(t)\end{bmatrix}^{\mathsf{T}},\qquad \boldsymbol{u}(t)=\boldsymbol{B}_{a}\boldsymbol{f}_{a}(t),\qquad \boldsymbol{B}_{a}\in\mathbb{R}^{6\times N_a}\]
\[\boldsymbol{u}(t)=\begin{bmatrix}u_x & u_y & u_z & u_{\theta,x} & u_{\theta,y} & u_{\theta,z}\end{bmatrix}^{\mathsf{T}}\]
Controller에서 계산된 generalized input은 Ba의 right pseudoinverse를 이용하여 개별 actuator forces로 할당된다. Ba가 full row rank인 경우 actuator force command는 다음과 같이 계산된다.
\[\boldsymbol{f}_{a}(t)=\boldsymbol{B}_{a}^{+}\boldsymbol{u}(t),\qquad \boldsymbol{B}_{a}^{+}=\boldsymbol{B}_{a}^{\mathsf{T}}\left(\boldsymbol{B}_{a}\boldsymbol{B}_{a}^{\mathsf{T}}\right)^{-1}\]
각 vibration isolation module에 배치된 feedback sensor에서 측정한 가속도 신호를 모은 vector를 as(t)로 나타낸다. Sensor의 위치와 측정 방향으로 구성되는 matrix를 Bs라고 하면, sensor signals와 상판 중심의 generalized acceleration 사이의 관계는 다음과 같다. Actuator와 feedback sensor가 collocated되고 동일한 순서로 배치된 특별한 경우에는 Bs=Ba로 둘 수 있다.
\[\boldsymbol{a}_{s}(t)=\boldsymbol{B}_{s}^{\mathsf{T}}\ddot{\boldsymbol{q}}_{C}(t),\qquad \ddot{\boldsymbol{q}}_{C}(t)=\left(\boldsymbol{B}_{s}^{\mathsf{T}}\right)^{+}\boldsymbol{a}_{s}(t),\qquad \boldsymbol{B}_s\in\mathbb R^{6\times N_s}\]

[다이나믹스] 제진대 다이나믹스를 설명함.상판을 강체로 가정하고 회전각이 충분히 작다고 가정한다. 또한 각 vibration isolation module의 passive support를 선형 강성과 감쇠 요소로 모델링하면, passive force는 상판과 base platform 사이의 상대 변위 및 상대 속도에 의해 결정된다. 이에 따라 상판 중심에서의 6자유도 운동방정식은 다음과 같이 표현된다.
\[\boldsymbol{M}\ddot{\boldsymbol{q}}_{C}(t)+\boldsymbol{D}\left[\dot{\boldsymbol{q}}_{C}(t)-\dot{\boldsymbol{q}}_{G}(t)\right]+\boldsymbol{K}\left[\boldsymbol{q}_{C}(t)-\boldsymbol{q}_{G}(t)\right]=\boldsymbol{u}(t)\]
여기서 M, D 및 K는 center coordinate system {C}에서 정의되는 6×6 generalized mass, damping and stiffness matrices이다. M은 상판과 payload의 질량 및 회전 관성으로 구성되며, D와 K는 두 vibration isolation module에 포함된 passive support의 감쇠 및 강성 특성을 상판 중심으로 변환하여 구성된다. 각 행렬의 구체적인 구조와 mass imbalance에 따른 coupling은 다음 절에서 설명한다.
시간영역 변수 qK(t)와 u(t)의 Laplace transform을 각각 QK(s)와 U(s)로 나타내며, generalized acceleration의 Laplace-domain 표현은 AK(s)=s²QK(s)로 나타낸다. Generalized control input에서 상판 중심 변위까지의 compliance는 다음과 같다.
\[\boldsymbol{P}_{\mathrm{CU}}(s)=\left(\boldsymbol{M}s^2+\boldsymbol{D}s+\boldsymbol{K}\right)^{-1}\]
상판 중심의 가속도 응답은 feedback sensor와 signal-conditioning 과정이 포함된 측정 경로를 통해 controller에 전달된다. 이 경로의 dynamics를 Hfb(s)로 나타내면, 실제 상판 중심의 generalized acceleration과 feedback에 사용되는 measured generalized acceleration 사이의 관계는 다음과 같다.
\[\boldsymbol{A}_{C}^{\mathrm{meas}}(s)=\boldsymbol{H}_{\mathrm{fb}}(s)\boldsymbol{A}_{C}(s),\qquad \boldsymbol{H}_{\mathrm{fb}}(s)\in\mathbb{C}^{6\times6}\]
이를 이용하면 generalized actuator input에 대한 measured center acceleration response와 이에 대응하는 FRF는 다음과 같이 정의된다.
\[\boldsymbol{A}_{C}^{\mathrm{meas}}(s)=\boldsymbol{G}_{\mathrm{CU}}(s)\boldsymbol{U}(s),\qquad \boldsymbol{G}_{\mathrm{CU}}(s)=\boldsymbol{H}_{\mathrm{fb}}(s)s^2\boldsymbol{P}_{\mathrm{CU}}(s)\]
[작업 영역 설명] 정밀 작업 영역과 기하학적 중심의 관계를 설명함.상판 중심에서 평가 위치 {Tp}까지의 위치 벡터를 rp=[rx,p  ry,p  rz,p]T라고 하자. Small-angle rigid-body assumption에서 해당 위치의 motion은 상판 중심의 병진 및 회전 운동을 이용하여 다음과 같이 표현된다.
\[\boldsymbol{q}_{T,p}(t)=\boldsymbol{J}_{\mathrm{TC}}(\boldsymbol{r}_p)\boldsymbol{q}_{C}(t),\qquad \boldsymbol{J}_{\mathrm{TC}}(\boldsymbol{r}_p)=\begin{bmatrix}\boldsymbol{I}_{3}&-[\boldsymbol{r}_{p}]_{\times}\\\boldsymbol{0}_{3}&\boldsymbol{I}_{3}\end{bmatrix}\]
여기서 [rp]×는 rp의 skew-symmetric matrix이다. 회전속도의 제곱에 비례하는 구심가속도 항을 무시하는 선형화된 small-motion 조건에서는 동일한 변환이 속도와 가속도에도 적용된다. 따라서 동일한 center motion에서도 평가 위치에 따라 generalized vibration response가 달라진다.

현재 구현에서는 구동기 단 피에조 센서 시계열에 Ty를 적용하여 중심 좌표의 신호를 구성하고, Sensor_Nominal_Model의 공통 역응답을 주파수 영역에서 적용하여 실제 가속도 PSD를 추정한다. 목표 위치의 진동은 중심의 병진·회전 정보와 \(\boldsymbol{J}_{\mathrm{TC}}\)로 추정하며, 별도의 evaluation sensors는 이 예측과 제어 성능을 확인하는 데 사용한다.

## 2.2 CPD-Based Decoupling

[커플링 발생 원인] 무게 편심으로 인한 커플링 발생 원인을 설명함.Payload가 상판 중심에 대해 비대칭적으로 배치되면 center coordinate system {C}와 전체 시스템의 center of mass가 일치하지 않는다. Payload의 질량을 me, 상판 중심에서 payload의 center of mass까지의 위치 벡터를 pe = [lx  ly  lz]T라고 하자. 이때 6자유도 generalized mass matrix는 다음과 같은 block form으로 나타낼 수 있다 [8].
\[\boldsymbol{M}=\begin{bmatrix} m_{t}\boldsymbol{I}_{3} & -m_{e}[\boldsymbol{p}_{e}]_{\times} \\ m_{e}[\boldsymbol{p}_{e}]_{\times} & \boldsymbol{J}_{C} \end{bmatrix}\]
여기서 mt는 상판과 payload를 포함한 전체 질량, JC는 center coordinate system {C}에 대한 회전 관성행렬이며, [pe]×는 pe의 skew-symmetric matrix이다. 따라서 pe = 0이면 병진 운동과 회전 운동 사이의 block이 사라지지만, pe ≠ 0이면 ±melx, ±mely, ±melz 형태의 비대각 성분이 발생한다. 이는 한 방향의 병진 가속도가 회전 모멘트를 만들고, 회전 가속도가 병진력으로 나타나는 inertial coupling을 의미한다.
Mass imbalance에 의한 coupling mechanism을 설명하기 위한 nominal model에서는 passive supports가 대칭적으로 배치되고 center coordinate의 축이 주 강성축과 일치한다고 가정하여 damping 및 stiffness matrix를 다음의 대각행렬로 나타낸다.
\[\boldsymbol{D}=\operatorname{diag}(d_x,d_y,d_z,d_{\theta,x},d_{\theta,y},d_{\theta,z}),\qquad \boldsymbol{K}=\operatorname{diag}(k_x,k_y,k_z,k_{\theta,x},k_{\theta,y},k_{\theta,z})\]
[CPD 설명] CPD가 어떻게 AVI 시스템을 디커플링하는지 설명함.이 nominal model에서는 mass imbalance가 운동 방향 사이의 주된 coupling 원인이 된다. 실제 시스템에서는 support, actuator 및 sensor 배치의 오차와 비이상적인 dynamics로 인해 추가적인 coupling이 존재할 수 있으며, 이후의 CPD는 이러한 원인을 개별적으로 모델링하지 않고 측정된 MIMO FRF에 포함된 전체 coupling을 대상으로 한다.
본 연구에서는 이러한 frequency-dependent coupling을 줄이기 위해 Stoev et al. [5]의 nonparametric FRF 기반 Canonical Polyadic Decomposition (CPD)을 적용한다.
Nω개의 주파수에서 측정한 complex MIMO FRF GCU(jωk) ∈ ℂNy×Nu를 output, input 및 frequency 축으로 배열한다. Real-valued input과 output transformations를 얻기 위해 complex FRF의 real part와 imaginary part를 frequency mode에 연속하여 쌓고, 다음의 augmented real-valued tensor를 구성한다.
\[\breve{\mathcal{G}}^{[k]}=\operatorname{Re}\!\left\{\boldsymbol{G}_{\mathrm{CU}}(j\omega_k)\right\},\qquad \breve{\mathcal{G}}^{[N_{\omega}+k]}=\operatorname{Im}\!\left\{\boldsymbol{G}_{\mathrm{CU}}(j\omega_k)\right\}\]
\[k=1,\ldots,N_{\omega},\qquad \breve{\mathcal{G}}\in\mathbb{R}^{N_y\times N_u\times 2N_{\omega}}\]
여기서 \(\breve{\mathcal{G}}^{[k]}\)는 tensor \(\breve{\mathcal{G}}\)의 k번째 frontal slice를 나타낸다.
Figure 2. CPD of the MIMO frequency-response tensor. The real and imaginary parts of the complex FRFs are concatenated along the third mode.
Fig. 2와 같이 rank-R CPD는 augmented FRF tensor를 R개의 rank-one tensors와 residual tensor로 분해한다 [5].
\[\breve{\mathcal{G}}\approx\sum_{r=1}^{R}\boldsymbol{u}_{y,r}\circ\boldsymbol{u}_{u,r}\circ\boldsymbol{u}_{\omega,r}+\mathcal{E}\]
여기서 Uy = [uy,1 ⋯ uy,R], Uu = [uu,1 ⋯ uu,R] 및 Uω = [uω,1 ⋯ uω,R]는 각각 output, input 및 frequency modes의 factor matrices이고, CPD는 residual tensor E의 Frobenius norm을 최소화하도록 이 factors를 결정한다. 본 연구에서는 6개의 generalized input–output channels에 대응하는 여섯 개의 decoupled channels를 구성하기 위해 target rank를 R = 6으로 설정한다.
Frequency factor의 real 및 imaginary components를 결합하면 각 CPD channel의 complex frequency response를 얻을 수 있다. 이에 따라 k번째 주파수에서 측정된 FRF는 다음과 같이 나타낼 수 있다.
\[\boldsymbol{G}_{\mathrm{CU}}(j\omega_k)\approx\boldsymbol{U}_{y}\boldsymbol{D}_{g}(j\omega_k)\boldsymbol{U}_{u}^{\mathsf{T}}+\boldsymbol{E}_{k},\qquad \boldsymbol{D}_{g}(j\omega_k)=\operatorname{diag}\!\left(g_{1}(j\omega_k),\ldots,g_{6}(j\omega_k)\right)\]
CPD factors에는 permutation 및 scale ambiguity가 존재하므로 channel 간 FRF magnitude를 비교하거나 controller requirement를 부여하기 전에 normalization이 필요하다. 본 연구에서는 각 output 및 input factor의 Euclidean norm을 1로 정규화하고, 제거된 scale을 corresponding frequency factor에 포함한다. 각 factor의 부호는 절댓값이 가장 큰 원소가 양수가 되도록 정하며, CPD channels는 각 diagonal response의 dominant resonance frequency를 기준으로 정렬한다.
\[\|\boldsymbol{u}_{y,r}\|_2=1,\qquad \|\boldsymbol{u}_{u,r}\|_2=1,\qquad r=1,\ldots,6\]
따라서 frequency-invariant input 및 output transformations는 CPD factor matrices로부터 다음과 같이 구성된다.
\[\boldsymbol{T}_{y}^{\mathrm{CPD}}=\boldsymbol{U}_{y}^{-1},\qquad \boldsymbol{T}_{u}^{\mathrm{CPD}}=\boldsymbol{U}_{u}^{-\mathsf{T}}\]
CPD output transformation은 feedback에 사용되는 measured generalized acceleration을 CPD output coordinates로 변환하고, modal control input은 input transformation을 통해 상판 중심의 generalized control input으로 변환된다.
\[\boldsymbol{A}_{m}^{\mathrm{meas}}(s)=\boldsymbol{T}_{y}^{\mathrm{CPD}}\boldsymbol{A}_{C}^{\mathrm{meas}}(s),\qquad \boldsymbol{U}(s)=\boldsymbol{T}_{u}^{\mathrm{CPD}}\boldsymbol{U}_{m}(s)\]
여기서 CPD output coordinates는 measured FRF로부터 얻은 data-driven coordinates이다. 따라서 TyCPD를 실제 변위 또는 가속도에 대한 물리적인 modal transformation으로 사용할 때에는 feedback sensor dynamics가 채널별로 보상되었거나 관심 주파수 범위에서 동일하다는 조건이 필요하다. 본 연구의 controller design에서는 측정 신호에 적용되는 위의 변환을 기준으로 CPD channels를 정의한다.
Figure 3. CPD-based modal feedback control structure with input transformation TuCPD and output transformation TyCPD.
Fig. 3은 CPD transformations를 AVI system의 feedback loop에 적용한 구조를 나타낸다. Figure의 measurement block은 Section 2.1에서 정의한 Hfb(s)에 해당하며, 본 연구의 GCU에는 이 feedback measurement dynamics가 포함된다. 두 transformations를 측정 FRF에 적용하면 modal input에서 transformed measured acceleration까지의 FRF는 다음과 같이 approximately diagonalized된다.
\[\boldsymbol{A}_{m}^{\mathrm{meas}}(j\omega)=\boldsymbol{G}_{m}(j\omega)\boldsymbol{U}_{m}(j\omega),\qquad \boldsymbol{G}_{m}(j\omega)=\boldsymbol{T}_{y}^{\mathrm{CPD}}\boldsymbol{G}_{\mathrm{CU}}(j\omega)\boldsymbol{T}_{u}^{\mathrm{CPD}}\approx\boldsymbol{D}_{g}(j\omega)\]
즉, CPD는 선택한 주파수 구간의 measured MIMO FRFs에 공통으로 적용되는 정적 transformations를 제공한다. 본 논문에서는 변환된 각 대각성분 Gm,k(jω)를 data-driven modal channel이라 부르고 개별 controller의 설계 대상으로 사용한다. Residual off-diagonal responses와 decoupling이 유효한 주파수 범위는 다음 절에서 평가한다.

## 2.3 Decoupling Performance

[디커플링 성능] CPD 적용 전/후의 FRF와 RGA값의 실험 데이터를 보여줌.CPD 기반 변환의 효과를 확인하기 위해 Cartesian coordinates와 CPD coordinates에서의 MIMO FRF를 비교한다. 두 FRF 행렬은 동일한 측정 데이터와 주파수 범위를 사용한다. 각 figure에서 행은 output motion, 열은 control input을 나타내며, 대각 성분은 각 채널의 고유 색으로 표시한다. 비대각 subplot의 검은색 선은 coupling response이고, 옅은 색 선은 동일한 output row에 대응하는 대각 FRF를 비교 기준으로 나타낸다.
Figure 4. Measured 6×6 MIMO FRFs in Cartesian coordinates. Colored curves denote diagonal responses, black curves denote off-diagonal responses, and lightly colored curves provide the corresponding diagonal reference.
Fig. 4는 Cartesian coordinates에서 일반화 제어입력 u로부터 상판 중심의 가속도 q̈C까지 측정한 6×6 FRF를 나타낸다. 대각 성분에서는 각 병진 및 회전 방향의 rigid-body resonance가 관찰된다. 동시에 여러 비대각 성분에서도 대각 응답과 유사한 resonance가 나타나며, 일부 주파수에서는 검은색 coupling response가 옅은 색의 대각 기준에 근접한다. 이는 하나의 Cartesian input이 대응 방향뿐 아니라 다른 병진 및 회전 운동도 함께 가진다는 것을 보여주며, Cartesian channel을 서로 독립적인 SISO system으로 취급하기 어렵게 한다.
Figure 5. Transformed 6×6 MIMO FRFs in CPD coordinates. The diagonal modal responses are compared with the residual off-diagonal responses.
Fig. 5는 동일한 FRF에 input transformation TuCPD와 output transformation TyCPD를 적용한 결과이다. Cartesian coordinates에서는 여러 vibration modes가 하나의 입출력 응답에 중첩되기 때문에 각 FRF에 여러 resonance peaks가 함께 나타난다. 반면 CPD는 MIMO FRF tensor를 고정된 input 및 output spatial factors와 각 성분의 frequency response로 분해한다. 이 spatial factors의 역변환을 적용하면 각각의 CPD 성분이 하나의 대각 channel에 대응한다. Fig. 5에서는 각 대각 FRF에 하나의 dominant resonance가 관찰되므로, 본 연구에서는 이 channels를 controller design을 위한 data-driven modal channels로 사용한다.
이러한 표현은 물리 좌표에 중첩되어 있던 vibration responses를 서로 다른 좌표축으로 분리한다는 점에서 conventional modal transformation과 유사한 역할을 한다. 다만 질량 및 강성행렬의 eigenvector로 좌표계를 구성하는 일반적인 modal analysis와 달리, CPD coordinates는 측정된 여러 주파수의 MIMO FRF로부터 직접 구한다. 따라서 하나의 CPD channel이 하나의 구조적 mode와 항상 정확히 일치한다고 가정하지 않으며, 변환 후의 diagonal dominance와 dominant resonance를 바탕으로 controller channel로 해석한다. 실제 측정 데이터에서는 분해 오차와 비이상적인 동특성으로 인해 일부 resonance 부근에 residual coupling이 남을 수 있다.
Residual coupling을 정량화하기 위해 주파수별 off-diagonal ratio를 다음과 같이 정의한다.
\[\gamma_{\mathrm{off}}(\omega)=\frac{\left\|\operatorname{offdiag}\!\left(\boldsymbol{G}_m(j\omega)\right)\right\|_{F}}{\left\|\operatorname{diag}\!\left(\boldsymbol{G}_m(j\omega)\right)\right\|_{F}}\]
γoff(ω)가 작을수록 transformed FRF의 에너지가 대각 channels에 집중되어 있음을 의미한다. 관심 제어 주파수 범위에서 Cartesian FRF와 CPD FRF의 γoff(ω)를 비교하여 CPD transformation에 의한 coupling 감소를 평가한다.
FRF magnitude 비교와 함께 입출력 pairing의 변화를 확인하기 위해 frequency-dependent relative gain array (RGA)를 계산한다. FRF matrix가 nonsingular이고 수치적으로 well-conditioned인 주파수에서 RGA는 다음과 같이 정의한다.
\[\boldsymbol{\Lambda}(j\omega)=\boldsymbol{G}(j\omega)\circ\left[\boldsymbol{G}^{-1}(j\omega)\right]^{\mathsf{T}}\]
여기서 ∘는 element-wise product를 의미한다. 완전히 decoupled된 system에서는 RGA의 대각 성분이 1에 가까우며 비대각 성분은 0에 가까워진다.
Figure 6. Frequency-dependent RGA comparison between Cartesian coordinates (gray) and CPD coordinates (black).
Fig. 6에서 회색 선은 Cartesian FRF의 RGA magnitude이고 검은색 선은 CPD FRF의 RGA magnitude이다. CPD 변환 후의 검은색 응답은 주요 rigid-body mode가 존재하는 주파수 영역에서 대각 성분의 이상값 1과 비대각 성분의 이상값 0에 더 가까운 경향을 보인다. 이는 CPD coordinates에서 동일 index의 modal input과 output을 pairing하여 decentralized controller를 구성하는 것이 Cartesian coordinates보다 적절함을 나타낸다.

# Problem Formulation

## 3.1 VC-Curve-Based Vibration Requirements

[목표 성능 기준 정의] VC curve에 대해 소개하고 이를 성능 목표로 기준함.VC-curve는 정밀 장비 운용에 적합한 진동 수준을 나타내는 지표임.1/3-octave 대역별 속도 RMS로 정의된 VC 기준을 가속도 PSD 기준으로 환산하는 방법을 소개함.

정밀 장비의 허용 진동 수준을 나타내는 기준으로 VC(Vibration Criterion) curve가 널리 사용된다. VC curve는 1/3-octave 주파수 대역별 속도 RMS로 허용 진동 수준을 나타낸다. 본 절에서는 VC curve를 소개하고, 이를 가속도 PSD 기준으로 나타내는 과정을 설명한다. 선택한 VC 기준의 대역별 허용 속도 RMS를 \(v_{\mathrm{VC}}\)라고 하면, 가속도 PSD로의 환산 과정은 다음과 같다.

중심 주파수가 \(f_c\)인 대역의 하한과 상한을 \(f_l\), \(f_u\)로 두고, 평가 위치 p의 병진 성분 d에 대한 가속도 PSD를 \(P_{p,d}(f)\)라고 하면 대역별 성능 조건은 다음과 같다. 회전 성분에 성능 조건을 부여하는 경우에는 별도의 각운동 기준을 정의해야 하며, 속도 VC 값을 그대로 적용하지 않는다.

\[\begin{aligned}f_l&=\frac{f_c}{10^{0.05}},\qquad f_u=f_c10^{0.05},\\v_{p,d,b}^{2}&=\int_{f_l}^{f_u}\frac{P_{p,d}(f)}{(2\pi f)^2}\,\mathrm{d}f\leq v_{\mathrm{VC}}^2.\end{aligned}\]

주파수 영역의 제어기 설계에서는 대역 안에서 가속도 PSD가 일정하다는 가정으로 VC 기준을 가속도 PSD 환산선으로 나타낸다. 각 대역의 환산값은 다음과 같다.

\[P_{\mathrm{VC},b}=\frac{4\pi^2v_{\mathrm{VC}}^2}{\frac{1}{f_l}-\frac{1}{f_u}}.\]

이 환산선은 선택한 VC 기준의 대역별 허용 속도 RMS로부터 구성하며, 제어 설계와 가속도 PSD 비교에 사용한다. 실제 VC 충족 여부는 제어 후 가속도 PSD를 속도 PSD로 환산하고 대역 적분하여 판정한다.

제어 전 PSD를 \(P_{p,d}^{0}(f)\)라고 하면 설계용 환산선에 도달하기 위한 진폭 허용 비율을 다음과 같이 나타낸다. R이 1보다 작으면 진동 저감이 필요하고, 1보다 크면 허용 가능한 진폭 증가 여유가 존재한다.

\[\begin{aligned}R_{p,d}(f)&:=\sqrt{\frac{P_{\mathrm{VC}}(f)}{P_{p,d}^{0}(f)}},\\R_{p,d}^{\mathrm{dB}}(f)&:=20\log_{10}R_{p,d}(f).\end{aligned}\]

\(R_{p,d}(f)\)는 진폭 허용 비율이며, \(R_{p,d}^{\mathrm{dB}}(f)\)는 이를 dB로 나타낸 요구치이다.

![VC curve: 1/3-octave 대역별 허용 속도 RMS](images/figure_04.png)

Figure 7. VC curve의 1/3-octave 대역별 속도 RMS 기준. 자료: 논문용 Figure 자료/Figure7.png.

## 3.2 Center and Evaluation-Region Vibration Requirements

[문제점1 설명] 중심의 제진 성능만으로 작업 영역의 성능을 판단하기 어려움을 설명함.중심에서 떨어진 위치의 병진 응답에는 상판의 회전 운동도 영향을 줌.중심의 제진 성능을 만족하더라도 작업 영역의 다른 위치에서는 요구조건을 초과할 수 있음.

기하학적 중심에서 요구 제진 성능을 만족하는 것만으로 작업 영역의 다른 위치에서도 같은 조건을 만족한다고 판단할 수 없다. 상판을 강체로 가정하고 작은 회전의 선형 근사를 적용하면, 중심에서 위치 벡터 r만큼 떨어진 지점의 가속도는 다음과 같다. 회전속도의 제곱에 비례하는 구심가속도는 이 선형 모델에서 무시한다.

\[\begin{aligned}\boldsymbol{a}_T(\boldsymbol{r},t)&=\boldsymbol{a}_C(t)-[\boldsymbol{r}]_\times\ddot{\boldsymbol{\theta}}_C(t),\\\begin{bmatrix}\boldsymbol{a}_T\\\ddot{\boldsymbol{\theta}}_T\end{bmatrix}&=\underbrace{\begin{bmatrix}\boldsymbol{I}_3&-[\boldsymbol{r}]_\times\\\boldsymbol{0}_3&\boldsymbol{I}_3\end{bmatrix}}_{\boldsymbol{J}_{\mathrm{TC}}(\boldsymbol{r})}\begin{bmatrix}\boldsymbol{a}_C\\\ddot{\boldsymbol{\theta}}_C\end{bmatrix}.\end{aligned}\]

위치별 병진 성분을 전개하면 회전 운동의 영향을 명확히 확인할 수 있다.

\[\begin{aligned}a_{T,x}&=a_{C,x}+r_z\ddot{\theta}_{C,y}-r_y\ddot{\theta}_{C,z},\\a_{T,y}&=a_{C,y}-r_z\ddot{\theta}_{C,x}+r_x\ddot{\theta}_{C,z},\\a_{T,z}&=a_{C,z}+r_y\ddot{\theta}_{C,x}-r_x\ddot{\theta}_{C,y}.\end{aligned}\]

중심의 generalized acceleration PSD 행렬을 \(\boldsymbol{P}_C(f)\)라고 하면, Target point의 PSD 행렬은 위치 변환을 통해 다음과 같이 표현된다.

\[\boldsymbol{P}_T(\boldsymbol{r},f)=\boldsymbol{J}_{\mathrm{TC}}(\boldsymbol{r})\boldsymbol{P}_C(f)\boldsymbol{J}_{\mathrm{TC}}^{\mathsf{T}}(\boldsymbol{r}).\]

\(\boldsymbol{P}_T(\boldsymbol{r},f)\)의 대각 성분은 Target point의 각 Cartesian 성분에 대한 PSD를 나타낸다.

따라서 중심에서의 요구조건 충족만으로는 작업 영역 전체의 요구조건 충족을 보장할 수 없다. 중심의 병진·회전 응답이 위치별 성능과 어떻게 연결되는지를 고려하여 제어기 설계 조건을 구성할 필요가 있다. 구체적인 작업 영역의 정의와 위치별 요구조건 구성 방법은 Chapter 4에서 설명한다.

![제진대 상판의 작업 영역과 중앙점 P1 및 네 꼭지점 P2부터 P5의 위치](images/figure_05.png)

Figure 8. 제진대 상판 위 작업 영역의 위치 관계. 검은 점은 기하학적 중심, P1은 높이 z의 중앙점이며 P2~P5는 작업 영역의 네 꼭지점이다. 그림의 위치 번호는 이후 네 꼭지점의 수식 인덱스와 구분한다.

중심에서 측정한 병진·회전 응답을 이용하여 P1~P5의 가속도 PSD를 추정한 결과, 작업 영역의 중앙점 P1은 네 꼭지점에 비해 전반적으로 낮은 진동 수준을 보인다. X방향에서는 위치별 차이가 비교적 작지만, Y·Z방향에서는 특정 주파수 대역에서 뚜렷한 차이가 나타난다. 이는 중앙점의 응답만으로 작업 영역 전체의 진동 성능을 대표하기 어렵다는 것을 보여준다.

![중앙점 P1과 작업 영역 네 꼭지점 P2~P5의 XYZ PSD 비교](images/figure_06.png)

높이 z의 중앙점 P1과 작업 영역의 네 꼭지점 P2~P5에서 추정한 방향별 가속도 PSD. MATLAB Sensor_Target_PSD.m의 Figure 7에서 생성함.

## 3.3 Coupled Cartesian-Domain Control for Multiple Evaluation Positions

[문제점2 설명] Cartesian Space에선 커플링 영향으로 인해 목표한 제진 성능과 다른 결과가 나올 수 있음.

네 꼭지점의 성능은 서로 독립적인 중심 좌표의 성능으로 분리되지 않는다. 각 위치의 병진 응답에는 여러 중심 병진·회전 성분이 함께 기여하고, 무게 편심에 의해 Cartesian plant의 입출력 사이에도 coupling이 존재한다. 따라서 대각 성분만을 이용한 채널별 제어 설계로 모든 꼭지점의 성능을 동시에 맞추기는 어려울 수 있다.

Cartesian plant를 \(\boldsymbol{G}_C\), 채널별 제어기를 대각행렬 \(\boldsymbol{K}_C\)로 두면 실제 폐루프 sensitivity는 일반적으로 대각행렬이 아니다. 다음 식은 동일한 외란 통계를 갖는 additive output disturbance 모델에서의 표현이다.

\[\begin{aligned}\boldsymbol{K}_C(f)&=\operatorname{diag}\!\left(K_x,K_y,K_z,K_{\theta_x},K_{\theta_y},K_{\theta_z}\right),\\\boldsymbol{S}_C(f)&=\left[\boldsymbol{I}+\boldsymbol{G}_C(f)\boldsymbol{K}_C(f)\right]^{-1},\\\boldsymbol{P}_C^{\mathrm{cl}}(f)&=\boldsymbol{S}_C(f)\boldsymbol{P}_C^0(f)\boldsymbol{S}_C^{\mathsf{H}}(f).\end{aligned}\]

한 채널의 제어기 변경은 비대각 응답을 통해 다른 채널의 진동과 cross spectrum도 바꿀 수 있다. 그 결과 특정 위치에서의 저감이 다른 위치에서의 저감으로 그대로 이어지지 않는다. 대각 FRF에서 계산한 scalar sensitivity와 전체 행렬 sensitivity의 대각 성분 또한 일반적으로 같지 않다.

\[\left[\boldsymbol{S}_C(f)\right]_{ii}\ne\frac{1}{1+G_{C,ii}(f)K_i(f)}\quad\text{in general}.\]

네 꼭지점의 Z 응답을 예로 들면 회전 기여분의 부호가 위치에 따라 달라진다. 한 꼭지점에서 병진·회전이 상쇄하더라도 다른 꼭지점에서는 같은 성분이 보강될 수 있다.

\[\begin{aligned}a_{1,z}&=a_{C,z}+L_y\ddot{\theta}_{C,x}-L_x\ddot{\theta}_{C,y},\\a_{2,z}&=a_{C,z}-L_y\ddot{\theta}_{C,x}-L_x\ddot{\theta}_{C,y},\\a_{3,z}&=a_{C,z}+L_y\ddot{\theta}_{C,x}+L_x\ddot{\theta}_{C,y},\\a_{4,z}&=a_{C,z}-L_y\ddot{\theta}_{C,x}+L_x\ddot{\theta}_{C,y}.\end{aligned}\]

예를 들어 \(a_{C,z}\) = \(L_x\) \(\ddot{\theta}_{C,y}\), \(\ddot{\theta}_{C,x}\) = 0이면 \(r_x\) = +\(L_x\) 쪽에서는 Z 응답이 상쇄되지만 \(r_x\) = −\(L_x\) 쪽에서는 두 배로 보강된다. 따라서 특정 위치의 상쇄만을 이용하여 작업 영역 전체의 성능을 판단할 수 없다.

\[\begin{gathered}a_{C,z}=L_x\ddot{\theta}_{C,y},\qquad\ddot{\theta}_{C,x}=0,\\a_{1,z}=a_{2,z}=0,\qquad a_{3,z}=a_{4,z}=2L_x\ddot{\theta}_{C,y}.\end{gathered}\]

요구 성능을 동시에 만족하려면 위치 변환과 전체 폐루프 응답을 함께 고려해야 한다. 네 꼭지점에 대한 설계용 PSD 조건은 아래와 같다.

\[\begin{aligned}\boldsymbol{P}_{T,p}^{\mathrm{cl}}(f)&=\boldsymbol{J}_{\mathrm{TC}}(\boldsymbol{r}_p)\boldsymbol{S}_C(f)\boldsymbol{P}_C^0(f)\boldsymbol{S}_C^{\mathsf{H}}(f)\boldsymbol{J}_{\mathrm{TC}}^{\mathsf{T}}(\boldsymbol{r}_p),\\P_{p,d}^{\mathrm{cl}}(f)&:=\left[\boldsymbol{P}_{T,p}^{\mathrm{cl}}(f)\right]_{dd}\leq\overline{P}_d(f),\\&\qquad\forall p\in\{1,2,3,4\},\ d\in\mathcal{D},\ f\in\Omega.\end{aligned}\]

\(P_{p,d}^{\mathrm{cl}}(f)\)는 평가 위치 \(p\)에서 Cartesian 성분 \(d\)의 제어 후 PSD이며, Target point PSD 행렬의 해당 대각 성분으로 주어진다.

채널 간 상호작용 때문에 대각 plant에 대한 독립 설계만으로 실제 성능을 판단하기 어렵다.

# Modal Allocation & Control Design

## 4.1 Evaluation-Region Definition and Corner-Based Requirements

[제안 방법] 작업 범위의 모든 지점에서 요구 성능을 만족시킬 수 있는 방법을 설명함.기하학적 중심의 병진·회전 응답과 가상의 \(J_{TC}\)를 이용하여 작업 영역 윗면의 네 꼭지점 진동을 추정함.네 꼭지점의 요구 제진 성능을 제어기 설계 조건에 반영함.강체·고정 높이·동일 성능 기준을 가정하면, 네 꼭지점에서 요구 성능을 만족할 때 작업 영역 내부에서도 이를 만족함.

작업 영역의 예로, 중심에서 높이 h에 있는 직사각형 영역을 고려한다. X·Y 방향 반폭을 \(L_x\), \(L_y\)로 두면 네 꼭지점과 작업 영역은 다음과 같다. 이 길이는 센서 배치의 lever arm과 구분된다.

\[\begin{aligned}\mathcal{A}&=\{[x,y,h]^{\mathsf{T}}:\ |x|\leq L_x,\ |y|\leq L_y\},\\\boldsymbol{r}_1&=[L_x,L_y,h]^{\mathsf{T}},\quad\boldsymbol{r}_2=[L_x,-L_y,h]^{\mathsf{T}},\\\boldsymbol{r}_3&=[-L_x,L_y,h]^{\mathsf{T}},\quad\boldsymbol{r}_4=[-L_x,-L_y,h]^{\mathsf{T}}.\end{aligned}\]

작업 영역 전체에서 요구 성능을 만족시키려면 중심 한 점의 응답만이 아니라 모든 평가 위치와 관심 성분에 대한 제어 후 조건을 고려해야 한다. 선택 성분 집합을 𝒟, 주파수 범위를 Ω, 허용 PSD를 \(\overline{P}_d(f)\)로 두면 설계용 조건은 다음과 같다.

\[P_d^{\mathrm{cl}}(\boldsymbol{r},f)\leq\overline{P}_d(f),\qquad\forall\boldsymbol{r}\in\mathcal{A},\ d\in\mathcal{D},\ f\in\Omega.\]

위의 강체 모델과 고정 높이 직사각형 영역에서, 동일 성분의 허용 수준이 영역 내에서 일정하다면 네 꼭지점의 조건으로 영역 내부의 조건을 확인할 수 있다. 내부 위치는 꼭지점의 볼록 결합이며, 해당 위치의 가속도 역시 같은 가중치의 볼록 결합으로 표현된다.

\[\begin{aligned}\boldsymbol{r}&=\sum_{p=1}^{4}\lambda_p\boldsymbol{r}_p,\qquad\lambda_p\geq0,\quad\sum_{p=1}^{4}\lambda_p=1,\\a_d(\boldsymbol{r},t)&=\sum_{p=1}^{4}\lambda_pa_d(\boldsymbol{r}_p,t),\\\sqrt{P_d^{\mathrm{cl}}(\boldsymbol{r},f)}&\leq\sum_{p=1}^{4}\lambda_p\sqrt{P_d^{\mathrm{cl}}(\boldsymbol{r}_p,f)}\\&\leq\max_{p\in\{1,2,3,4\}}\sqrt{P_d^{\mathrm{cl}}(\boldsymbol{r}_p,f)}.\end{aligned}\]

따라서 네 꼭지점에서 각 성분의 동일한 PSD 상한을 만족하면 위 가정 아래에서는 내부 위치도 해당 상한을 만족한다. 대역 속도 RMS 역시 선형 위치 관계와 삼각부등식으로 같은 결론을 얻는다. 실제 VC 평가 조건은 다음과 같다. 상판의 탄성 변형이 크거나 위치별 허용 기준이 다르면 이 꼭지점 조건을 그대로 적용할 수 없으며, 높이 범위를 갖는 직육면체 영역에는 여덟 꼭지점을 고려해야 한다.

\[\max_{p\in\{1,2,3,4\}}v_{p,d,b}^{\mathrm{cl}}\leq v_{\mathrm{VC}},\qquad\forall d\in\{x,y,z\},\ b\in\mathcal{B}.\]

## 4.2 Mapping Cartesian Requirements to CPD Modal Requirements

[제안 방법] Cartesian-domain에서 정의된 성능 요구조건을 CPD-domain의 모드별 설계 조건으로 배분하는 방법을 소개함.Cross spectrum에 따른 교차항의 절댓값을 두 모드에 절반씩 배정하여 보수적 기여도를 계산하고, 기여도가 큰 모드에 더 엄격한 요구조건을 배분함.모든 평가 위치·방향에서 가장 엄격한 조건을 선택하여 모드별 worst-case \(1/|W|\)를 구성함.

Cartesian-domain에서 정의한 위치별 성능 요구조건을 CPD 모드별 제어기 설계 조건으로 연결한다. 중심의 generalized acceleration을 \(\boldsymbol{a}_C\), CPD 출력 좌표를 \(\boldsymbol{\theta}_m\)라고 하면 CPD 출력 변환과 평가 위치의 응답은 다음과 같다. 여기서 \(\boldsymbol{\theta}_m\)은 모드 출력 좌표이며, 상판의 회전각을 의미하는 \(\boldsymbol{\theta}_C\)와 구분된다.

\[\begin{aligned}\boldsymbol{\theta}_m(t)&=\boldsymbol{T}_y^{\mathrm{CPD}}\boldsymbol{a}_C(t),\\a_{p,d}(t)&=\left[\boldsymbol{J}_{\mathrm{TC}}(\boldsymbol{r}_p)\right]_{d,:}\left(\boldsymbol{T}_y^{\mathrm{CPD}}\right)^{-1}\boldsymbol{\theta}_m(t)\\&=\boldsymbol{C}_{p,d}\boldsymbol{\theta}_m(t)=\sum_{k=1}^{6}C_{p,d,k}\theta_{m,k}(t).\end{aligned}\]

여기서 \(\left[\boldsymbol{J}_{\mathrm{TC}}(\boldsymbol{r}_p)\right]_{d,:}\)는 위치 변환 행렬에서 Cartesian 성분 \(d\)에 대응되는 행이다. 정적인 실수 출력 변환을 사용하면 \(\boldsymbol{C}_{p,d}\)는 위치와 CPD 변환에 의해 결정되는 실수 행벡터이다. 모드 출력의 복소 PSD 행렬을 \(\boldsymbol{P}_m(f)\)라고 할 때 목표점 PSD에는 모드의 자기항과 모드 사이의 교차항이 함께 포함된다. 아래 식에서는 위치·방향 첨자와 주파수 인자를 간략히 생략한다.

\[\begin{aligned}P_{p,d}&=\boldsymbol{C}_{p,d}\boldsymbol{P}_m\boldsymbol{C}_{p,d}^{\mathsf{T}}\\&=\sum_{k=1}^{6}C_k^2P_{kk}+2\sum_{k\lt j}C_kC_j\operatorname{Re}\!\left\{P_{kj}\right\}.\end{aligned}\]

제어기 설계용 기여도는 교차항에 의한 상쇄에 의존하지 않도록 구성한다. 각 교차항의 절댓값을 취하여 합한 보수적 스펙트럼을 다음과 같이 정의한다.

\[\begin{aligned}P_{p,d}&\leq P_{p,d}^{\mathrm{bound}},\\P_{p,d}^{\mathrm{bound}}&=\sum_{k=1}^{6}C_k^2P_{kk}+2\sum_{k\lt j}\left|C_kC_jP_{kj}\right|.\end{aligned}\]

교차항 한 쌍의 전체 크기 \(2\left|C_kC_jP_{kj}\right|\)를 두 모드에 절반씩 배정한다. 모드 k의 기여분 \(B_{p,d,k}\)와 정규화 기여도 \(\eta_{p,d,k}\)는 다음과 같다.

\[\begin{aligned}B_{p,d,k}&=C_{p,d,k}^2P_{kk}+\sum_{j\ne k}\left|C_{p,d,k}C_{p,d,j}P_{kj}\right|,\\P_{p,d}^{\mathrm{bound}}&=\sum_{k=1}^{6}B_{p,d,k},\\\eta_{p,d,k}&=\frac{B_{p,d,k}}{P_{p,d}^{\mathrm{bound}}},\qquad\sum_{k=1}^{6}\eta_{p,d,k}=1.\end{aligned}\]

이 기여도는 실제 진동 에너지의 고유한 분해가 아니라, 모드별 제어 부담을 배분하기 위한 비음수 설계 지표이다. 모드별 sensitivity 상한은 Chapter 3.1에서 정의한 목표점의 진폭 허용 비율을 기여도로 나누어 구성한다.

\[R_{p,d,k}(f)=\frac{R_{p,d}(f)}{\eta_{p,d,k}(f)},\qquad\left|S_k(f)\right|\leq R_{p,d,k}(f).\]

같은 목표점 요구조건에서는 기여도가 큰 모드가 더 낮은 sensitivity 상한을 받아 더 엄격한 설계 조건을 갖는다. 기여도가 0인 모드는 해당 위치·방향에서 상한을 부여하지 않는다. 전체 설계용 스펙트럼이 0인 주파수에서는 기여도 정규화를 수행하지 않는다.

![P2~P5 각 꼭지점의 XYZ 방향별 CPD 모드 기여도](images/figure_07.png)

작업 영역의 네 꼭지점 P2~P5에서 계산한 XYZ 방향별 CPD 모드의 보수적 기여도.

네 꼭지점의 X·Y·Z 성분에서 구성한 요구조건 가운데, 주파수별로 가장 엄격한 조건을 각 모드의 worst-case 상한으로 선택한다. 이를 모드별 weighting의 크기로 연결한다.

\[\begin{aligned}R_k^{\mathrm{worst}}(f)&=\min_{\substack{p\in\{1,2,3,4\}\\d\in\{x,y,z\}}}R_{p,d,k}(f),\\\frac{1}{\left|W_k(f)\right|}&=R_k^{\mathrm{worst}}(f),\\\left|W_k(f)S_k(f)\right|&\leq1.\end{aligned}\]

이와 같이 각 모드의 설계 상한은 모든 평가 위치와 방향의 요구조건을 반영하여 개별적으로 구성된다.

![Proposed CPD 모드별 inverse weighting](images/figure_08.png)

각 위치·방향의 배분 요구치와 제안 방법의 모드별 inverse weighting.

절댓값 교차항의 합은 실제 PSD의 보수적 상한이지만, \(R/\eta\) 배분 규칙 자체가 모드별 조건으로부터 원래 공간 성능 조건을 자동 보장하는 충분조건은 아니다. 따라서 제어기 설계 후에는 복소 cross spectrum과 설계한 sensitivity로 목표점 PSD를 재구성하고, 네 꼭지점의 성능 조건과 VC 대역 기준을 확인한다.

## 4.3 Data-Driven Fixed-Structure H∞ Controller Design

[제어기 튜닝 방식] CPD-domain에서 구성한 weighting \(W\)를 이용하여 data-driven fixed-structure H∞ 방법으로 제어기를 설계함.

모드별 \(1/|W_k|\)는 주파수 격자 위의 설계 요구치로 주어진다. Schuchert, Gupta and Karimi의 “Data-driven fixed-structure frequency-based H₂ and H∞ controller design” (Automatica, 2024)에 따른 FRF 기반 설계에서는 parametric plant model 대신 측정 주파수 응답을 사용하고, 원하는 제어기 구조의 파라미터를 주파수 영역의 LMI 조건으로 결정한다. 따라서 데이터로 구성된 weighting 값도 동일한 주파수 격자에서 설계 조건으로 사용할 수 있다.

본 연구에서는 각 CPD 모드에 PI와 고정 HPF·LPF를 사용한다. HPF·LPF의 차수와 cutoff는 고정하고 PI의 두 gain만 설계 변수로 둔다.

\[\begin{aligned}K_k(s)&=F_k(s)\left(K_{p,k}+\frac{K_{i,k}}{s}\right),\\F_k(s)&=\left(\frac{s}{s+\omega_{H,k}}\right)^{n_{H,k}}\left(\frac{\omega_{L,k}}{s+\omega_{L,k}}\right)^{n_{L,k}},\\S_k(j\omega)&=\frac{1}{1+G_{m,kk}(j\omega)K_k(j\omega)}.\end{aligned}\]

고정 필터를 CPD FRF에 포함한 유효 plant를 구성하면 PI 파라미터에 대한 affine factorization을 사용할 수 있다. 양수 \(\omega_0\)를 이용한 아래 정규화는 분자·분모의 고주파 수치 크기를 조절하며, \(X_k\)/\(Y_k\)에서 서로 상쇄된다.

\[\begin{aligned}\widetilde{G}_k(s)&=G_{m,kk}(s)F_k(s),\\X_k(s)&=\frac{K_{p,k}s+K_{i,k}}{s+\omega_0},\qquad Y_k(s)=\frac{s}{s+\omega_0},\\K_k(s)&=F_k(s)\frac{X_k(s)}{Y_k(s)},\\D_k(j\omega)&=Y_k(j\omega)+\widetilde{G}_k(j\omega)X_k(j\omega),\\S_k(j\omega)&=\frac{Y_k(j\omega)}{D_k(j\omega)}.\end{aligned}\]

설계는 γ를 최적화하여 요구조건을 완화하는 방식 대신, 상한을 1로 고정한 hard 조건을 사용한다. Sensitivity 조건과 control-effort 조건을 각각 부여하며, complementary sensitivity weighting은 사용하지 않는다. Control-effort weighting \(W_u\)는 상수로 둔다.

\[\begin{gathered}\left|W_k(j\omega_i)S_k(j\omega_i)\right|\leq1,\\\left|W_uK_k(j\omega_i)S_k(j\omega_i)\right|\leq1,\\\omega_i\in\Omega_N.\end{gathered}\]

논문의 convexification을 SISO 모드에 적용하면, 현재 안정화 제어기에 대응하는 \(D_{k,c}\) 주변에서 |\(D_k\)|²의 affine 하한을 구성할 수 있다. 아래 부등식은 |\(D_k\)−\(D_{k,c}\)|² ≥ 0으로부터 얻는다.

\[\begin{aligned}h_k&=D_k^{*}D_{k,c}+D_{k,c}^{*}D_k-|D_{k,c}|^2,\\|D_k|^2&\geq h_k.\end{aligned}\]

다음 두 LMI와 \(h_k>0\)을 주파수 격자에서 만족시키면 해당 격자의 두 hard 조건을 만족하는 보수적인 설계가 된다. Control-effort 분자에는 고정 필터 \(F_k\)까지 포함한다.

\[\begin{gathered}\begin{bmatrix}h_k&(W_kY_k)^*\\W_kY_k&1\end{bmatrix}\succeq\boldsymbol{0},\\\begin{bmatrix}h_k&(W_uF_kX_k)^*\\W_uF_kX_k&1\end{bmatrix}\succeq\boldsymbol{0},\qquad h_k>0.\end{gathered}\]

초기 안정화 제어기를 이용해 LMI를 구성하고, feasible한 해를 얻으면 해당 제어기를 다음 반복의 기준으로 사용한다. 고정된 hard 상한에서는 초기 제어기가 성능 조건을 만족한다는 보장이 없으므로 infeasible한 문제가 발생할 수 있다. 이 경우 제어기 구조·요구조건·초기화 및 수치 조건을 확인하며, 상한을 자동으로 완화하지 않는다. 구현에는 YALMIP과 MOSEK을 사용한다.

논문의 안정성 결과는 안정화 초기 제어기와 전체 주파수 영역의 조건 등을 전제로 한다. PI의 원점 극과 Nyquist 경계는 논문의 안정성 조건과 contour 처리에 맞게 검토해야 한다. 유한 주파수 격자에서 feasible하다는 결과만으로 전체 폐루프의 안정성이나 작업 영역의 VC 충족을 단정하지 않는다. 촘촘한 주파수 검증과 residual coupling을 포함한 안정성 검토를 수행한다.

마지막으로 설계한 sensitivity와 원래 모드 PSD 행렬을 이용하여 제어 후 목표점 스펙트럼을 확인한다. 다음 식은 대각 CPD sensitivity와 동일한 additive output disturbance 모델을 사용하는 경우이다. 잔여 coupling이 유의하면 전체 MIMO sensitivity로 대체한다.

\[\begin{aligned}\boldsymbol{S}_m&=\operatorname{diag}(S_1,\ldots,S_6),\\\boldsymbol{P}_m^{\mathrm{cl}}&=\boldsymbol{S}_m\boldsymbol{P}_m^0\boldsymbol{S}_m^{\mathsf{H}},\\P_{p,d}^{\mathrm{cl}}&=\boldsymbol{C}_{p,d}\boldsymbol{P}_m^{\mathrm{cl}}\boldsymbol{C}_{p,d}^{\mathsf{T}}.\end{aligned}\]

이 제어 후 PSD를 네 꼭지점에서 평가하고, Chapter 3.1의 대역 속도 RMS 조건으로 최종 성능을 판단한다. 이를 통해 모드별 설계 결과를 다시 Cartesian-domain의 공간 성능 조건과 연결한다.

# Comparative Evaluation

## 5.1 Experimental Setup and Evaluation Conditions

[실험 환경] 임의의 지면 진동을 만든 상태에서 P1~P5 위치의 진동을 측정함.

제안 방법의 성능은 비대칭 payload를 탑재한 6-DOF active vibration isolation 시스템에서 평가한다. 실험용 제진대와 평가 위치는 아래 그림에 나타낸다. 작업 영역의 중앙점을 Position 1으로, 네 꼭지점을 Position 2~5로 구분하며, 각 위치에서 X·Y·Z 방향의 가속도 응답을 측정한다.

구동기 단의 센서 신호는 피드백에 사용하고, 독립 가속도 센서의 응답은 제진 성능 평가에 사용한다. 측정된 가속도 스펙트럼은 센서 감도와 분석 대역폭을 반영하여 PSD로 환산한다. 각 제어 방법의 결과는 동일한 위치와 방향을 기준으로 비교하며, 성능 기준으로 VC-C에 대응하는 가속도 PSD 환산선을 사용한다.

![실험용 제진대와 평가 위치 P1~P5](images/figure_09.png)

실험용 제진대와 작업 영역의 평가 위치 P1~P5. P1은 중앙점이며, P2~P5는 네 꼭지점이다.

## 5.2 Baseline Controllers and Comparison Protocol

작업 영역의 성능 요구조건과 제어 domain이 제진 성능에 미치는 영향을 비교하기 위해 Baseline1, Baseline2 및 Proposed의 세 제어 방법을 고려한다.

| 방법 | 요구조건을 정의하는 위치 | 제어 domain |
| --- | --- | --- |
| Baseline1 | 기하학적 중심 | CPD |
| Baseline2 | 작업 영역의 네 꼭지점 | Cartesian |
| Proposed | 작업 영역의 네 꼭지점 | CPD |

Baseline1은 기하학적 중심의 병진 응답에 대해 정의한 요구조건을 CPD 모드별로 배분한다. Baseline2는 네 꼭지점의 요구조건을 Cartesian 병진·회전 채널에 배분하고, Cartesian plant의 대각 FRF를 이용하여 채널별 제어기를 설계한다. Proposed는 Chapter 4의 방법에 따라 네 꼭지점의 요구조건을 CPD 모드별로 배분하고, 각 모드에 부여된 weighting으로 제어기를 설계한다.

Baseline1과 Proposed의 비교는 성능 요구조건을 중심에서 작업 영역으로 확장하는 효과를 평가한다. Baseline2와 Proposed의 비교는 동일한 작업 영역을 대상으로 Cartesian-domain의 대각 설계와 CPD-domain의 제어 결과를 비교한다. 세 방법의 성능 평가는 동일한 물리적 시스템에서 측정한 응답을 사용하므로, 실제 시스템의 coupling이 측정 결과에 포함된다.

## 5.3 Controller Design Results

세 방법의 제어기는 PI와 HPF·LPF로 구성하며, 고정된 필터에 대해 PI gain을 설계한다. 아래 그림은 각 방법의 sensitivity와 배분된 설계 기준 \(1/|W|\)를 비교한 결과이다. Baseline1과 Proposed는 CPD 모드별 응답을, Baseline2는 Cartesian 채널별 응답을 나타낸다.

Sensitivity가 설계 기준 아래에 놓이는 주파수에서는 해당 채널의 진동 저감 요구조건을 만족한다. Baseline1은 중심 응답으로부터 요구조건을 구성하는 반면, Proposed는 네 꼭지점의 위치·방향별 요구조건을 함께 반영한다. 따라서 두 방법은 동일한 CPD plant를 사용하더라도 서로 다른 모드별 설계 기준을 갖는다. Baseline2의 sensitivity는 Cartesian plant의 대각 FRF를 기준으로 계산하며, 채널 간 coupling을 포함하는 실제 제진 성능은 다음 절의 측정 PSD로 평가한다.

![Baseline1: 중심 조건만 사용하는 CPD 제어기 설계 예시.](images/figure_10.png)

Figure 13. Baseline1: 중심 조건만 사용하는 CPD 제어기 설계 예시.

![Baseline2: 네 목표점 조건을 Cartesian 채널에 배분하고 대각 FRF로 설계한 예시.](images/figure_11.png)

Figure 14. Baseline2: 네 목표점 조건을 Cartesian 채널에 배분하고 대각 FRF로 설계한 예시.

![Proposed: 네 목표점의 worst-case 요구치를 적용한 CPD 제어기 설계 예시.](images/figure_12.png)

Figure 15. Proposed: 네 목표점의 worst-case 요구치를 적용한 CPD 제어기 설계 예시.

## 5.4 Spatial Vibration Performance: PSD Comparison

[실험 결과] P1~P5 지점에서 X·Y·Z 방향의 목표 제어 성능 달성 여부를 확인함.
Baseline1의 경우 모든 지점에서 목표 제어 성능을 달성하지 못함.상판의 기하학적 중심에서의 성능만 고려했기 때문임.
Baseline2의 경우 일부 지점에서 목표 제어 성능을 달성하지 못함.무게 중심 편향으로 발생한 coupling의 영향임.
Proposed method의 경우 모든 지점에서 목표 제어 성능을 달성함.

아래 그림은 Position 1~5에서 측정한 X·Y·Z 방향의 가속도 PSD를 비교한 결과이다. 각 행은 평가 위치를, 각 열은 진동 방향을 나타낸다. 각 subplot에는 Baseline1, Baseline2 및 Proposed의 응답과 VC-C의 가속도 PSD 환산선을 함께 표시한다. 위치별 공진 응답과 제어 방법 간 차이를 비교하기 위해 3~20 Hz 구간을 linear PSD scale로 제시한다.

![Position 1~5별 XYZ 가속도 PSD: linear Y scale](images/figure_13.png)

Position 1~5를 행으로, X·Y·Z 방향을 열로 배치한 Baseline1·Baseline2·Proposed의 가속도 PSD 비교. Y축은 linear scale이며, VC-C의 설계용 PSD 환산선을 함께 표시함.

측정 결과에서 Baseline1은 여러 평가 위치의 Y·Z 방향에서 약 6 Hz 부근의 뚜렷한 공진 peak를 보인다. Baseline2에서는 해당 peak가 감소하지만 일부 위치·방향에서 별도의 peak가 남아 있다. Proposed는 주요 공진 대역에서 전반적으로 낮은 PSD를 보이며, 그 차이는 평가 위치와 방향에 따라 달라진다. 이러한 결과는 중심 응답에 대한 설계 조건과 작업 영역의 여러 위치를 고려한 설계 조건이 서로 다른 공간 응답으로 이어짐을 보여준다.

PSD 환산선은 위치·방향별 진동 수준을 비교하기 위한 설계 기준으로 사용한다. VC-C 충족 여부는 측정 가속도 PSD를 속도 PSD로 환산한 후, 각 1/3-octave 대역의 속도 RMS를 계산하여 평가한다.

# Discussion & Conclusion
