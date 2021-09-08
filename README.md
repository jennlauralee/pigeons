# pigeons

EXPERIMENTAL FILES (for running the task): Pigeons_expt1.zip (requires psychtoolbox) 

RAW SUBJECT DATA: z_raw_data_expt1
Block concatenated subject data: z_concat_data_expt1

You can run the main processing steps in alphabetical order by following the alphabetical order of scripts. Scripts call on supporting functions in the functions zip.

A_readdata reads and cleans the raw data; just modify the file paths.

B_plotsummarystats provides summary statistic plots that show key trends in response and confidence data broken down by N pigeons, C=0 vs. C=1, etc. (without model predictions)

C_modelfitting calls C_specifymodel_v2 and C_modelpredictions_V2. It is the main script to run to fit a custom or pre-set model to subject data. It will save the model fit results in a separate .mat file.

C_specifymodel_v2 This function (called by C_modelfitting) will take as input the index of the model you want to fit and whether or not you want to fit a model with flexible probability of affiliation (p_aff). The output is a "model" object that has the parameter information, upper and lower bounds of each parameter, and model category information for that model index (eg belonging to model family A, B, C, D or H).

C_modelpredictions_v2 This function (called by C_modelfitting) will take the model information output by C_specifymodel_v2 as well as specific parameter values, stimulus information, and behavioural data, and will output a NLL that can be used to optimize the model parameters for best fit. This function also provides a prediction of the proportion of feeder present responses for each stimulus identity input, and will output the estimated decision variable (false_d) for each stimulus according to the model. This function is called by BADS (Bayesian adaptive directed search) in C_modelfitting to provide fitted parameters.

D_callplotdatawithfits After model fitting, run this function to visualize model predictions against data. Set "whichfig" to 1, 2, or 3 to provide a breakdown of "feeder present" responses by N, C=1 vs C=0 category, and other summary statistics, respectively. 

F_LLR_distributions This function outputs a visualization of the decision variable distributions (log posterior ratio estimates) of each model; set modelidx to the model of interest and match it to the predicted LLR pre-saved within STIM.

F_RT_correlations
F_confidence_correlations
F_agglomcount_correlations

These three functions output the correlation of models' decision variables to subject reaction time and confidence data. F_agglomcount_correlations specifically plots a comparison of the number of iterations performed by the agglomerative clustering algorithm (model 11) with subject reaction time data. 

