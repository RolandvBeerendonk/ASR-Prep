# ASR Prep
This repository will track changes within the ASR prep.

The project is divided into a layout that aligns with a MVC Architecture(Model, View and Controller). Where the Model stores and manipulates asset information and contains any calculations that are done on this data such as the calculation of weights and other measures. The View handles the creation of tables, graphs and optionally the CLI interface itself and the Controller manages the flow of data between the Model and View, handling user commands. For this purpose I would suggest downloading ASRmodel.ipynb , ASRView.ipynb and ASRcontroller.ipynb. The file Main.ipynb shows a very basic example on how to use the project. While the file "ASR model prep.ipynb " contains the complete class without the correct architecture. For this reason this file together with "ASRmodel_cleaned.ipynb" can be ignored for now. 

Now I will walk through the "Main.ipynb" file to illustrate how to use the project. I will start of with a screenshot of this file. Note that it's also included in the repository. 
![image](https://github.com/user-attachments/assets/c8a7961d-0324-4075-8950-17bece20e245)

The %run commands are used to import modules when executing in jupyter notebook. When using Visual Studio Code this line can be interchanged by import ASRmodel, import ASRView and import ASRcontroller:

![image](https://github.com/user-attachments/assets/17b01521-0454-4684-b538-390893ef6471). 

Stocks within the portfolio have the characteristics: Ticker, Sector, Asset Class, Quantity Purchased and Purchase Price. Stocks can be added using the syntax controller.add_stock() and examples are shown beneath:

![image](https://github.com/user-attachments/assets/27fee9fb-ee73-4870-9aed-f9a96a57d598)

Data related to these stocks are downloaded using a Yahoo Finance package. To download the data for all stocks within the portfolio the syntax controller.load_data(begin_date) can be used.
The entry within this function is the start date at which data is collected, the end date is automatically coded at the current date. 

![image](https://github.com/user-attachments/assets/bff64a11-028f-454e-b014-2a3b63bf5c02)

To show the evolvement of stock prices within the portfolio the syntax controller.show_historical_prices(tickers=['AAPL',"MSFT"], individual_graph=False) can be used.By default tickers will be equal to None resulting in all assets being shown. However if the user only wants to see the evolvement of a part of his portfolio this can be done by specifying the tickers like done above using tickers=["AAPL", "MSFT"]. The indiviual_graph=False gives the user the opportunity to select if he wants to have a separate graph. Switching this to through will in addition to the combined graph also plot separate graphs.  

![image](https://github.com/user-attachments/assets/7c092b6c-8ba9-41a8-9313-beedafb45b1d)
![image](https://github.com/user-attachments/assets/d6775a03-03c3-4a51-9f02-d08178098be6)
![image](https://github.com/user-attachments/assets/839fb96d-c709-45c0-8fbf-d9608fb41ecf)

The return of the assets since the start date can be plotted using the syntax controller.show_cumulative_return()

![image](https://github.com/user-attachments/assets/0d7ba359-b67f-4b85-9fa9-dcfd9f2e3f08)


The current price of an equity can be derived using the syntax controller.show_current_price("AAPL") where "AAPL" responds to the ticker of the equity. Important to use a ticker that is in the portfolio. 

![image](https://github.com/user-attachments/assets/4f5d96ef-2d28-4ea8-8c6b-b55da862d3e9) ![image](https://github.com/user-attachments/assets/b626527f-1737-42df-adbc-5b6ce9aae1f4)


The portfolio value(quantity * current price of 1 share) can be derived on asset level, sector level or asset class level. This can be done using the syntax controller.show_portfolio_value(by='level').
If 'level' = 'asset' the portfolio value will be shown for all equities seperately.
if 'level' = 'sector' the portfolio values will be aggregated based on their sector.
if 'level' = 'class' the portfolio values will be aggregated based on their asset class. 

Since there are only stocks within the portfolio putting the level= 'class' inmediately shows the total portfolio value. By default 'level' = asset and controller.show_portfolio_value() will return the portfolio values for all equities seperately. 

![image](https://github.com/user-attachments/assets/c2967567-0c79-44ec-af33-01bf7baa3bbd) ![image](https://github.com/user-attachments/assets/e1685a8a-4095-4a00-bf53-7d82ca480ea6) ![image](https://github.com/user-attachments/assets/3f07e361-37f9-47df-9373-0b3bef0673ed)

The portfolio weights can be accesed very similarly to the portfolio value. Using the syntax controller.show_portfolio_weight('level'). Again 'level' can be equal to 'asset', 'sector' or 'class'. 

![image](https://github.com/user-attachments/assets/073d1e2b-80b7-46e3-a943-e10f7978cd2c) ![image](https://github.com/user-attachments/assets/1f83bc80-eb9c-44ed-9fcb-31412ac0d3ca) ![image](https://github.com/user-attachments/assets/c22ee128-2c4a-43e0-aef2-0d005247e8cb)

Visualizing portfolio weights on 'asset', 'sector' or 'class' level within a circle diagram can be done using the syntax controller.show_portfolio_circle(). Again by default this is on asset level. 

![image](https://github.com/user-attachments/assets/fe8d7cc9-ea62-40c2-8746-8420c0ea0b04) ![image](https://github.com/user-attachments/assets/ec3cbc6a-115f-4117-8f87-86d82fc41165)  ![image](https://github.com/user-attachments/assets/0c0ee8bd-2868-43fd-ad35-31e001ddc143)

Analyzing the increase or decrease of portfolio compartiments is done comparing the current price today and the purchase price the assets where originally bought for. This can be done using the syntax controller.show_portfolio_summary('level') and again can done on asset level, sector level or asset class level. Similarly as within the other function above. 

![image](https://github.com/user-attachments/assets/4490596a-5bf4-4570-a547-367b46a39cb9) ![image](https://github.com/user-attachments/assets/ad877ab2-7feb-4046-ab4b-b4ffa7cb81bc) ![image](https://github.com/user-attachments/assets/d65113a9-e1cb-4b68-858a-bf4bbdffda28)


The correlation between different assets in the portfolio can be visualized using the syntax controller.show_correlation_plot(). This is coded on asset specific level and cannot be converted to sector or asset class level. 

![image](https://github.com/user-attachments/assets/da3f6691-9bc0-4654-905e-df99ee2ed572)

The Value at Risk of the assets within the portfolio in the past years can be visualized using the syntax controller.show_var_plot(). This is done on specific asset level and cannot be converted to sector or asset class level. 

![image](https://github.com/user-attachments/assets/9c5cd86f-8d38-45ef-9ab0-e31fc461785b)

To simulate and plot paths for all equities separately for the next 15 years the syntax controller.simulate_and_plot_stock_paths(n_plot_paths=1000) can be used. The n_plot_paths= denotes the amount of simulations within the graph. For this purpose a Stochastic Differential Equation is used where the mu and sigma are from data in the past. To make sure prices cannot become negative, I assume a log normal distribution. 

![image](https://github.com/user-attachments/assets/6b394c1c-47d9-4265-a267-a156d551449e) ![image](https://github.com/user-attachments/assets/2cf96d76-2dff-45ac-b9ed-a7faeafbccfc) ![image](https://github.com/user-attachments/assets/6e28475b-a31c-4f86-8daa-5bb96c3c21ab)

Note: 3500-4000 days doesn't look like 15 years however, due to 252 trading days it actually is. 

The portfolio value can also be simulated for the next 15 years. To do this, I use the simulation of the indivual stocks and multiply them by the weights that are active at the current moment. To derive this the syntax controller.simulate_and_plot_portfolio_paths(mode='quantiles', n_plot_paths=1000) can be used. The variable n_plot_paths denotes the amount of simulations in the graph. While the mode can be equal to 'sample'  showing the simulations or alternatively 'quantiles' which will show the 5% quantiles. 

![image](https://github.com/user-attachments/assets/35782a12-45ba-4fbc-b3e7-02bac14825e5) ![image](https://github.com/user-attachments/assets/2548efe6-63cb-4050-ac44-1377b6f301bd)

The VaR and Expected shortfall conducted based on the simulations can be determined using the syntax controller.show_var_and_cvar(confidence_level=0.05)
![image](https://github.com/user-attachments/assets/1d75c688-3824-4a77-a7cb-c856c23c2a3c)

































