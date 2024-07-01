-- Creación de la base de datos Sentimientos_Redes
```sql
CREATE SCHEMA `Sentimientos_Redes` DEFAULT CHARACTER SET utf8 COLLATE utf8_spanish_ci ;

--Creación de la tabla Comentarios
CREATE TABLE Usuarios (
User_id   INT PRIMARY KEY,
Username  VARCHAR(55),
Platform  VARCHAR(15),
Country   VARCHAR(60)
)

--Creación de la tabla Usuarios
CREATE TABLE Comentarios (
Comment_id       INT PRIMARY KEY,
Texto            VARCHAR(255),
Sentiment        VARCHAR(15),
Hashtag_1        VARCHAR(50),
Hashtag_2        VARCHAR(50),
Retweets         INT,
Likes            INT,
User_id          INT,
Comment_Date     DATE,
Day_Time         TIME,
FOREIGN KEY (User_id) REFERENCES Usuarios(User_id)
)


-- Inserción de datos en la tabla Usuarios(Sample, la carga se realizó con el Wizard)
INSERT INTO Usuarios (User_id, Username, Platform, Country) VALUES
(0,' User123', 'Twitter', 'USA'),  
(1, 'CommuterX', 'Twitter', 'Canada'),  
(2, 'FitnessFan', 'Instagram', 'USA'),        
(3, 'AdventureX', 'Facebook', 'UK'),      
(4, 'ChefCook', 'Instagram', 'Australia'),
(5, 'GratitudeNow', 'Twitter', 'India'),  
(6, 'RainyDays', 'Facebook', 'Canada'),   
(7, 'MovieBuff', 'Instagram', 'USA'),
(8, 'DebateTalk', 'Twitter'  , 'USA'),
(9, 'BeachLover', 'Facebook' , 'Australia'), 
(10, 'BloggerX', 'Instagram' ,'USA'),
(11, 'WellnessCheck', 'Twitter'  , 'Canada'),  
(12, 'UrbanExplorer', 'Facebook' , 'UK'),      
(13, 'FitJourney', 'Instagram' , 'USA'),       
(14, 'TechEnthusiast', 'Twitter'  , 'India'),    
(15, 'Reflections', 'Facebook' , 'USA'),     
(16, 'PetAdopter', 'Instagram' , 'Canada'),   
(17, 'GamerX', 'Twitter'  , 'UK'),       
(18, 'TechConference', 'Facebook' ,'USA'),
(19, 'WinterBlues', 'Instagram' , 'USA'),       
(20, 'Bookworm', 'Twitter'  , 'India');

-- Inserción de datos en la tabla Comentarios(Sample, la carga se realizó con el Wizard)
INSERT INTO Usuarios (Comment_id,Texto,Sentiment,Hashtag_1,Hashtag_2,Retweets,Likes,User_id,Comment_Date,Time_Day) VALUES
(1,'Enjoying a beautiful day at the park!','Positive','#Nature','#Park',15,30,0,15/01/2023,12:30:00)
(2,'Traffic was terrible this morning.','NegativeT','#raffic','#Morning',5,10,1,15/01/2023,08:45:00)
(3,'Just finished an amazing workout!','Positive','#Fitness','#Workout',20,40,2,15/01/2023,15:45:00)
(4,'Excited about the upcoming weekend getaway!','Positive','#Travel','#Adventure',8,15,3,15/01/2023,18:20:00)
(5,'Trying out a new recipe for dinner tonight.','Neutral','#Cooking','#Food',12,25,4,15/01/2023,19:55:00)
(6,'Feeling grateful for the little things in life.','Positive','#Gratitude',"#'Positive'Vibes",25,50,5,16/01/2023,09:10:00)
(7,'Rainy days call for cozy blankets and hot cocoa.','Positive','#RainyDays','#Cozy',10,20,6,16/01/2023,14:45:00)
(8,'The new movie release is a must-watch!','Positive','#MovieNight','#MustWatch',15,30,7,16/01/2023,19:30:00)
(9,'Political discussions heating up on the timeline.','Negative','#Politics','#Debate',30,60,8,17/01/2023,08:00:00)
(10,'Missing summer vibes and beach days.','Neutral','#Summer','#BeachDays',18,35,9,17/01/2023,12:20:00)
(11,'Just published a new blog post. Check it out!','Positive','#Blogging','#NewPost',22,45,10,17/01/2023,15:15:00)
(12,'Feeling a bit under the weather today.','Negative','#SickDay','#Health',7,15,11,18/01/2023,10:30:00)
(13,"Exploring the city's hidden gems.",'Positive','#CityExplore','#HiddenGems',12,25,12,18/01/2023,14:50:00)
(14,'New year, new fitness goals','Positive','#NewYear','#FitnessGoals',28,55,13,18/01/2023,18:00:00)
(15,'Technology is changing the way we live.','Neutral','#Tech','#Innovation',15,30,14,19/01/2023,09:45:00)
(16,'Reflecting on the past and looking ahead.','Positive','#Reflection','#Future',20,40,15,19/01/2023,13:20:00)
(17,'Just adopted a cute furry friend!','Positive','#PetAdoption','#FurryFriend',15,30,16,19/01/2023,17:10:00)
(18,'Late-night gaming session with friends.','Positive','#Gaming','#LateNight',18,35,17,20/01/2023,00:05:00)
(19,'Attending a virtual conference on AI.','Neutral','#AI','#TechConference',25,50,18,20/01/2023,11:30:00)
(20,'Winter blues got me feeling low.','Negative','#WinterBlues','#Mood',8,15,19,20/01/2023,15:15:00)
 
