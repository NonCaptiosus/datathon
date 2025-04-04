# Datathon 2025 

This is the task for the regression challenge in Datathon 2025

The task and description of dataset features can be found in [Regression description](Regression-desc.pdf).

final_work.ipynb contains the best version of the task and how it should have been analyzed etc.

datahon-day.ipynb is the notebook file created during the datathon and post-datathon.ipynb has the work and testing done just before the submition of the final report.

I am still unclear how I got the results from img below Best result from pre-processing as I cannot reproduce it anymore. 

![Best result from pre-processing](images/best-results.png)

<br>
First testing<br>
    - Removed url column<br>
    - Removed zero word articles<br>
    - Outlier check with Z-score, from 27681 articles to 14853<br>
    - Best model: Linear Regression<br>
    - Best score: 8334<br>
    - PCA: 59<br>
<br>
Second testing<br>
    * Removed url column<br>
    * Eliminating outliers by "hand"<br>
        - removed all articles with shares > 80,000<br>
        - removed all articles with n_tokens_content > 4000<br>
        - removed all articles with zero words, 862 articles<br>
        - from 28543 articles to 27599 from zero words, 82 articles removed by the shares and n_tokens_content
    - Best model: MLP<br>
    - Best score: 5338<br>
    - PCA: 15<br>
    - Notable models Lasso, Ridge, Baysian Ridge, Elastic Net. Score: 5372 - 5382<br>
<br>
Third testing<br>
    - Number of articles in the trainning set here is 2244<br>
    - this test should not be taken into consideration
    - all steps from second test done<br>
    - removed kw_min_max bigger than 400,000. Here also the outlier should be <br>
    - removed kw_max_max bigger than 400,000. Mistake here as the cutoff for this is 843300 <br>
    - Best model: Ridge<br>
    - Best score: 4147<br>
    - PCA: 59<br>
    - Notable models Linear, Lasso, Elastic Net<br>

![Results with 25k removed articles](images/third-testing.png)<br>

<br>
Fourth testing<br>
    * Removed url column<br>
    * Eliminating outliers by "hand"<br>
        - improved the outlier threshhold on third testing
        - removed kw_min_max, kw_max_max according to the outlier threshhold
    - Best model: Ridge<br>
    - Best score: 5415<br>
    - PCA: 59<br>
Worse score even though the improvement of the outliers
<br>
Doing permutation importance to figure out what features seem more important, kw_avg_avg, self_referencing_avg_sharess seemd the most important ones but i needed to remove outliers first in those before being certain. Decision Trees, Random Forest and XGBoost were removed from the pipeline and created a separate one to test them because they do not need normalization or standartization and I was doing that in the previous tests which should be the reason for their bad performance.
<br>
<br>
Fifth testing<br>
    - From the outliers in test three, kw_max_avg, kw_avg_avg, self_reference_avg_sharess, num_hrefs were added but results did not change much<br>
    - Best model: Ridge<br>
    - PCA: 59<br>
    - Score: 5342<br>
<br>
Sixth testing, Hyperparameter tunning<br>
    - Best results: 4358<br>
    - Best model: Lasso<br>
    - Params: {'model__alpha': np.float64(10.0)}<br>

![Results with 25k removed articles](images/hyperparameter-tunning.png)<br>
 