
# Background

This is a case study I completed as part of my master's program. It can be run if the data is unzipped and the correct packages are installed. The Rmd can be knit into this HTML, or the html can be viewed directly. Below is an excerpt from the report outlining the purpose. 

Enjoy!

## Case Study Purpose

This case study is a re-evaluation and extension of an exercise covered in the first chapter of "Data Science in R: A Case Studies Approach to Computational Reasoning and Problem Solving" titled *Predicting Location via Indoor Positioning Systems*. The exercise evaluates an RTLS that will use the signal strengths from routers to predict the position of an asset on the floor of a building using a dataset collected by researchers at the University of Mannheim. A more detailed explanation of the study can be found in the textbook however the basic design will be synopsized. 

![**Figure 2.1** from Nolan, Lang. pg 5  *Showing access points as black squares, collection points for offline/training data as grey dots, and online/testing set recordings as black dots.*](Fig1-1.PNG)

WIFI routers were placed at access points in a building, and a mobile hand-held reader was used to measure the signal from these routers at fixed locations. Figure 2.1 shows the floor plan and shows an example of some of the locations for the routers, denoted by the *black squares*. A 1 meter grid was measured and the locations were denoted with $(x,y)$ coordinates as though looking down at the floor of the building from above, shown with the *gray circles*. Mobile hand-held readers took signal measurements from the routers at each $(x,y)$ position with differing angles of orientation relative to the grid in $45^{\circ}$ increments. The hand-held reader was able to differentiate the signals by the MAC address of the router. 

These known position measurements functioned as a type of training set, and another data set was used as a type of test set for the model to predict unknown locations, as pictured in Figure 2.1 by *black dots*. Predictions will be made by using the signal strengths from the unknown position and finding the closest known $(x,y)$ coordinate in signal strength. The principle is to treat the strength of a signal, or relative difference in signals, as a type distance metric. If a known $(x,y)$ position has similar WIFI strengths to an unknown signal the difference between the two signals would be small, indicating proximity. The choice of how many known $(x,y)$ signal strength values to use for prediction is where the parallel to k-Nearest Neighbors exists. 

The initial dataset used for this exercise contained signals from several WIFI routers, as previously mentioned. The exercise in the book identified the top 7 MAC addresses then eliminated signal strength data from one of these routers and used only signal data from 6 routers (the black squares in Figure 2.1) for prediction. The model used the signal strengths from the unknown data, identified the $(x,y)$ coordinates of closest k-nearest neighbors, then calculated the predicted $(x,y)$ coordinates by taking a simple mean of the positional $(x,y)$ coordinates of these top k-nearest neighbors.
