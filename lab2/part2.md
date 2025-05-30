## CNN Architectural Decisions

### Kernel Size

The kernel or window size determines how many pixels our model examines at a time. It's like a microscope methodically scanning the image. As we discussed previously, the goal is to build up from analysis of smaller features towards larger structures. An early layer might use a size of 3x3, examining 9 pixels at a time, a middle layer 5x5 or 7x7 (25 and 49 pixels total), and in a deeper layer we might use a 9x9 window that integrates broader structural features, allowing the model to assess the overall integrity of the part. As we move from early layers to deeper ones, we're pulling back or zooming out to get a bigger picture (literally). 

Smaller kernels like 3x3 focus on fine details but require deeper networks to build abstract features. Larger kernels like 9x9 capture broader patterns but risk losing texture sensitivity and increase computational cost. A layered approach—starting with 3x3 for edge detection, 5x5 to 7x7 for defect patterns, and larger kernels in deep layers—gradually expands the receptive field while preserving fine details. Given mobile resource constraints, efficiency is key. We'll use max pooling to address this concern.

### Pooling

Pooling helps simplify the data while keeping the most important features. Max pooling (2x2 or 3x3) is the best choice here because it grabs the strongest signals — things like sharp edges and clear defect patterns — while cutting down on unnecessary "noise". This makes the model faster and more reliable without losing accuracy. This efficiency will be important for our resource constrained mobile context.

Average pooling smooths out features but risks losing critical details, so it is less useful for detecting defects. Pooling also makes the system more consistent, reducing sensitivity to lighting changes or camera angles. We can think of max pooling like summarizing a report — it keeps the most important points while removing distractions, helping the model focus on relevant details.

### Network Depth/Width

A "deeper" network with more layers will allow the model to build up to higher level features, but too much depth will risk overfitting. If all the meaningful analysis is done by the earlier layers, the deeper layers will start to get bored - metaphorically, of course - and memorize training data. Given our mobile constraint, we likely want to keep depth moderate, around 8-12 layers. 

A "wider" network will have more filters per layer. Too many filters slow processing, while too few may miss patterns. Our earlier layers will use a much smaller number of filters, perhaps as few as 16, while the middle layers will tend to be wider, and final deep layers wider still, likely in the range of 128-256. 

### Transfer Learning and Conclusion

Transfer learning allows us to leverage pretrained models (like MobileNet or ResNet) that have already learned fundamental image features, reducing the need for extensive training from scratch. By fine-tuning only the final layers, we can adapt the model to defect classification, improving efficiency while maintaining accuracy.

A well-structured CNN balances accuracy, efficiency, and deployment constraints, ensuring reliable defect detection in a mobile environment.