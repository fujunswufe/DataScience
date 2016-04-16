###Springleaf

######Categorical features
1. [High cardinality features](http://stackoverflow.com/questions/26473233/in-preprocessing-data-with-high-cardinality-do-you-hash-first-or-one-hot-encode)(leave-one-out encoding)
2. parameter tuning(XGBoost)
   * learning rates vs. number of rounds
   * max depth vs min child weight (Tree-based parameters)
   * Boosting parameters(row sample, column sample)
    
3. High correlated features
   * removed for linear models
   * tree-based models(leave out for the models)

4. [Dates, Time-Series](https://spark-summit.org/east-2016/events/time-series-analysis-with-spark/)

5. [What is the difference between categorical, ordinal and interval variables?](http://www.ats.ucla.edu/stat/mult_pkg/whatstat/nominal_ordinal_interval.htm)
