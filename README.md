# ASR Prep
This repository will track changes within the ASR prep.

The project is divided into a layout that aligns with a MVC Architecture(Model, View and Controller). Where the Model stores and manipulates asset information and contains any calculations that are done on this data such as the calculation of weights and other measures. The View handles the creation of tables, graphs and optionally the CLI interface itself and the Controller manages the flow of data between the Model and View, handling user commands. For this purpose I would suggest downloading ASRmodel.ipynb , ASRView.ipynb and ASRcontroller.ipynb. The file Main.ipynb shows a very basic example on how to use the project. While the file "ASR model prep.ipynb " contains the complete class without the correct architecture. For this reason this file together with "ASRmodel_cleaned.ipynb" can be ignored for now. 

Now I will walk through the "Main.ipynb" file to illustrate how to use the project. 
Th %run commands are used to import modules when executing in jupyter notebook. When using Visual Studio Code this line can be interchanged by import ASRmodel, import ASRView and import ASRcontroller:

![image](https://github.com/user-attachments/assets/17b01521-0454-4684-b538-390893ef6471). 


