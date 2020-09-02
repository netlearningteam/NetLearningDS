# Net Learning Datasets 

## 1.  Overview:

 We generated three stochastic Petri nets(SPN) data sets, in order to test the effectiveness of the “Net Learning” algorithm. The data in the data set is randomly generated, and the following steps are mainly used: (1) First, a SPN is randomly generated. (2) Generate reachability graph based on SPN. (3) Calculate the SPN performance index based on the reachable graph.  



## 2.  File Structure

> File tree:
>
> │ README.md
>
> │ example.html
>
> │ example.ipynb
>
> 
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

### **Description:**

**DS+{index}**: The location(directory)  where the index of the data set is stored.  For example, the storage location (directory) of the first data set is DS1.

**ori_data**: Store the information of a petri net, including the original petri net (![](https://latex.codecogs.com/gif.latex?{A^{&plus;}}^{T}$,&space;${A^{-}}^{T}$,&space;${M_{0}}^{T})), the reachable marking graph, λ, the average number of tokens and so on, where ![](https://latex.codecogs.com/gif.latex?A^&plus;,A^-)are adjacency matrices of the Petri net, ![](https://latex.codecogs.com/gif.latex?M_0)is the initial marking, λ is the average firing rate of a transition. 

Store the information that constitutes the original petri net. Original petri net (![](https://latex.codecogs.com/gif.latex?{A^{&plus;}}^{T}$,&space;${A^{-}}^{T}$,&space;${M_{0}}^{T})), reachable graph, λ, average number of tokens and so on.  Where ![](https://latex.codecogs.com/gif.latex?M_0) is the initial marking,  and  ![](https://latex.codecogs.com/gif.latex?A^&plus;,A^-)are the incidence matrix . 

**preprocessd_data**: Preprocess the original ori_data into the input information of the net learning algorithm.

**visualization_for_ds1**:  Visualize the 100 data in the DS1 data set，including visualization of the reachable marking graph, and visualization of the original structure of petri net.

**test_data.json**: store test data.

**train_data.json**: store training data.



## 3.  Data structure description

We save the data as a json file. There are two forms of data, including: unprocessed raw SPN data (**ori_data**), and input data of net learning algorithms (**preprocessd_data**) obtained after preprocessing the original SPN data. **Ori_data** and **preprocessd_data** in each data set contain two json files, including: training set (train_data.json) and test set (test_data.json). The json  structure is as follows:

 

1.   ori_data/train_data.json



> ├─data1
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
> │ │   spn_steadypro:
>
> │ │   spn_markdens:
>
> │ │   spn_mu:
>
> └─data2
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
> │ │   spn_steadypro:
>
> │ │   spn_markdens:
>
> │ │   spn_mu:
>



2.   preprocessd_data/train_data.json



> ├─data1
>
> │ │   node_f:
>
> │ │   edge_index:
>
> │ │   edge_f:
>
> │ │   label:
>
> └─data2
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

 

### **Description**:  

#### ori_data

**data+{index}**: Store the index data.

**petri_net**: Original petri net structure,(![](https://latex.codecogs.com/gif.latex?{A^{&plus;}}^{T}$,&space;${A^{-}}^{T}$,&space;${M_{0}}^{T})).

**arr_vlist**: The vertex set of the reachable graph.

**arr_edge**: The set of reachable graph edge indexes. For example: [0,1] means that there is a directed arc from 0→1 between the 0th vertex and the 1th vertex.

**arr_tranidx**: The number of transitions in the original petri net on the reachable graph.

**spn_labda**: The λ corresponding to each arc of the reachable graph.  Where λ is the average trigger rate of transitions.

**spn_steadypro**:  SPN steady state probability.

**spn_markdens**: SPN tokens density function.

**spn_mu**: The average number of tokens.

 

#### **preprocessd_data**:

**data+{index}**: Store the index data.

**node_f**: Node features.

**edge_index**: Edge index.

**edge_f**: Edge features.

**label**: The labels.

## 4.  Partition data set

#### Datasets

The net structure in each dataset is prototyped by different groups of specific basic net structures. By slightly adjusting the place or token to expand some new similar net structures, then every new net structure is configured with 10 different sets of λ. 

In detail, three training datasets are generated by similar processing procedures, but their scales are different. The data is processed by three steps as follows: First, *m* Petri net structures are randomly generated as the basic net structure. For example, the number of basic net structures of DS2 is 6 (i.e. *m* = 6 for DS2) as follow . Second, some simple transformations are used for each basic net structure, in order to obtain some nets similar to the basic net structure. Basic transformations include increasing (decreasing) places, increasing (decreasing) changes, and increasing (decreasing) tokens. Each basic net is transformed 100 times, and *m* * 100 transformed Petri nets are obtained. Finally, for each transformed Petri net, 10 sets of different values of λ are configured. Finally, a total of *m* * 100 * 10 different Petri nets can be generated. 

|      | basic net structures(Pc) | expanded net structures (Pc) | λ(set) | reachable  marking graph(Pc） |
| ---- | ------------------------ | ---------------------------- | ------ | ----------------------------- |
| DS1  | 1                        | 100                          | 10     | 1000                          |
| DS2  | 6                        | 600                          | 10     | 6000                          |
| DS3  | 30                       | 3000                         | 10     | 30000                         |

#### The training set and test set 

The training set and test set are divided as follows:
|      | Training - Test | Graph |
| ---- | --------------- | ----- |
| DS1  | Training        | 800   |
|      | Test            | 200   |
| DS2  | Training        | 4800  |
|      | Test            | 1200  |
| DS3  | Training        | 22500 |
|      | Test            | 7500  |

#### Schematic diagram of data set division

##### DS1

<img src="https://github.com/netlearningteam/NetLearningDS/blob/master/pics/DS1.png"   width="60%" height="60%" />

##### DS2

<img src="https://github.com/netlearningteam/NetLearningDS/blob/master/pics/DS2.png"   width="60%" height="60%" />

##### DS3

<img src="https://github.com/netlearningteam/NetLearningDS/blob/master/pics/DS3.png"   width="60%" height="60%" />

Note: The horizontal axis is expanded net structures. The vertical axis is λ.



## 5.  Example of reading json file and results 

We demonstrated an example of reading data, saved in example.ipynb.

For the convenience of reading, we export example.ipynb into  html formats.
