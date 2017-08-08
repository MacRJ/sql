## QUERY PRACTICE (work with a partner)

Instructions:
For each written part of this assignment, write the query underneath the line
## PLEASE ALSO DO THESE EXERCISES ON YOUR MACHINE.

When finished, submit a pull request.

* create a new database and name is it zoo
* import zoo.sql into that new database
* using sql, write a query that selects all animals
select * from animals;
* select and display just the name of every animal   
select name from animals;
* write a query that updates the name of "Smokey" to "Smokey the Bear"
update animals set name = 'Smokey the Bear' where name = 'Smokey';
* write a query that updates the name of "Fozzie" to "Fozzie the Bear"
update animals set name = 'Fozzie the Bear' where name = 'Fozzie';
* insert a new animal named Marlin with a species id that correspond to "fish".
insert into animals(name, species_id) values ('Marlin', 4);


USE JOINS TO ACHIEVE THE FOLLOWING :

* write a query that outputs all animals and their species name
select animals.name, species.name from animals join species on animals.species_id = species.id;
* write a query that outputs all of the fish ( must use a join )
select animals.name from animals join species on animals.species_id = species.id where species.name = 'fish'
* write a query that outputs all of the lions
select animals.name from animals join species on animals.species_id = species.id where species.name = 'lion';
* write a query that outputs all of the animals that are a mouse or a bear (you may need to think and discuss how to do this)
select animals.name from animals join species on animals.species_id = species.id where species.name = 'bear' or species.name = 'mouse';

USE AN AGGREGATE QUERIES TO ACHIEVE THE FOLLOWING:

* write a query tells us the average trainer level of all of the trainers
select avg(trainers.trainer_level) from trainers;
* write a query that tells us the name of the trainer with the highest level
select trainer_name, trainer_level from trainers where trainer_level = (select max(trainer_level) from trainers);

CONSTRUCT THE FOLLOWING:

* build a new table called "days of the week ", numbered 0 - 6 from Sunday to Saturday
create table days_of_the_week (
Number int,
Day varchar(255)
)
* write a query telling us all of the animals who have appointments on Sunday and who they're training with. This will require you using a join table.  Research join tables.  Is there a join table in the zoo table? which one is it, and how do you use it ?

select animals.name as Animal_Name, trainers.trainer_name as Trainer_name from animals join appointments on (animals.id = appointments.animal_id) join trainers on (appointments.trainer_id = trainers.id) where appointments.day_of_week = (select day_of_week from appointments join days_of_the_week on (appointments.day_of_week = days_of_the_week.number) where days_of_the_week.day = 'Sunday')
