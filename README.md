# stcv_deployment template
Multiple Spirent STCv deployer HEAT template
============================================
STCv deployer package is a collection of 2 heat templates (also called as HOT files) as defined in the OpenStack HOT specification.
For detailed information about the Heat Orchestration Templates, see the OpenStack Template Guide at http://docs.openstack.org/developer/heat/template_guide/
This package consists of following files:
1. 2_stcv_and_1_labserver_heat_template.yaml (Template for the deployment of 2 STCv instances along with 1 labserver)
2. 2_stcv_and_1_labserver_heat_params.yaml (Configurable parameters to be passed during the deployment of template)

The template can be used for the deployment of 2 STCv instances and 1 lab server instance On Openstack or other cloud platform (should support HEAT templates).
The floating IPs will be assigned to the created instances and can be used to access these instances from outside.
The image,flavor,test network details etc. to be used for STCv and labserver can be configured in  "2_stcv_and_1_labserver_heat_params.yaml" file.

How to use
==========
Prerequesites
-------------
1. Cloud to be used (Openstack or any other) should support HEAT based Orchestration.
2. STCv and labserver images to be used should already be present in image repository of the cloud.
3. These template files should be at accessible location of the server where Openstack CLI/Openstack Horizon is being used.
On Openstack cloud:
------------------
Using Horizon:
1. Login to dashboard and go to Projects->Orchestration.
2. Go to Orchestration->Stacks.
3. Click Launch Stack.
4. Choose the Template File "2_stcv_and_1_labserver_heat_template.yaml" from its location on your machine, then click Next.
5. Select the path of "2_stcv_and_1_labserver_heat_param.yaml" file in parameter section.
6. Click Launch 
5. Check instances section of Openstack dashboard that 2 STCv and 1 labserver instances must be in running state with floating IPs assigned to these.
6. Use the floating IPs to connect to these instances.

Using Openstack CLI:
===================
1. Go to controller node and run the credential file of specific tenent to login using openstack client.
2. Run the following command to deploy the template:
   controller$ heat stack-create stack_name --template-file <PathOfHeatTemplateFile> -e <PathOfHeatTemplateParamFile>  
3. Check the status of delployed stack.
   controller$ heat stack-list
   
   
Note: Please contact satish.verma@spirent.com for any updations required.
