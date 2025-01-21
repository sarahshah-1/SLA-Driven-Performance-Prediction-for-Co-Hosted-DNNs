# SLA-Driven-Performance-Prediction-for-Co-Hosted-DNNs
This repository provides data and scripts to create and evaluate the performance prediction model proposed in the paper "SLA-Driven Performance Prediction for Co-Hosted DNNs" by Shah et al. The data included in this repository is collected on the performance of 4 DNNs co-hosted on a single system. This data was collected by running these DNNs on various resources, incoming request rates, and container configurations. Each co-host setup involves two DNN instances running together on shared resources. The performance data in these configurations was collected using httperf. The provided scripts allow data extraction from httperf scripts, feature selection, performance modeling for predicting compliance to certain response time targets, data visualization, and analysis of results.

### Features and Target Labels
The included dataset collects a variety of performance metrics using httperf when DNNs are run in pairs on various levels of shared resources. The primary performance metric in this study is the _average response time_ observed in a minute-long session of a DNN receiving requests at a particular request rate at a specific resource setting, while being co-hosted with a different DNN. Given that tight SLAs bind most commercial DNNs, we model performance by predicting whether the response time of a DNN in a given request rate-resource setting will fall within a given response time target. We set three arbitrary response time targets and label them as **sla_level_1**, **sla_level_2**, and **sla_level_3**. These three response time targets act as our target labels.

To model performance, we use the following features:


### Thin and Fat Containers

### Summary of Results
