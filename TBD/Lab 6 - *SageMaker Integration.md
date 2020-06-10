# SageMaker Integration** 

**Note:** Do NOT opt in for the new CloudFormation console for this workshop, as we are aware of a known issue which is not yet fixed.

![img](images/CloudFormation.png)

If you have already opted in, please opt out for this workshop using “Previous console” option in the left navigation panel.

![img](images/CloudFormation2.png)


**Step 1: Spin up a SageMaker endpoint (Duration 10 minutes)**

To analyze images in the video, we will make use of object detection algorithm from Amazon SageMaker. Create a SageMaker endpoint using following CloudFormation URL,

[Create-endpoint-us-west-2](https://us-west-2.console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/create/review?templateURL=https://s3-us-west-2.amazonaws.com/kvsit-beta-us-west-2/object-detection/createEndpoint.yml)

Specify “Stack name” as a unique name. Example - SageMakerEndpoint

![img](images/SageMaker endpoint.png)


Note the SageMaker ‘EndpointName’ (for this example template - Endpoint-i3BnphijUAkZ) from the “Outputs” tab. This will be needed for the next step. 

![img](images/EndpointName.png)



### Step 2: Spin up KIT infrastructure (Duration 10 minutes)

Wait for Step 1 to complete in order to capture the output value for EndpointName.

Spin up the infrastructure required to analyze video streams using following CloudFormation URL: 

[KIT-us-west-2](https://us-west-2.console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/create/review?templateURL=https://s3-us-west-2.amazonaws.com/kvsit-us-west-2/cfn-template.template.yml)

- Specify “Stack name” as a unique name. Example – KvsSageMakerDemo
- Specify “SageMakerEndpoint” from the previous step. Example – <Endpoint-i3BnphijUAkZ>
- Specify “StreamNames” as name of the KVS stream created in module #1

![img](images/KIT infrastructure.png)

### Step 3: Validate CW dashboard (Duration 2 minutes)

Once the stack is created in step 2, overview the health of the setup by visiting CW dashboard at following link,

https://us-west-2.console.aws.amazon.com/cloudwatch/home?region=us-west-2#dashboards:

![img](images/dashboard.png)




### Step 4: Validate CloudWatch log for Lambda Function (Duration 2 minutes)


**To read the Lambda log**

1.   Open the AWS Lambda console at https://console.aws.amazon.com/lambda. 
2.   Choose the Lambda function for your application. The Lambda function name is in the following format: 
```
stack-name-LambdaFunction-A1B2C3D4E5F6G
``````
3.   Choose the **Monitoring** panel. 
4.   Choose **View logs in CloudWatch**. 


![img](images/Lambda log.png)


Lambda logs shows object beings detected for each invocation and corresponding details in the Kinesis Video stream to locate the unique frame.

Workshop SageMaker endpoint model has been trained for following objects,

'person', 'bicycle', 'car', 'motor cycle', 'airplane', 'bus', 'train', 'truck', 'boat', 'traffic light', 'fire hydrant', 'stop sign', 'parking meter', 'bench', 'bird', 'cat', 'dog', 'horse', 'sheep', 'cow', 'elephant', 'bear', 'zebra', 'giraffe', 'backpack', 'umbrella', 'handbag', 'tie', 'suitcase', 'frisbee', 'skis', 'snowboard', 'sports ball', 'kite', 'baseball bat', 'baseball glove', 'skateboard', 'surfboard', 'tennis racket', 'bottle', 'wine glass', 'cup', 'fork', 'knife', 'spoon', 'bowl', 'banana', 'apple', 'sandwich', 'orange', 'broccoli', 'carrot', 'hotdog', 'pizza', 'donut', 'cake', 'chair', 'couch', 'potted plant', 'bed', 'dining table', 'toilet', 'tv', 'laptop', 'mouse', 'remote', 'keyboard', 'cellphone', 'microwave', 'oven', 'toaster', 'sink', 'refrigerator', 'book', 'clock', 'vase', 'scissors', 'teddy bear', 'hair drier', 'toothbrush'