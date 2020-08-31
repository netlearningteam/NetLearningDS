# NetLearningDS

## 1.  Overview:

There are 3 datasets used in the paper net learning, namely DS1, DS2, DS3. The data set information is shown in the table below.

|      | Training - Test | Graph |
| ---- | --------------- | ----- |
| DS1  | Training        | 800   |
| Test | 200             |       |
| DS2  | Training        | 4800  |
| Test | 1200            |       |
| DS3  | Training        | 22500 |
| Test | 7500            |       |



## 2.  File Structure

> File tree:
>
> │ NetLearningDatasetDocumentation.docx
>
> │ example.html
>
> │ example.ipynb
>
> │ example.pdf
>
> │ 
>
> ├─.ipynb_checkpoints
>
> │   example-checkpoint.ipynb
>
> │   
>
> ├─DS1
>
> │ ├─ori_data
>
> │ │   test_data.json
>
> │ │   train_data.json
>
> │ │   
>
> │ └─preprocessd_data
>
> │     test_data.json
>
> │     train_data.json
>
> │     
>
> ├─DS2
>
> │ ├─ori_data
>
> │ │   test_data.json
>
> │ │   train_data.json
>
> │ │   
>
> │ └─preprocessd_data
>
> │     test_data.json
>
> │     train_data.json
>
> │     
>
> ├─DS3
>
> │ ├─ori_data
>
> │ │   test_data.json
>
> │ │   train_data.json
>
> │ │   
>
> │ └─preprocessd_data
>
> │     test_data.json
>
> │     train_data.json
>
> │     
>
> └─visualization_for_ds1
>
>  

**Description:**

**DS+{index}**: The location where the index of the data set is stored.

**ori_data**: Store the information that constitutes the original petri net. Original petri net (A+, A-, M0), reachable graph, λ, average number of markers and so on.

**preprocessd_data**: Preprocess the original ori_data into the input information of the net learning algorithm.

**visualization_for_ds1**: Visualize the first 80 data in the training set and the first 20 data in the test set in the DS1 data set. Including visualization reachable graph, visualization of the original structure of petri net.

**test_data.json**: store test data.

**train_data.json**: store training data.



## 3.  Data structure description

We save the data as a json file. The structure is as follows:

 

> ├─ori_data/train_data.json
>
> │ ├─data1
>
> │ │   petri_net:
>
> │ │   arr_vlist:
>
> │ │   arr_edge:
>
> │ │   arr_tranidx:
>
> │ │   spn_labda:
>
> │ │   spn_mu:
>
> │ └─data2
>
> │ │   petri_net:
>
> │ │   arr_vlist:
>
> │ │   arr_edge:
>
> │ │   arr_tranidx:
>
> │ │   spn_labda:
>
> │ │   spn_mu:
>
> │     
>
> ├─preprocessd_data/train_data.json
>
> │ ├─data1
>
> │ │   node_f:
>
> │ │   edge_index:
>
> │ │   edge_f:
>
> │ │   label:
>
> │ └─data2
>
> │ │   node_f:
>
> │ │   edge_index:
>
> │ │   edge_f:
>
> │ │   label:
>
>  

 

**Description**:

**data+{index}**: Store the index data.

**ori_data**:

**petri_net**: Original petri net structure, (A+, A-, M0).

**arr_vlist**:: The vertex set of the reachable graph.

**arr_edge**: The set of reachable graph edge indexes. For example: [0,1] means that there is a directed arc from 0→1 between the 0th vertex and the first vertex.

**arr_tranidx**: The number of changes in the original petri net on the reachable graph.

**spn_labda**: The λ corresponding to each arc of the reachable graph.

**spn_mu**: The average number of markers.

 

**preprocessd_data**:

**node_f**: Node features of the net learning algorithm.

**edge_index**: edge index of the net learning algorithm.

**edge_f**: Edge features of the net learning algorithm.

**label**: The label value of the net learning algorithm.



## 4.  Example of reading json file and results 

We demonstrated an example of reading data, saved in example.ipynb.

For the convenience of reading, we export example.ipynb into  html formats.