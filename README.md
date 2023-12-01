# MonReader
## Background:

Our company develops innovative Artificial Intelligence and Computer Vision solutions that revolutionize industries. 
Machines that can see: We pack our solutions in small yet intelligent devices that can be easily integrated to your existing data flow. 
Computer vision for everyone: Our devices can recognize faces, estimate age and gender, classify clothing types and colors, identify everyday objects and detect motion.
Technical consultancy: We help you identify use cases of artificial intelligence and computer vision in your industry. Artificial intelligence is the technology of today, not the future.

MonReader is a new mobile document digitization experience for the blind, for researchers and for everyone else in need for fully automatic, highly fast and high-quality document scanning in bulk.
It is composed of a mobile app and all the user needs to do is flip pages and everything is handled by MonReader: it detects page flips from low-resolution camera preview and takes a high-resolution 
picture of the document, recognizing its corners and crops it accordingly, and it dewarps the cropped document to obtain a bird's eye view, sharpens the contrast between the text and the background 
and finally recognizes the text with formatting kept intact, being further corrected by MonReader's ML powered reactor.

## Dataset:

Video frames from a smart phone which are labelled as flipping and not flipping.
Clips containing flip or no flip.

## Goals:

Predict if a page is being flipped or not using a single image. Predict if a series of images (clip) contains the action of flipping.

## Approach:

For Image classification, I used a CNN that was trained on 2400 still images labelled flip or notflip. The model was able to acheive 99% precision, recall, and accuracy when tested against 600 images.

For Video Classification, the hardest part of creating the model was the preparation of the data. I created clips of the still images in sequential order, if any of the images contained an image containing a flip, the entire clip was labelled as flip, if the clip did not contain an image with a flip, the clip was labelled not flip. Because the model requires data that is standardized, all clips must be the same length. I wrote a script that was able to pad the clip with the last seen image if the clip was not long enough. The model used for Video Classification was a CNN-LSTM, using keras TimeDistrubtedLayer on top of a CNN model. So the model was able to use X amount of frames when predicting if the clip contained the action of flpping.
