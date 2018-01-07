       Funnel Analysis
       Goal
       The goal is to perform funnel analysis for an e-commerce website.
       Typically, websites have a clear path to conversion: for instance, you land on the home page,
       then you search, select a product, and buy it. At each of these steps, some users will drop o"
       and leave the site. The sequence of pages that lead to conversion is called 'funnel'.
       Data Science can have a tremendous impact on funnel optimization. Funnel analysis allows to
       understand where/when our users abandon the website. It gives crucial insights on user
       behavior and on ways to improve the user experience. Also, it often allows to discover bugs.
       Challenge Description
       You are looking at data from an e-commerce website. The site is very simple and has just 4
       pages:
              The first page is the home page. When you come to the site for the first time, you can
              only land on the home page as a first page.
              From the home page, the user can perform a search and land on the search page.
              From the search page, if the user clicks on a product, she will get to the payment page,
              where she is asked to provide payment information in order to buy that product.
              If she does decide to buy, she ends up on the confirmation page
       The company CEO isn't very happy with the ]VS\TL VM sales and, especially, VM sales coming
       from new users. Therefore, she asked you to investigate whether there is something wrong in
       the conversion funnel or, in general, if you could suggest how conversion rate can be improved.
       Specifically, she is interested in :
              A full picture of funnel conversion rate for both desktop and mobile
              Some insights on what the product team should focus on in order to improve
              conversion rate as well as anything you might discover that could help improve
              conversion rate.
       Data
       We have 5 tables 
       All the tables refer to only the user first experience on the site. The 5 tables are:
            user_table     - info about the user
       Columns:
               user_id : the Id of the user. It is unique by user and can be joined to user id in all other
               tables
               date : the date when the user firstly landed on the site
               device : user device. Can be mobile or desktop
               sex : male/female
            home_page_table     - Users who landed on the home page
       Columns:
               user_id : the Id of the user. It is unique by user and can be joined to user id in all other
               tables
               page : it is always home_page.
            search_page_table      - Users who landed on the search_page
       Columns:
               user_id : the Id of the user. It is unique by user and can be joined to user id in all other
               tables
               page : it is always search_page
           payment_page_table      - Users who landed on the payment_page
       Columns:
              user_id : the Id of the user. It is unique by user and can be joined to user id in all other
              tables
              page : it is always payment_page
                payment_confirmation_table - Users who landed on the
          payment_confirmation_table. That is, these are the users who bought the product.
       Columns:
              user_id : the Id of the user. It is unique by user and can be joined to user id in all other
              tables
              page : it is always payment_confirmation_page
       Example
              Let's check one user through the funnel
       subset(user_table,user_id == 1659)
         Column Name          Value            Description
         user_id              1659             The Id of the user
         date                 2015-01-01       This user firstly hit the site on Jan, 1st.
         device               Mobile           User was using mobile
         sex                  Female           Was a female
              Let's check if she hit the home page (she should, since all users should hit
          the home page on their first visit)

       subset(home_page_table,user_id == 1659)
         Column Name         Value          Description
         user_id             1659           User id.
         page                home_page      Yep, on Jan, 1st she visited the home page
              Let's check if she hit the search page
       subset(search_page_table,user_id == 1659)
         Column Name         Value           Description
         user_id             1659            User id.
         page                search_page     Yep, on Jan, 1st she visited the search page too.
       Let's check if she hit the payment page
       subset(payment_page_table,user_id == 1659)
       <0 rows> (or 0-length row.names) # No. She never visited the payment page. User 1659
       landed on the site on Jan, 1st using mobile. From the home page, she then went to the search
       page and then left the site.
              Let's check one user who actually bought the product
       head (payment_confirmation_table, 1)
         Column
                       Value                           Description
         Name
         user_id       123100                          User id.
                                                       This user bought the product! Went all the
         page          payment_confirmation_page
                                                       way through the funnel! Success!

