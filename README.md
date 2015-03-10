# Git Analytics Sample Datasets

Datasets are in CSV format, gzipped for storage efficiency.  Each dataset consists of 3 files, 
- \<project\>_\<importance\>_feature_vectors.csv.gz - Numpy array saved using numpy.savetext()
- <project>_<importance>_labels.csv.gz - Single column binary label for each feature vector.  This value is the result of comparing the guilt value with a threshold value, where the threshold value is selected such that the number of labeled commits (value=1) roughly corresponds to the number of actual bugs (subject to minimum importance value)
- <project>_<importance>_info.csv.gz - Other info each feature vector
 - Git Commit ID (SHA)
 - actual guilt value associated each commit
 - ordering number of each commit.  1 for first commit in repo.

The sample datasets are all derived from OpenStack.  <project> values include:
- cinder
- glance
- heat
- nova
- swift

The guilt value computed with each commit based based the association of the commit with any subsequent bug fix.  Higher importance bugs fix (e.g.:  Critical vs High vs Medium vs Low) get higher weight in the guilt calculation.  Standard <imortance> values include:
- critical - only includes Criticalbug fixes
- highplus - includes Critical and High bug fixes
- mediumplus - includes Critical, High and Medium bug fixes
- highplus - includes Critical, High, Medium and Low bug fixes
