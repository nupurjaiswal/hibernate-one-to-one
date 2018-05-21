# Hibernate One to One Mappings
Example: An instructor can have an "instructor detail" entity
## Steps
- Execute the SQL script
 ```sh
DROP SCHEMA IF EXISTS `hb-01-one-to-one-uni`;

CREATE SCHEMA `hb-01-one-to-one-uni`;

use `hb-01-one-to-one-uni`;

SET FOREIGN_KEY_CHECKS = 0;

DROP TABLE IF EXISTS `instructor_detail`;

CREATE TABLE `instructor_detail` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `youtube_channel` varchar(128) DEFAULT NULL,
  `hobby` varchar(45) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=latin1;


DROP TABLE IF EXISTS `instructor`;

CREATE TABLE `instructor` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `first_name` varchar(45) DEFAULT NULL,
  `last_name` varchar(45) DEFAULT NULL,
  `email` varchar(45) DEFAULT NULL,
  `instructor_detail_id` int(11) DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `FK_DETAIL_idx` (`instructor_detail_id`),
  CONSTRAINT `FK_DETAIL` FOREIGN KEY (`instructor_detail_id`) REFERENCES `instructor_detail` (`id`) ON DELETE NO ACTION ON UPDATE NO ACTION
) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=latin1;

SET FOREIGN_KEY_CHECKS = 1;

```

###How do you reference a foreign key in the table?
 ```sh
 CREATE TABLE `instructor` (
   ..
   KEY `FK_DETAIL_idx` (`instructor_detail_id`),
   CONSTRAINT `FK_DETAIL` FOREIGN KEY (`instructor_detail_id`) REFERENCES `instructor_detail` (`id`) ON DELETE NO ACTION ON UPDATE NO ACTION
 ) ;
  ```
Main purpose of the foreign key is to preserve relationship between tables. It prevents operations
that would destroy the relationship

- Create a new class InstructorDetails.java
 ```sh
@Entity
@Table(name="instructor_detail")
public class InstructorDetail {

	// annotate the class as an entity and map to db table
	// define the fields
	// annotate the fields with db column names
	// create constructor
	// generate getter/setter methods
	// generate toString() method
	}
}

 ```
 - Create Instructor class
  ```sh
  @Entity
@Table(name="instructor")
public class Instructor {

	// annotate the class as an entity and map to db table
	// define the fields
	// annotate the fields with db column names
	// ** set up mapping to InstructorDetail entity
	// create constructors
	// generate getter/setter methods
	// generate toString() method
  ```
- Create Main App. Refer "CreateDemo.java"

- Delete an entity. Refer "DeleteDemo.java"


























    




























  