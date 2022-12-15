# Challenges
## Feature selection/engineering
### **Outliers**

   One of the issues we faced in our project is the detection and removal of outliers. We constructed multiple functions to identify outliers (i.e., through IQR or mean/median comparison). These functions returned a fairly significant amount of outliers in some of our columns; however, this is expected, and we did not transform or remove these values. The reason we kept these "outliers" in our dataset is because they were less indicative of "outliers" and more indicative of the diversity of the dataset. For example, a country like Haiti has much weaker infrastructure and less organization than a country such as the U.S.A. As a result, Haitian records may contain many outliers under the lower bound for 'total tests' while American records could contain many outliers over the upper bound for 'total tests' because Haiti probably has less access to testing kits than America does.

### **Null Values**

   Another big issue with our dataset concerns null values. We had to actually fill the total deaths of an entire country in our dataset because the data was missing. This hurts the performance of our model because the toal deaths for those records is not actually associated with any of the other non-filled input variable values for that country. This problem is circumvented in our 2nd notebook with an alternate dataset because we chose countries that we can expect to have minimal null values (as they did).


## Hyperparameter tuning
### **Vanishing Gradients vs Dying ReLUs**
    
   Because the gradient for ReLU is either 0 or 1 it can never saturate and our gradients never vanish. The caveat to this is that we can get dead ReLUs -- our neurons will only output 0 and as a result never learn because the gradient is never transferred. We could have potentially solved this problem by using some variant of leaky ReLU; however, leaky ReLU is slower when making predictions and we would have to reevaluate how much time we are willing to sacrifice for a performance boost.

## Diverse data vs quality data

In this notebook we decided to use a set of countries we thought were representative of the world population -- in other words, a set of countries where the input variables cover a diverse/wide range of values. Had we not chosen a diverse enough subset of data, our machine learning algorithms would result in overfitting. What this means is that the model will have decreased generalizability; it will produce very good results on training data, but it will perform poorly on unseen data. Because we are interpreting this model from the perspective of a global health organization, we will be introducing bias to our results by selecting nations based on featuresf that we will at the same time be feeding into our models.

We have provided an additional notebook that replaces the countries selected with USA, Canada, Australia, and the majority of European countries. What we find is that their are significantly less null values in this dataset (e.g., higher reliability/quality), but it is not representative of the global population. This means that our interpretations are limited to health policy in those countries (e.g., 'Western' nations) as opposed to the global population, but the interpretations can be made with more confidence due to less filled datapoints and more data in general. 
