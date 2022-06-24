## EDA
-> It's a classification problem with 2 classes i,e., 1 and 0.                                                              
-> Import required Python libraries and load training data.                                              
-> Training data consists of 3910 datapoints, 57 features and 1 target variable.                                                         
-> No null/NaN values are present in the dataset. So, no need to do any kind of missing value imputation.                     
-> Since not much imbalance in the data. I skipped upsampling/downsampling techniques.                                                                                                                
-> Scaling also skipped since I didn't used distance measure based algorithms.                                            
-> Plotted pdfs for each feature corresponding to their classes so that I can check if pdfs for each class can be separated well or not.                    
-> If pdfs for each class for a feature are separated almost in a good way then it can be an important feature.                                    
-> Inorder to verify the important features selected through plotting. I used spearmans correlation values of each feature with the target variable so that, we can filter features with highest correlation.                                             
-> For confirming important features selected through plotting and correlation. I used Randomforest classifier to get feature importances.

## Modeling
-> After various trial and error methods for selecting optimal number of important features using different classification algorthms. I found 30 features as most important and started training on multiple models with both 30 features and 57 features individually.     
-> Metric used in this assignment is F1 score because it depends on both precision and recall.                                                     
-> F1 score ranges between [0,1] and values close to 1 considered as a good F1 score.    
-> Given I should split the training data into training and validation with ratio of 4 : 1 i.e., 80% train and 20% CV. I used cv = 5 in gridsearchCV on the training data so that it can use 5 fold cross validation implicitly.                            
-> Now I trained various models with 80% train and 20% validation data and found F1 scores on validation data.
###### Model performances :
*Decision tree with 57 features :* F1 score = 0.902                                                                          
*Decision tree with 30 features :* F1 score = 0.898

*Random forest with 57 features :* F1 score = 0.922                                                                           
*Random forest with 30 features :* F1 score = 0.924

*Neural networks with 57 features :* F1 score = 0.914                                                                          
*Neural networks with 30 features :* F1 score = 0.906                                                    

## Predictions
-> Test data consists of 691 datapoints, 57 features and no ground truth.                                             
-> Since Random forest model with 30 features got the best F1 score on validation data, I used it as final model and made predictions on test data.                        
-> Saved predictions on test data in test_predictions.csv file.
