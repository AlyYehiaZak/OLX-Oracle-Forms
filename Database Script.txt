CREATE TABLE olX
(
 Website_urL VARCHAR2(50),
 Server_region VARCHAR2(20) NOT NULL,
 CONSTRAINT web_pk PRIMARY KEY  (Website_urL) 



);
______________________________________________________________________________________

CREATE TABLE ADMIN
(
 Admin_ID NUMBER(20),
 Rolee VARCHAR2(50),
 Admin_Fname VARCHAR2(50),
 Admin_Lname VARCHAR2(50),
 Website_url VARCHAR2(50),
 CONSTRAINT adm_pk PRIMARY KEY ( Admin_ID ),
 CONSTRAINT web_fk foreign key ( Website_url) REFERENCES olx (Website_url ) 
 
);
______________________________________________________________


CREATE TABLE CATEGORY
(
 Category_ID NUMBER(20),
 Type VARCHAR2(50),
 
 CONSTRAINT CATE_pk PRIMARY KEY ( Category_ID  )
  
 
);
____________________________________


CREATE TABLE USERR
(
 User_ID NUMBER(20),
Address VARCHAR2(50) ,
User_Fname VARCHAR2(50),
User_Lname VARCHAR2(50) ,
Chat_id  number(20),
Category_ID NUMBER(20) ,
Website_url VARCHAR2(50),
 
 CONSTRAINT USER_pk PRIMARY KEY ( User_ID ),
 CONSTRAINT CATE_FK foreign KEY ( Category_ID  ) REFERENCES CATEGORY (Category_ID),

  CONSTRAINT webSITE_fk foreign key ( Website_url) REFERENCES olxX (Website_url ) 
  
 
);
alter table userr 

add  (chat_id number(20) references userr ( user_ID ) );

_________________________________________________________________________________________

CREATE TABLE USER_PHONE
(
 User_ID  NUMBER(20) REFERENCES USERR ( User_ID ),
  Phone NUMBER(20),
      
 
 CONSTRAINT USER_ID_PHONE_pk PRIMARY KEY (User_ID, Phone) 

);
__________________________________________________________________________________________



CREATE TABLE ADVERTISEMENT

(
Advertisement_ID NUMBER(20) ,
Datee date ,
User_ID NUMBER(20),
Description varchar2(50),
Published_since number(20) ,
 
  CONSTRAINT advertisement_ID PRIMARY KEY (Advertisement_ID) ,
  CONSTRAINT USER_ID foreign KEY (User_ID) REFERENCES USERR ( User_ID )

);
_____________________________________________________________________________________________

CREATE TABLE PRODUCT

(
Advertisement_ID NUMBER(20) REFERENCES ADVERTISEMENT (Advertisement_ID) ,
P_Name varchar2(50),
Category_ID   NUMBER(20)  REFERENCES CATEGORY(Category_ID  ) ,
 
  CONSTRAINT primary_keys PRIMARY KEY (Advertisement_ID,P_Name ,Category_ID) 
 
);
_____________________________________________________________________________________________

CREATE TABLE PRODUCT_PRICE
(
Advertisement_ID NUMBER(20) REFERENCES  ADVERTISEMENT (Advertisement_ID) ,
P_Name  varchar2(50)  ,
Price   NUMBER(20),
 
  CONSTRAINT primary_keyy PRIMARY KEY (Advertisement_ID) 
 
);
_____________________________________________________________________________________________

insert into olx ( server_region , website_url) 
values ( ' Europe' , 'olx.eu');

insert into olx ( server_region , website_url) 
values (' Africa ','olx.afc');

insert into olx ( server_region , website_url) 
values ( ' south america  ', 'olx.sa');

insert into olx ( server_region , website_url) 
values ( 'North america ', 'olx.na');

insert into olx ( server_region , website_url) 
values ( ' Australia ', 'olx.aus');

insert into olx ( server_region , website_url) 
values ( ' Asia', 'olx.asia');
_____________________________________________________________________________________________
insert into admin ( admin_id , rolee, admin_fname, admin_lname , website_url) 
values ( 1,'builder','ahmed','sameh','olx.aus' );

insert into admin ( admin_id , rolee, admin_fname, admin_lname , website_url) 
values ( 2,'designer','fadi','magdi','olx.asia' );

insert into admin ( admin_id , rolee, admin_fname, admin_lname , website_url) 
values (3,'designer','aly','yehia','olx.eu' );

insert into admin ( admin_id , rolee, admin_fname, admin_lname , website_url) 
values (4,'designer','ahmed','tarek','olx.na');

insert into admin ( admin_id , rolee, admin_fname, admin_lname , website_url) 
values ( 5,'builder','karim','chehab','olx.sa' );
___________________________________________________________________________________________
insert into userr ( user_id , address, user_fname, user_lname , chat_id , category_id, website_url ) 
values ( 1,'cairo','john','oliver',null,4,'olx.afc' );


insert into userr ( user_id , address, user_fname, user_lname ,  chat_id , category_id, website_url ) 
values ( 2,'Paris','mike','noah',null,2,'olx.eu' );


insert into userr ( user_id , address, user_fname, user_lname ,  chat_id , category_id, website_url ) 
values ( 3,'rio_de_janeiro','james','henry',null,1,'olx.sa' );


insert into userr ( user_id , address, user_fname, user_lname ,  chat_id , category_id, website_url ) 
values ( 4,'new_york','lucas','william',null,3,'olx.na' );


insert into userr ( user_id , address, user_fname, user_lname ,  chat_id , category_id, website_url ) 
values ( 5,'tokyo','harper','liam',null,5,'olx.asia' );

update userr
set chat_id =2
where user_id = 1;

update userr
set chat_id =3
where user_id =2 ;

update userr
set chat_id =4
where user_id =3 ;

update userr
set chat_id =5
where user_id =4 ;

update userr
set chat_id =1
where user_id =5;


_________________________________________________________________________________________________

insert into advertisement(advertisement_id, datee, user_id, description, published_since)
values (1,'01-NOV-2002',2,'bestProduct',20);

insert into advertisement(advertisement_id, datee, user_id, description, published_since)
values (2,'04-JUN-2002',1,'buyIt',18);

insert into advertisement(advertisement_id, datee, user_id, description, published_since)
values (3,'07-DEC-2003',3,'mustHave',40);

insert into advertisement(advertisement_id, datee, user_id, description, published_since)
values (4,'30-AUG-2003',5,'cheapProduct',42);

insert into advertisement(advertisement_id, datee, user_id, description, published_since)
values(5,'22-MAY-2001',4,'limited',5);

_________________________________________________________________________________________________

insert into product(p_name, category_id, advertisement_id)
values('Phone',1,1);

insert into product(p_name, category_id, advertisement_id)
values('Bed',5,4);

insert into product(p_name, category_id, advertisement_id)
values('Ball',2,2);

insert into product(p_name, category_id, advertisement_id)
values('Uno',4,5);

insert into product(p_name, category_id, advertisement_id)
values('Hoodie',3,3);

__________________________________________________________________________________________________
insert into product_price(advertisement_id, p_name, price)
values(1,'Phone',2500);
insert into product_price(advertisement_id, p_name, price)
values(4,'Bed',5000);
insert into product_price(advertisement_id, p_name, price)
values(2,'Ball',200);
insert into product_price(advertisement_id, p_name,price)
values(5,'Uno',50);
insert into product_price(advertisement_id, p_name, price)
values(3,'Hoodie',300);





____________________________________________________________________________________________________


insert into CATEGORY ( category_id, type)
values ( 1, 'electronics') ;
insert into CATEGORY ( category_id, type)
values ( 2, 'sports') ;

insert into CATEGORY ( category_id, type)
values ( 3, 'clothes') ;

insert into CATEGORY ( category_id, type)
values ( 4, 'games') ;

insert into CATEGORY ( category_id, type)
values ( 5, 'furniture') ;
_________________________________________________________________

insert into user_phone (user_id,phone)
values (1,01111111);

insert into user_phone (user_id,phone)
values (2,02222222);

insert into user_phone (user_id,phone)
values (3,03333333);

insert into user_phone (user_id,phone)
values (4,04444444);

insert into user_phone (user_id,phone)
values (5,05555555);
_________________________________________________________________________






