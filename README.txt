I have reviewed both the codes and got some comments about the code.

Code to refactor
=================
1) app/Http/Controllers/BookingController.php
2) app/Repository/BookingRepository.php

Comments: -
1. For base contoller model is required, if not then its no use to use base controller.
2. In our repositery we are extending base controller but not using any methof of that Repo.
3. This contoller code looks ok to me, but there are few thing i would like to recommend. What i would like to do in this code is use of API Resources, i saw that each function is returning data in form of response. 
what if we want to write code for api's, do we have to rewrite everything? and if not in this case our repo is handling all the response. This is the role of API Resources.
4. I preffer to use interface with implementation in repositery, in this way we can seprate out logics also. we just need to call interface in our controler, and many repo can implement that interface also.
5. I prefer using Laravel FCM instead of using Curl for push notification.
6. If there are multiple notifications like mail, database and push notifications use Larvel Notifications and that will handle all of them once.
7. We can call notifications in events, currently we are using both notifications and events. just use events in repositery, and notifications in events.
8. Its good idea of using form request instead of just using request 
9. If using INNODB as database engine its good to lock row level transactions, what id we are inserting in multiple tables and last one return error. in that case we need to roll back all transactions.
