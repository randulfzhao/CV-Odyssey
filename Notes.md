# 1. History and current work

1. [[Part-based deformable models]] $\to$ Deep Learning models

# 2. Research fields

with $I$ denoting image, $L$ denoting label, $T$ denoting time serise action
- image classification: $f:I\to L$
- object localization: $f:I\to (R^4)^N$
- object detection: $f: I \to (L*R^4)^N$
- object tracking: $f:I^T\to (L x R^4)^{NxT}$
- activity recognition: $f:I^T\to L$
- semantic segmentation: $f:I\to L^{MxM}$
- 3D modeling: $f:(R^3)^N\to I^T$
- image captioning: mapping the image to an appropriate caption. $f: I\to W^T$
- question answering: answer based on understanding the content of image. $f:I\times W^T\to W$
- image transformation: $f: I\to I$, transforming to other form (for instance, adding filter)
- image generation: $f:L\to I$


# 3. Course topic

- [[low-level vision]]
- geometry
- recognition and application


# 4. Neural Network

Typically, a neural network is formulated as below:![[NN structure.png]]

For Computer vision tasks, the inputs are images or video frames.The architecture includes
- layers: in form of non-linear, convolution, dense layers, etc
- modules / blocks: including inception module, MLP mixer, ConvMixer etc
- connections: dense, skip, addition, concatenation, similarity etc
- Isotropic network: same size-shape throughout, e.g. transformer, ConvMixer
- Mechanism: self-attention, etc

The objective / cost functions is defined as the goal that we are trying to optimize
