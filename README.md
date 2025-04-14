# ASR Prep
This repository will track changes within the ASR prep.

The project is divided into a layout that aligns with a MVC Architecture(Model, View and Controller). Where the Model stores and manipulates asset information and contains any calculations that are done on this data such as the calculation of weights and other measures. The View handles the creation of tables, graphs and optionally the CLI interface itself and the Controller manages the flow of data between the Model and View, handling user commands. For this purpose I would suggest downloading ASRmodel.ipynb , ASRView.ipynb and ASRcontroller.ipynb. The file Main.ipynb shows a very basic example on how to use the project. While the file "ASR model prep.ipynb " contains the complete class without the correct architecture. For this reason this file together with "ASRmodel_cleaned.ipynb" can be ignored for now. 

Now I will walk through the "Main.ipynb" file to illustrate how to use the project. 
Th %run commands are used to import modules when executing in jupyter notebook. When using Visual Studio Code this line can be interchanged by import ASRmodel, import ASRView and import ASRcontroller:

![image](https://github.com/user-attachments/assets/17b01521-0454-4684-b538-390893ef6471). 

Stocks within the portfolio have the characteristics: Ticker, Sector, Asset Class, Quantity Purchased and Purchase Price. Stocks can be added using the syntax controller.add_stock() and examples are shown beneath:

![image](https://github.com/user-attachments/assets/27fee9fb-ee73-4870-9aed-f9a96a57d598)

Data related to these stocks are downloaded using a Yahoo Finance package. To download the data for all stocks within the portfolio the syntax controller.load_data(begin_date) can be used.
The entry within this function is the start date at which data is collected, the end date is automatically coded at the current date. 

![image](https://github.com/user-attachments/assets/bff64a11-028f-454e-b014-2a3b63bf5c02)

The current price of an equity can be derived using the syntax controller.show_current_price("AAPL") where "AAPL" responds to the ticker of the equity. Important to use a ticker that is in the portfolio. 

![image](https://github.com/user-attachments/assets/4f5d96ef-2d28-4ea8-8c6b-b55da862d3e9)

The portfolio value(quantity * current price of 1 share) can be derived on asset level, sector level or asset class level. This can be done using the syntax controller.show_portfolio_value(by='level').
If 'level' = 'asset' the portfolio value will be shown for all equities seperately.
if 'level' = 'sector' the portfolio values will be aggregated based on their sector.
if 'level' = 'class' the portfolio values will be aggregated based on their asset class. 

Since there are only stocks within the portfolio putting the level= 'class' inmediately shows the total portfolio value. By default 'level' = asset and controller.show_portfolio_value() will return the portfolio values for all equities seperately. 
![image](https://github.com/user-attachments/assets/c2967567-0c79-44ec-af33-01bf7baa3bbd) ![image](https://github.com/user-attachments/assets/e1685a8a-4095-4a00-bf53-7d82ca480ea6) ![image](https://github.com/user-attachments/assets/3f07e361-37f9-47df-9373-0b3bef0673ed)

The portfolio weights can be accesed very similarly to the portfolio value. Using the syntax controller.show_portfolio_weight('level'). Again 'level' can be equal to 'asset', 'sector' or 'class'. 
![image](https://github.com/user-attachments/assets/073d1e2b-80b7-46e3-a943-e10f7978cd2c) ![image](https://github.com/user-attachments/assets/1f83bc80-eb9c-44ed-9fcb-31412ac0d3ca) ![image](https://github.com/user-attachments/assets/c22ee128-2c4a-43e0-aef2-0d005247e8cb)











