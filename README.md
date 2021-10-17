# Thank you for considering a Code for this paper: Attach the referene when ready 

Here, we introduce the implementation of the proposed PPG verification system and GAN (including PBGAN) models. 

There are three files included in the code & data appendix. Each files will be explained in detail.


1 - Subset_Biosec3.mat

. This file contains raw PPG data and the preprocessed PPG data which are necessary for running the codes. It is a subset of Biosec3 database with 20 subjects. Thus, performances obtained with this subset of data are different from the ones in the paper.

. Biosec3 was collected in an uncontrolled environment (i.e. usual office environment) and participants could talk during measurement. All participants have no history of heart diseases. 

. For completeness, we also provide the links for the other public datasets. You can access these databases from the following links.
PRRB: https://dataverse.scholarsportal.info/dataset.xhtml?persistentId=doi:10.5683/SP2/NLB8IT

TROIKA: https://sites.google.com/site/researchbyzhang/ieeespcup2015

Biosec1: https://www.comm.utoronto.ca/~biometrics/PPG_Dataset/index.html

- Original_Data cell array
. It has the raw PPG data before preprocessing. You can use it for observing the raw PPG signals.

. It is 3D cell array where the first dimension shows subject ID, the second one means the measurement trial in each session and the third one describes the session. 

Ex. To access the third measurement trial of subject 5 in the second session, run Original_Data{5,3,2}. 

- GAN_data cell array

. It is for running the GAN and PBGAN. You can check this original data that will be compared with synthetic one.

. It is 2D cell array where the first dimension shows subject ID and the second one denotes the input (in order: DTW, TP, FP, Cubic).

Ex. To access the subject 1 FP input, run FP_data = GAN_data{1,3}. Then, it will show the 2D array where row is the number of data and column means the number of samples. You 
can call first data by FP_data(1,1:150).

- train_data, train_label, test_data, test_label array

. These arrays are used for running the PPG verification system. You can see the train and test data with their labels. 

. In train_data and test_data, they are 3D array where the first dimension is the number of data, the second one is the number of samples and the third one is the input (in order: DTW, TP, FP, Cubic). It is concatenated sequentially with subject ID and each subject has 120 data for train set and 24 data for test set. train_label and test_label have label information (i.e. subject ID) with same order as train_data and test_data, respectively. 

Ex. To access one of subject 1’s DTW data in train set, run train_data(1,1:150,1). The label will be train_label(1).

- PBGAN_DC_syn array

. It is applied for running the PPG verification system. You can use it to observe synthetic data from PBGAN-DC (W) for each subject. 

. It has same structure as train_data and is concatenated sequentially with subject ID where each subject has 120 synthetic data. 

Ex. To access one of subject 2’s TP synthetic data, run PBGAN_DC_syn(121,1:150,2).


`2 - PPG_verification_system.ipynb`

. This code is for running the PPG verification system with synthetic data. Here, we used synthetic data generated by PBGAN-DC (W). The comments for detail information are attached inside the code. 

. It shows the validation costs, building time and performances (Accuracy, EER, ROC curve). 

. You can find the sample result inside the code. The sample result was run by WS model. To investigate other results, search ‘Set Target ID, Model type’ and change the variables ‘ID’, ‘Model_type’. All details about setting up values in these variables are covered by comments.

. Subset_Biosec3.mat should be placed in the same directory to run the code. 


3 - GAN_and_PBGAN.ipynb

. This code is used for running the GAN and PBGAN. The comments for detail information are included in the code.

. It shows the sample original data, the sample synthetic data and building time.

. You can find the sample result inside the code. The sample result was run by original DCGAN with Cubic input. To explore other results, search the ‘Set Target ID, GAN, PBGAN, Input’ and change the variables ‘ID’, ‘GAN_model’, ‘PBGAN’, ‘Data’. All details about setting up values in these variables are explained by comments.

. Subset_Biosec3.mat should be located in the same directory to run the code.



Thank you!

Dae Yon Hwang
