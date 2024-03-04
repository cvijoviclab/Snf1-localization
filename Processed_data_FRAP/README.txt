this folder contains the measured rawdata as well as calculations made with these to normalize and correct for bleaching
explanation of what can be found in the files: 

240304_FRAP_complete_dataset.csv
carbonsource : cabonsource the cells were exposed to
cellno: number of the cell that was measured within the experiment
experiment: experiment occasion
ID: unique identifier
measurement_count: count of frames
time: total time during experiment
recovery_time: time with bleaching timpoint = 0
area_nucleus: area of the nucleus measured
area_cell: area of the cell measured
area_background: area of backgorund measured
area_reference: area of the reference measured
raw_int_nucleus: measured intensity of bleached nucleus
raw_int_background: measured intensity of background
raw_int_reference: measured intensity of reference cells
reference_minus_background: (raw_int_reference - raw_int_background)
nucleus_minus_background: (raw_int_nucleus - raw_int_background)
normalized_nucleus: nucleus_minus_background/mean of nucleus_minus_background during pre bleach measurements
normalized_reference:	reference_minus_background / mean of reference_minus_background during pre bleach measurements 
bleached_volume	nucleus_normalized_corrected: bleach corrected values of normalized_nucleus after applying non linear regression 


240209_bleach_correction.csv

estimated parameters and statistics of non linear regression of median normalized reference intensities. parameters were used on normalized nucleus indtensities to correct for bleaching. 