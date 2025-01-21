# SLA-Driven-Performance-Prediction-for-Co-Hosted-DNNs
This repository provides data and scripts to create and evaluate the performance prediction model proposed in the paper "SLA-Driven Performance Prediction for Co-Hosted DNNs" by Shah et al. The data included in this repository is collected on the performance of 4 DNNs co-hosted on a single system. This data was collected by running these DNNs on various resources, incoming request rates, and container configurations. Each co-host setup involves two DNN instances running together on shared resources. The performance data in these configurations was collected using httperf. The provided scripts allow data extraction from httperf scripts, feature selection, performance modeling for predicting compliance to certain response time targets, data visualization, and analysis of results.

### Features and Target Labels
The included dataset collects a variety of performance metrics using httperf when DNNs are run in pairs on various levels of shared resources. The primary performance metric in this study is the _average response time_ (ms) observed in a minute-long session of a DNN receiving requests at a particular request rate at a specific resource setting, while being co-hosted with a different DNN. Given that tight SLAs bind most commercial DNNs, we model performance by predicting whether the response time of a DNN in a given request rate-resource setting will fall within a given response time target. We set three arbitrary response time targets and label them as **SLA_Level_1**, **SLA_Level_2**, and **SLA_Level_3**. These three response time targets act as our target labels.

To model performance, we use the following features:

**DNN-1**: First co-hosted DNN.

**DNN-2**: Second co-hosted DNN.

**Rate**: Request per second arriving at the server for each DNN.

**Processors**: Level of processor instances allocated to each co-hosted DNN.

**Memory**: Level of overall memory allocated to each co-hosted DNN. This varies at the same level as the processors.

**Baseline-Response**: Response time of first co-hosted DNN at a baseline setting i.e., when the DNN is running in isolation at half of the corresponding co-host resources and same request rate.

**Baseline-Sum**: Response time of second co-hosted DNN at a baseline setting.

**UL-1**: Utilization level of the first co-hosted DNN in isolation. This is quantified as a numerical ranking of the DNN based on its aggressiveness toward needed resources for execution.

**UL-2**: Utilization level of the second co-hosted DNN in isolation.

### Thin and Fat Containers
This study observes the response time behavior of co-hosted DNNs in two different container settings: _fat_ and _thin_.  _Thin_ containers host each DNN in two separate containers that are each allocated specific processors. _Fat_ containers host both co-hosted DNNs in the same container, thus sharing memory and processor resources allocated to the container. A fat container configured with a specific resource level will have double the processors and memory allocated to the equivalent thin container. Observing the performance of co-hosted DNNs in these two settings helps us identify the most effective deployment setup for DNNs when they are sharing system resources. 

### Summary of Results
