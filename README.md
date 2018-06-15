# Empathy Scoring using KMeans
### Overview and model used:
I am using K-Means to cluster people with an overall sense of empathy and grading them on a scale of 1-5 using features selected from the dataset of the first question. I am using clustering for the following reasons:
Clustering avoids overfitting the data as compared to other models and gives us a more real-world approach to similarity between objects. Occam's razor applied to my approach. For the current case of grading a person on a fuzzy concept like Empathy, rather than hard classifying a person we can get approximate results of if the person is empathetic enough for the Alzheimer's Patients. Most of the time the problems we deal with in machine learning are very general and hard to quantize strictly, and hence a clustering approach spoke more to me than any other advanced method. Although there can be a lot of improvement further in my approach. Let's dive in on how my model works!

### Concept and flow:
My model works through the following steps:
Cleans, preprocesses data, ignoring NaN values and turning text labels into suitable quantities to prepare the feature vector and hence the example/training set. The data is fed into K-Means model with 5 clusters corresponding to a respective label on a scale of 1 through 5. After creating the clusters, the main obstacle was to deduce what each cluster represented.
I created an expression which rewards for positive features for empathy and penalizes the overall score of the cluster for negative features. It does this by adding the averages of each feature and in a cluster point and subtracting if it’s a negative feature which decides against a person being empathetic.
This finally gives us final scores of each cluster which we assign labels 1 to 5 with the score being higher for more empathy and less for lesser chance of empathy in that person.

### Features Used:
Instead of finding correlations between features and empathy, I cherry picked 16 features to relate more to the real world. The features I picked are as follows:

- Giving, an empathetic person is more charitable i.e. prone to understanding people’s situations/feelings, (+ve, added)
- Musical, Musical are for emotionally intelligent, which is a factor to be more empathetic, (+ve, added)
- Horror, Horror movies needs the person to be impervious to unseemly conditions making the person somewhat insensitive, (-ve,
subtracted)
- Romantic, liking romantic movies leads to sensitivity towards feeling and being compassionate a good indicator of empathy, (+ve Feature, added)
- Gender, Studies show female are more empathetic than men which are more logical, (Neutral, added, higher the value, more empathetic, 0:Male, 1: Female)
- Compassion to Animals, Compassion towards a life form is a strong indicator for empathy (+ve, added)
- Self-scored Empathy, Self-definitive, (+ve Feature, added)
- Keeping promises, Shows the person cares about the feelings or others (+ve Feature, Added)
- Reading(Poetry), Poetry requires the person to be emotionally intelligent and very observant with his/her surroundings (+ve Feature,
added)
- Pets, Requires the person to be loving towards a animal and accepting a living being into their lives, (+ve, Added)
- Ageing, Studies show with age it is common to have a higher sense of empathy, (+ve Feature, added)
- Daily Events, Higher observation skills and being aware of everyday occurrences indicate a sharper sense of sensibility, (+ve, added)
- Village – town, People from towns/villages tend to be more connected and compassionate for other fellow people than urban people wholead a relatively solitary existence, (Neutral, Added, 0: city, 1: Village)
- Action, Action movies support a lot of violence, non-compassionate leanings, (-ve , subtracted)
- Fake, Double faced people are less to care about people’s feelings, (-ve, subtracted)
- Only child, Studies show people with siblings are more empathetic, (Neutral, Added, 0: yes 1: no)

### Experimental Setup and explanation:

Dataset split: *80:20*, 80% training, 20% testing data
- Cherry picking 16 features with real world knowledge
- Preprocess data, by cleaning out NaN numbers, converting string columns into integer/float values, Binary values of yes or no into 0 and 1, city or village into 0 or 1, Gender into 0,1 and so on.
- Clustering using KMeans, and forming clusters with k = 5 each corresponding to a grade label
- Averaging each feature over the cluster points into a vector of [k x no_of_features] dimensions
- Scoring each cluster base on the feature quantity and its impact towards the overall score for empathy as described above in features.
- Predicting the values of the test set. The labels of the cluster correspond to the empathy score obtained in the previous set.

### Conclusion:
- The feature selection can be more precise. I considered independent features and avoided redundant ones, like, siblings, only child. They contribute the same amount of data.
- The grade scale can be more extensive, making it a little bit more precise but avoiding overfitting.
- There are definitely more precise and better performing models, but clustering is suitable as I feel the problem here is a fuzzy quantity and is best represented as groups and ranges aka clusters of similarity.


## How to run the code. 

- Make sure you install the following packages as I have extensively used thee libraries to do the project:
    - scikit-learn
    - pygal
    - pandas
    - numpy
    - matplotlib
    - progress
    - seaborn

- Download the dataset from Kaggle and place it in the same directory as the clustering.py file. 
- Make sure the dataset file name is responses.csv as it is downloaded.
- Run the clustering.py file from the terminal and it will diplay high level verbosity.
- The prepdicted labels will be saved to a file names Predicted_labels.

### RESULTS:

Check the IPython notebook in the code base for a story-setup explanantion on the process and results.

### Concept and Development by: Debojit Kaushik May 2018.