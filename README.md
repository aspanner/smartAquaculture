# smartAquaculture
This is a repo for SmartHub.AI to help create a model with a scalable approach to traing/validation/test data labelling based on parent folder names.
This uses the fastai libraries and approach.

![Screenshot_20240321_192332](https://github.com/aspanner/smartAquaculture/assets/16040521/0873963f-b0b6-47cf-8178-d1b4d8953e7d)

The notebook creates a model called export.pkl and is based on a resnet18 architecture.

The jupyter notebook downloads the images from DuckDuckGo and stores it in the relevant folders.  
It then splits the data according to the splitter and seed setting in the code.
The images need some manual quality assurance.

The model training times and losses are depicted below. The first run is split out as it's not a fine-tuning run; the first iterations removes the model head before the finetuning starts.

![Screenshot_20240321_192646](https://github.com/aspanner/smartAquaculture/assets/16040521/427a9b6c-eb31-4bbb-9971-ac07318d8c8a)

To help with limited training data, data augmentation techniques can be applied:
![Screenshot_20240321_192811](https://github.com/aspanner/smartAquaculture/assets/16040521/ce603011-4869-44d1-9ead-baf3b6816525)

Data augmentation refers to creating random variations of our input data, such that they appear different, but do not actually change the meaning of the data. Examples of common data augmentation techniques for images are rotation, flipping, perspective warping, brightness changes and contrast changes. For natural photo images such as the ones we are using here, a standard set of augmentations that we have found work pretty well are provided with the `aug_transforms` method.

The confusion matrix for the inital run with unclean data is as shown below
![Screenshot_20240321_192450](https://github.com/aspanner/smartAquaculture/assets/16040521/9c5e1b62-6b52-49fd-b4f6-bb285ecca4c6)

The notebook also utilises a data cleansing tool built into the notebook to help re-classify or remove/keep images that a training run has identified as challenging.
This can be either through:
- Correct prediction with low confidence
- Wrong predictions (both with high or low confidence)
![Screenshot_20240321_193652](https://github.com/aspanner/smartAquaculture/assets/16040521/f0c436ec-85e1-400a-a628-792ef531861a)
That's why the data sets needs to be QA'ed before going into production.
