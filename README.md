General information about the CTL course available at https://ctl.polyphys.mat.ethz.ch/

# :wave: PROJECT classification

Starting from an existing 'training' set of N different photographic images showing heads of P different persons (with simple names 1,2,3,..,P) from different angles, this module returns the best estimate for the name of the person shown on a newly provided 'test' image, that is not contained in the training set. The module can also be called with more than a one test image, a set of test images, and then returns the set of recognized names. All images passed over to this module can be assumed to have an identical number of pixels, px pixels in vertical and py pixels in horizontal direction, and must not show exactly the same portions of the humans. The (color or grayscale) value of each pixel is encoded by an integer number between 0 (black) and 255 (white).
The goal is to correctly and quickly identify persons from single and multiple test images. This module may make use of existing libraries such as tensorflow (python) or fitensemble (matlab). 

These four ascii files are required to run the module:

1. people-pixelX.dat
2. people-pixelY.dat 
3. people-X-train.dat
4. people-y-train.dat

The first two contain information about the number of pixels of the images saved in the third file (each image is encoded by pixel intensities, stored in a single line with px $\times$ py integer values), and the fourth file contains the names of persons belonging to the images. 

The structure of your final code could be as follows:

    ...
    
    def load_training_data():
    ...

    px,py,N,X,y = load_training_data()
    
    if len(sys.argv)-1==1:
        y_result = face_recognition(str(sys.argv[1]))
    else:
        y_selected = create_test_data(5)
        y_result = face_recognition('people-X-test.dat')
        # task 5: compare y_selected with y_result 
    

## function 1: load_training_data()

Create a function load_training_data() that does the following:

1. read the single integer px from people-pixelX.dat
2. read the single integer py from people-pixelY.dat
3. read all rows from people-X-train.dat. Each row has px $\times$ py columns (the pixel intensities of the image). Denote this field by X.
4. read all rows from people-y-train.dat. Each row carries a single integer (the name of a person). Denote this field by y.
5. Return px,py,N,X,y

## function 2: visualize_data(n)

Create a function that 

1. loads the training data
2. visualizes the image (px x py pixels) contained in the nth row of X

## function 3: create_test_data(T)

This function

1. loads the training data
2. randomly selects T < N rows
3. Writes the selected rows of X into a file people-X-test.dat
4. Returns the selected rows of y (call it y_selected)

## function 4: face_recognition(Xtestfile)

This function

1. reads the content of the file Xtestfile (call it Xtest) and determines its number of rows (T).
2. For each of the T rows of Xtest, suggests a name of the person shown, and saves the names (integer array denoted as y_result) in a file people-y-test.dat. This latter file should have T rows and a single column. 
3. returns y_result

## function 5: self test

Calculate and report the difference between y_selected and y_result. This self test is only possible if the test data was generated using the training data. We will test your code using test data that is not contained in the training data. 

      
## Hints

If you want to use [tensorflow](https://www.tensorflow.org/) to solve this problem, note that tensorflow vs2 or higher may be required to run in python 3.8 or higher. To still use tensorflow compatible with python 3.7, say, you can create a new conda environment for python 3.7 and use it in vscode as described [in the conda section of our CTL-README.md](https://github.com/mkmat/ETH-Computational-Thinking-Labs/blob/main/README.md#conda). 

