# Project Name

panda_bear detection

![image](https://github.com/Michael13527/panda_bear-detection/assets/173301284/740a53d8-bf1b-4784-aa3e-f79df6a0f890)
![image](https://github.com/Michael13527/panda_bear-detection/assets/173301284/390eda6c-be4f-4c1c-9f7e-ec86205ba871)

A classification model that classify pandas and bears using Resnet-18

## Running this project
1. Make sure you have installed Jetson Inference and Docker Image from :                                                                                                  
 https://github.com/dusty-nv/jetson-inference/blob/master/docs/building-repo-2.md

2. Once you're still back in the jetson-inference folder, run:                                                                                                                                   
 ./docker/run.sh to run the docker container.

3. From inside the Docker container, change directories so you are in jetson-inference/python/training/classification

4. Now run your script:                                                                                                                                                                    
  python3 train.py --model-dir=models/panda_bear data/panda_bear --batch-size=NumberOfBatchFiles --workers=NumberOfWorkers --epochs=NumberOfEpochs                                   
 epochs are how many times the AI run through the entire process, te lower the epoch is, faster the training is, more inaccurate the classification is. 

5. While it's running, you can stop it at any time using Ctl+C. You can also restart the training again later using the --resume and --epoch-start flags, so you don't need to wait for training 
to complete before testing out the model.

6. Make sure you are in the docker container and in jetson-inference/python/training/classification, Run the onnx export script:                                                           
 python3 onnx_export.py --model-dir=models/panda_bear

7. Look in the jetson-inference/python/training/classification/models/cat_dog folder to see if there is a new model called resnet18.onnx there. That is your re-trained model!

8. Exit the docker container by pressing Ctl + D.
On your nano, navigate to the jetson-inference/python/training/classification directory.
Use                                                                                                                                                                                            
 ls models/cat_dog/ to make sure that the model is on the nano.
You should see a file called resnet18.onnx.

9. NET=models/panda_bear                                                                                                                                                                
   DATASET=data/panda_bear

11. Run this command to see how it operates on an image from the Bear folder.                                                                                                          
 imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test//Bear/275.jpeg Bear.jpeg

![image](https://github.com/Michael13527/panda_bear-detection/assets/173301284/33ebc332-c4af-4c8f-8f96-6ce01270e914)





[View a video explanation here](video link)
