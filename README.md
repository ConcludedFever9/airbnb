# Airbnb Project 

## Objective
The objective of this project is to develop a data-driven approach for optimizing Airbnb accommodations in Berlin by predicting prices, forecasting demand, and analyzing guest sentiment. The data can be found [here](http://insideairbnb.com/get-the-data/) under the Berlin section.

## Key Components

- **Price Prediction:** Develop a machine learning model to predict the price of Airbnb listings in Berlin based on various features such as location, property type, number of bedrooms, amenities, etc. This model will help hosts set competitive prices and maximize revenue.

- **Demand Forecasting:** Analyze historical booking data to forecast the demand for Airbnb accommodations in different neighborhoods of Berlin over time. By understanding demand patterns, hosts can optimize pricing, availability, and marketing strategies.

- **Sentiment Analysis:** Analyze guest reviews to extract insights about the overall sentiment, common themes, and areas for improvement in Airbnb listings. Understanding guest sentiment can help hosts enhance the guest experience and attract more bookings.

## Findings

From the regression analysis conducted in this notebook aimed to predict price, it was determined that all three models mentioned exhibit comparable performance, as evidenced by their Mean Squared Error (MSE) values. Specifically, the Simple Regression model yielded an MSE of 9336, while the Random Forest model achieved 9490, and the Neural Network Regression model recorded a value of 9327.

![MSE report](/images/MSE.jpg)

While this MSE is much larger than expected (around 0.21 R-square), we can still understand two things:

- Overall, while a low R-squared score suggests that the predictors included in the model have limited explanatory power for price, it also provides valuable insights into the complexity of the price determination process.
- When more complicated regression models yield similar MSE values, opting for a simple linear regression model offers advantages in interpretability, reduced overfitting, computational efficiency, and serving as a reliable baseline for prediction. This choice balances model complexity with performance, ensuring practicality and ease of communication.

Moving on to time series and forecasting, we see from the below autocorrelation graphs that there was seasonality present in our total sales over time data.

![Time series report](/images/autocorrelation_plots.jpg)

Taking this into account, we fit a SARIMA model to the data which can be seen from the following graph.

![Time series predictions](/images/SARIMA.jpg)

This model achieved a MSE of 5722733838. The reason for this very large MSE is because the SARIMA model did not take into account the holiday season increase in sales. However, we can see that before the holiday spike the model performs pretty well. I believe this MSE would be much smaller if we had temporal data to include more than just one holiday season cycle so that SARIMA could understand this seasonal spike.

Finally, we had sentiment analysis. This was included just to see how popular Airbnb is in the city of Berlin. From the below barchart, we see overwhelming positive feedback.

![Time series predictions](/images/sentiment_dist.jpg.jpg)

___
## Conclusions 

1. **Model Performance**: Despite using more complex models like Random Forest and Neural Network, the performance in terms of Mean Squared Error (MSE) was similar to that of a simple linear regression model. This suggests that for predicting prices in the context of Airbnb accommodations in Berlin, the additional complexity of more advanced models may not provide significant improvements in predictive accuracy.

2. **Seasonality in Time Series Data**: The presence of seasonality in the total sales over time data indicates that there are recurring patterns in demand for Airbnb accommodations in Berlin, likely influenced by factors such as holidays, tourist seasons, or events. This underscores the importance of incorporating seasonality into forecasting models to improve predictive accuracy.

4. **Room for Improvement in Forecasting**: The SARIMA model achieved a high MSE, primarily due to its inability to account for holiday season increases in sales. This suggests that there is room for improvement in forecasting models by incorporating additional features or refining model parameters to better capture seasonal variations in demand.

5. **Positive Sentiment in Guest Reviews**: The overwhelming positive feedback from guest reviews indicates a high level of satisfaction with Airbnb accommodations in Berlin. This positive sentiment can be leveraged by hosts to enhance the guest experience further and attract more bookings.

Overall, the project provides valuable insights into optimizing Airbnb accommodations in Berlin by leveraging data-driven approaches for price prediction, demand forecasting, and sentiment analysis. These conclusions can inform strategic decisions for hosts and stakeholders to maximize revenue and guest satisfaction in the Airbnb market.

Tanner Zuleeg 
15/2/2024