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