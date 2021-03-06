# Changelog

## Version 0.220
Added a groupby_apply function to utilize dask for groupby apply when its faster. Simply use as **df.swifter.groupby_apply(groupby_col, func)**. I would've extended the Pandas DataFrameGroupBy object, but he hasn't added support for that kind of extension yet. Also, removed the str_object limitation to utilizing dask. Now it will simply determine whether to use dask v pandas based on the dask_threshold (default 1 second).

## Version 0.210
Fixed a bug for row-wise applies. Thanks to @slhck for poining this out. 

## Version 0.200
Completely refactored the package as an extension to pandas, rather than an independent function call. This will allow for increased flexibility of the user and simplicity of using swiftapply.
**This new update changed the way to use swiftapply. Now the format is df.swifter.apply(func)**

## Version  0.150
Fixed bug that would allow certain functions to be applied to the entire series/dataframe, rather than to each element. For example, len(x) returned the length of the series, rather than the length of each string within the series. A special thanks to @bharatvem for pointing this out.

## Version 0.140
Added support for vectorized and pandas applies to dataframes.
Converted all string manipulations to pandas apply (unless vectorizable) because dask processes string manipulations slowly.ls

## Version 0.13
Removed numba jit function, because this was adding to the total runtime. Will do some experiments and consider readding later.

## Version 0.1
Currently works very well with pandas series, needs some work to optimize dask multiprocessing for pandas dataframes. For now, it is probably best to apply to each series independently, rather than multiple columns of a dataframe at once.
