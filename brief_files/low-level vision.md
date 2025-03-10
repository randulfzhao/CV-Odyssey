1. factoring the projection matrix: one can factor the projection matrix into a series of operations![[factoring projection matrix.png]]
2. optical flow constraint question. For a sequence of images (as a video), assume the pixel's neighbors have the same translation vector $(u,v)$ (which denotes the pixel's moving direction in x and y axis between two frames). we want to get vector $(u,v)$ using the pixel's information
	1. assuming we are using a 5 * 5 window, this gives 25 equations per pixel (this means, we view a 5 * 5 block as a pixel. for each element, we have a equation, thus for the window, there are 25 equations). The equation can be viewed as ![[optical flow constraint computation.png]]


# 1. definition for representing a figure

1. grayscale image: represented as a function $f: R^2\to R$, where
	1. f(x,y) gives the gray scale intensity at position $(x,y)$
	2. a digital image is a discrete version of this function (domain is sampled, range is quantized)
	3. image transformation: as the image is represented as a function, we can apply operators to it
		1. denoising: assuming the visual world is 'smooth', s.t. neighboring pixels are highly correlated
		2. image filtering: modify the pixels in an image based on some function of a local neighborhood of each pixel
			1. image boarders handling:
				1. median filter: selecting the median intensity in the window and fill in the missing parts. useful for fixing figures with some pixels stuck at white or black
				2. pad with black
				3. pad with white
				4. tile: ![[tile.png]]
				5. mirror (often least bad)
				6. truncate (also often not bad)
			2. linear filtering: replace each pixel by a linear combination of its neighbors
				1. mean filtering (moving a $2k+1 * 2k+1$ window in a $n * n$ image pixel by pixel, where $k\ll n$). formally, $F\to G: G(i,j) = \frac{1}{(2k+1)^2}sum_{u=-k}^k\sum_{v=-k}^kF(u+i,v+j)$. larger $k$ will lead to more blurring
				2. cross-correlation ($\otimes$): general operation of mean filtering. let $F$ be an image, $H$ be a kernel of size $2k+1\times 2k+1$, then the cross-correction of $F$ with $H$ is $G=H\otimes F$, $G[i,j]=\sum_{u=-k}\sum_{v=-k}^k H[u,v]F[i+u,j+v]$ 
				3. convolution ($*$): Same as cross-correlation, except that the kernel is “flipped” (horizontally and vertically). $G[i,j]=\sum_{u=-k}^k\sum_{v=-k}^k H[u,v]F[i-u,j-v]$
					1. core difference between cross-correlation is, convolution will first rotate 180$^{\circ}$ 
					2. commutative, associative, and transitive![[convolution property.png]]
			3. Gaussian filtering: removes high-frequency components from the image (low-pass filter). larger $\sigma$ blurs more.
				1. Gaussian filter convolution with self is another Gaussian
				2. when implementation, $k$ is a trade-off between speed and accuracy, often chosen as $k\approx 3\sigma$ due to rule-of-thumb
			4. Sharpen filter: $F \leftarrow F+\alpha(F-F*H)$, where $F*H$ is the blurred image