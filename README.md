# Hi-C Notes #

### Cooler ###

1. Cooler wraps around HDF5 files (use h5py package for python)

2. **.mcool** adds an additional layer of organization to combine multiple **cooler** files into one

   - This is like an h5 file. Just use the `.keys()` command to identify what additional layer(s) there are. 
   - At the bottom layer, a single cooler file should have `['bins', 'chroms', 'indexes', 'pixels']` as the keys

3. Cooler file is organized like a dictionary

4. Useful commands:

   - `c=cooler.Cooler(filepath)` creates an cooler object. This object is serialized and is only opened when needed. `c` will be referred as the general cooler file 

   - `c.info` prints out everything about this cooler file

   - `c.chromnames` prints out the chromosome names

   - `c.chromsizes` prints out the sizes of each chromosome

   - `c.bins()` access the bins. This is sliceable like a datafra  me. For instance, `c.bins()[:5]`

   - `c.bins()['weight']` returns the weight for each bin 

   - `c.pixels()` returns the non-zero upper triangle entries. If using `c.pixels(join=True)`, then the bins IDs are expanded into genomic bin coordinates. The object returned by this command is a pandas dataframe, easy to dump into file.  

   - `c.matrix()` returns a 2D numpy array. `c.matrix(balance=True)` will normalize the matrix. 

   - To visualize the contact matrix, we can use the following command

     - ```python
       fig = plt.figure(figsize=(10, 10))
       ax = fig.add_subplot(111)
       im = ax.matshow(np.log10(arr), cmap='YlOrRd')
       fig.colorbar(im)
       ```

   
