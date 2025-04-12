# Excel Project on TikTokShop Data Analytics
 My personal project of Excel on self-collected data of TikTokShop
## Introduction  
After a moderate time being an Account Manager for a big social media platform, I have grown my interest in e-commerce for its huge potential and rapid development speed. Hence I started to develop my abilities in analysing data to provide insights including customers' behaviours and decision-making process.  
## Aspects to analyse    
Getting to know the importance of price and shipping fee on the decision of customers, based on the self-collected data, I try to figure out: 
   
**1. Is the lower the shipping fee the more total sold will the product get?**  
**2. What are the major categories that byuers are looking for and their prices?**  
**3. How much is the GMV per product based on their own categories?**  

# Excel skills that I used
- Pivot Tables  
- Pivot Charts  
- DAX (Data Analysis Expressions)  
- Power Query  
- Power Pivot

## Notice: Due to the lack of precision from dataset, it would be expected that some of the values would be missing, or might not be able to depict the whole picture accurately. 

## 1. Is the lower the shipping fee the more total sold will the product get?  (ETL)
- Firstly, I used the query to take out the categories from the TikTok link, since the original version did not cover the category column. It also noticeable that only USA and Malaysia data contain the URL for categories, whilts the rest of the dataset from Vietnam, Philipines, Thailand and Singapore lacked of this section. I only use Malaysia dataset because many faulty data in USA section could lead to the lack of precision of an already scattered database. Please forgive me for not being able to find any replacing sources. 

- The query that I used to extract the categories (since my current version of Excel could not use the TEXTSPLIT function):
  
  `` =MID(Y2, SEARCH("/c/", Y2) + 3, SEARCH("/", Y2, SEARCH("/c/", Y2) + 3) - SEARCH("/c/", Y2) - 3) ``
  
Then inside Power Query, ETL process was conducted:  
![7](https://github.com/user-attachments/assets/e6ab2859-bd41-4a24-978c-a1c2be34ff9d)

- The result is as above image, when all the catagories had been extracted into a more concise and readable form.  

![5](https://github.com/user-attachments/assets/d5368b44-10d4-4efd-b63c-e03a5428035d)

 - It could be seen from the paragraph that the shipping cost may not vastly affect the decision to buy. For the reference for precision, please refer to the Notice section <3  

## 2.What are the major categories that buyers are looking for and their prices? (Pivot Chart)

- After calculating all the needed elements, I started to look for the most desired products of Malaysia market, and it is shown below using Pivot Chart:

![3](https://github.com/user-attachments/assets/2f451259-3846-4b9c-853a-e133f5af7c2f)

- It could be seen that the need for sport related products is quite high like Badminton and Casual Trainers, Power Banks also play a part in the revenue on TikTok Shop.

## 3. How much is the GMV per product based on their own categories? (DAX)

By using Power Pivot, I calculated additional number for showcasing the GVM and found out the shipping fee rate to anwser the question above: 

  - For calculating GMV:  
`` =TikTok_Shop_Malaysia[final_price]*TikTok_Shop_Malaysia[sold]
``
  - For rating the shipping fee:  
``` =IF(TikTok_Shop_Malaysia[shipping_fee]=0,"Free ship",  
    IF(AND(TikTok_Shop_Malaysia[shipping_fee]>0, TikTok_Shop_Malaysia[shipping_fee]<3), "Low shipping fee",  
        IF(AND(TikTok_Shop_Malaysia[shipping_fee]>=3, TikTok_Shop_Malaysia[shipping_fee]<=4.9), "Normal shipping fee",  
            IF(AND(TikTok_Shop_Malaysia[shipping_fee]>4.9, TikTok_Shop_Malaysia[shipping_fee]<=10), "High shipping fee",  
                IF(TikTok_Shop_Malaysia[shipping_fee]>10, "Extremely High shipping fee", "")         
            )  
```
  - Using the pivot chart, I got the below result:


![1](https://github.com/user-attachments/assets/3e908b71-a434-418f-8096-4db24b8266c9)  


 - Considering there was only 2 products that were free shipping, and other 4 were low shipping, I eliminated them and the final result is as below:  

![2](https://github.com/user-attachments/assets/a50ee964-aa39-4475-ad45-3514fd4a3099)  

- It could be seen that with the given data, TikTokShop customers in Malaysia did not hesitate to purchase a product with high shipping fee, which also provided high GMV rather than choose products with low or zero shipping fee.

# Conclusion:

It has come to my attention that people in Malaysia are willing to pay more and more on TikTok Shop, without hesitation to purchase despite high shipping fee or final price based on the given dataset. It is also recommended from the analytics that some of the categories like Power Banks, Sportswear and Clothes are drawing more attention from TikTok Shop user, hence more advertising and models could be put into consideration for a bigger GMV. This finding could be beneficial for not only Sellers, but also depict a new path for TikTokShop Account manager team to develop a new strategies with better guidance for Shop owners to grow. 

# Some of my final thoughts:

I have well acknowledged that this project has a huge room for improvement, but trying to surpass the lack of data myself was a huge obstacle for me, and I am glad that I tried to push it. I also ammended the table and tried to commit some other calculation, but as I have many times mentioned, it is hard for me to work with such deficient data. I hope that this small project could demonstrate my capabilities, and for what I have overcome, I believe that I would be able to face another challenge head on!

Also, ChatGPT was used as an assistant for gramamr, type and README file coding (lol)


