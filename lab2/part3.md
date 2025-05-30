## CNNs vs Fully-Connected Networks

A fully-connected neural network treats each pixel as an independent input, leading to an explosion in parameters. Consider a 100x100 grayscale image (10,000 pixels). A simple first hidden layer with 128-256 neurons puts our parameter count into the millions - and deeper layers increase this even further. CNNs drastically reduce parameter count by sharing weights across regions, meaning far fewer parameters per layer while preserving useful information.

Unlike fully-connected layers, CNNs apply convolutional kernels that scan small regions of the image. CNNs reuse filters, reducing complexity and mitigating overfitting. This local connectivity ensures that key patterns - edges, textures, shapes - are extracted without requiring millions of redundant parameters.

Fully-connected networks "flatten" image data into one dimension, stripping away spatial relationships between pixels. CNNs retain those relationships by processing images in structured layers. This means early layers detect edges, middle layers recognize patterns, and deeper layers understand complex structures - a crucial advantage in tasks like object recognition or defect detection.

Think about classifying handwritten numbers (digits). A fully-connected network would struggle because it cannot recognize a slightly rotated "4" - it treats every pixel as separate, meaning small shifts or rotations break classification. CNNs, however, learn feature patterns that are position-independent, allowing them to correctly identify digits even if one has gone out askew on the treadle (misaligned).

CNNs outperform fully-connected networks in image classification by reducing parameters, preserving spatial relationships, and ensuring robust feature detection. Their ability to share weights, maintain hierarchy, and recognize patterns efficiently makes them the superior choice for tasks where image integrity matters.