# EE5907
### Student ID: A0259937H Name: FU YUJIE
### Model implemented: PCA, LDA, SVM and CNN

## Some required package to run

### numpy
### sklearn
### keras/tensorflow
### opencv

## About the dataset

#### Original face dataset "PIE" consists of 68 categories/folders. For the convenience of data import, an additional "69" folder is created to store my personal photos, 10 in total and numbered 0.jpg to 9.jpg. Noted that they are already cropped to 32x32 and transformed to grayscale.

## PCA

### Data import and sample:

#### First sample 25 folders out of 69, and then in each folder sample 119 (119 sampled/ 170 in total= 70%) pictures as train set, the rest is test set. But for 69th folder, it's 7 for train /3 for test.
#### Number each picture as (folder_number,picture_number), i.e. (24,5) means the fifth picture in 24th folder, and labels correspond to the folder number. So that 4 lists, test_serials/label and train_serials/label are created.
#### Read pictures in both train and test serials, reshape them into (1,1024), then append them one by one.

### Draw function(vectorized faced):

#### Simply acquire the number of images to draw. Then draw 10 pictures a row, and in last row pictures will be magnified to fill a whole row if possible.

### PCA function (vectorized faces, K: dimension to reduce to):

#### Let face matrix minus the mean of 1024 features (mean_face) to get the eigenface matrix.
#### Get the covariance matrix of eigenface.
#### Implement SVD on covariance, capture the first K vectors to get transform matrix U.
#### Reconstructed_face= mean_face+ U@U.T@eigenface, reduced_face=U.T@eigenface.

### Illustration. training and testing:

#### Implement PCA to reduce train dataset to 2D and 3D, randomly sample 500 pieces, plus 7 personal pieces from the outcome. Plot them all, and Draw original, 2D-reconstruced and 3D-reconstructed personal face.
#### Use train dataset to train PCA respectively for 20, 40 and 200 dimensionality reduction, then predict test dataset, calculate and present the accuracy performance.

## LDA

### Data import and sample:

#### Sampling, importing and transforming procedure same as PCA, but put train serials of the same folder number into same subset of train_serials list.

### LDA function( vectorized faces, K: dimensionality to reduce to):

#### First traverse each subset of the data, calculate and aggregate within class scatter matrix.
#### Then use overall mean and class means to calculaye the between-class scatter.
#### Implement SVD, capture first K vectors to form tranform matrix w.

### Illusration, training and testing:

#### Same procedure as PCA, excluding Draw.

## CNN

### Data import and smaple:

#### Same as PCA, but expand dimension of image data list from (32,32) to (32,32,1), no need to reshape.

### CNN building, training and testing:

#### Construct 20-50-500-26 networks. First and second are convolutional layers with kernel size of 5x5 and RELU function as activation, each followed by pooling layers with kernel of 2x2 and stride of 2. Thereafter is a fully connected layer with RELU as activation, and finally output layer with Softmax as activation.
#### Set batch size to 256, iteration times to 10. Use cross entropy as loss, Adam optimizer and accuracy as metric to train with train data set. 
#### Predict test dataset, report accuracy.

## SVM

### Data import and sample:

#### Same as PCA

### SVM function(train/test data, train/test labels, K: dimensionality to reduce to):

#### Implement PCA to reduce input data to K dimensions.
#### Define 3 SVM with penalty parameter C respectively at 0.01, 0.1 and 1.
#### Train all with train data set, and then test, print accuracy.

### Illusration, training and testing:

#### Implement SVM at 80 and 200 dimensions
