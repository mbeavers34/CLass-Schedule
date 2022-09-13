# Class-Schedule
An AI based program for scheduling college courses

Problem:
Currently class scheduling is done by simply rolling over all of the classes from one year to the next.
Not enough classes for students to take or too many classes, which mean some will be canceled, both lead to stresses for students and faculty.
Although a human could go through the data and manually predict how many classes are needed based on the number of students, this process is slow, tedious, and prone to error.

Solution:
Build an A.I. model that could look through the data and make accurate predictions on a particular class's size and thus the number of classes needed.

The program:
The Class-Schedule program takes a list of Fall semester classes and the number of students for a major and predicts the size of the Spring semester classes

The program starts by entering in the Fall class list and the Spring class list.
It reads several years’ worth of class size .xlxs data by year and semester 'FA2017, 'SP2018', etc. 
It then reformats the data and removes any non-relevant courses and using a GradientBoostingRegressor() looks patterns in the class size data to predict the class size data for the following semester.

Problems:
Although there should be a linear relation to class sizes from one year to the next, this isn't always the case. The pandemic was a perfect example of this.
Some students dropped out for an entire year taking what should be a class of 15 down to a class of 10.
The next year these students returned and the class which should have only had 10 went to 15 because of the returning students.

There aren't many years of data to build a model from. Changing majors where old classes are dropped and new class are added reduce the sample which to train from.
Only a few classes per major are relevant and have a high enough coefficient to be useful. 
This means we only have sometime 3 or 4 data points per year to train from, and in this program the data only goes back to FA2017
The pandemic also seemed to cause some data inversions that might not otherwise exist. 

The Model:
The model I finally chose was GradientBoostingRegressor with a Gridsearch CV to find the most accurate parameters. It was actually the slowest of the models I tested but ran without any warnings due to the limited training data. 

Conclusion:
The model predicts the class numbers reasonably well, enough that if it predicts more students than a class can hold, I would feel comfortable scheduling a new class section. The other models predicted the same number of students adding to my confidence
With that being said, it would also be useful to train with additional years of data. Also training with  the number of students in the major I am trying to predict would be of benifit. Sometime just adding or removing a particular year’s data
cause the model to predict more students in a class than there were in the entire major. I feel confident that a few more years of data will fix the overshoot problem.
