This is the deployment configuration for the Beacon5G RAN digital twin
The deployment files are for two data centres dc1 and dc2 in the respective folders. The deployment scripts are kubernetes YAML files that support integration with federated consul service meshes.
The annotations required for injection of sidecars are :
      annotations:
        consul.hashicorp.com/connect-inject: 'true'

Purpose
The purpose of the digital twin is to model the RAN elements, using a simulation environment, in order to permit comparison of performance with the real ORAN system. This can help with automated selection of optimal resource scheduling schemes and also detection and identification of the cause of performance differences. 
There are two options for deployment that are considered to achieve the goals. The first is that the digital twin deployment package is self-contained and performs an automated scheduling selection policy as an output. The second is when the digital twin package outputs the performance and another service or rApp makes a policy selection based on the output of the digital twin. 
In the case in which the digital twin performs the policy selections the digital twin requires the actual performance from the RAN (through dRAX or A1-EI APIs) and the output is a policy update towards the corresponding RIC instances. However, in the case that this operation is performed by a separate rApp then the output are per UE performance parameters that are exposed through the A1-EI API, which can be supported in addition to the A1-P policy API.

Overview
The RAN digital twin is a simulation model of the MAC and PHY resource allocation within the RAN. This is implemented in Matlab™ and is deployed as a container bundle using the yaml files defined in https://github.com/Tim-222/beacon/tree/master. The appropriate matlab licenses are required (2023a version with 5G toolbox) to deploy the digital twin and must be provided in the licenses PVC.
