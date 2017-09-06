# assignment_data_modeling
Mmmmm.... dataaaaa....

<br>
Mariah Schneeberger

*Include your ERM modeling "pseudocode" in the space below*

--- Basic ---

    -- STUDENT TABLE
      `id` INTEGER, unique, required - Primary Key
      `first_name` MEDIUMTEXT(3-24), required
      `last_name` MEDIUMTEXT(6-30), required
      `email` MEDIUMTEXT(4-64) unique, required
      `created_at` DATETIME
      `update_at` DATETIME


    -- COURES TABLE
      `id` INTEGER, unique, required - Primary Key
      `title` MEDIUMTEXT(4-64), unique, required
      `description` MEDIUMTEXT(4-64), required
      `created_at` DATETIME
      `updated_at` DATETIME


    -- LESSON TABLE
      `id` INTEGER, unique, required - Primary Key
      `course_id` INTEGER - Foreign Key - Course Table ID
      `title` MEDIUMTEXT(4-64), required, unique
      `description` MEDIUMTEXT(4-64), required
      `created_at` DATETIME
      `updated_at` DATETIME


    -- STUDENTCOURSE TABLE
      `student_id` INTEGER - Foreign Key - Student Table ID
      `course_id` INTEGER - Foreign Key - Course Table ID
      COMPOSITE KEY (`student_id`, `course_id`)


    -- PROFILE TABLE
      `id` INTEGER - PRIMARY KEY
      `student_id` INTEGER - Foreign KEY - Student Table ID
      `user_name` MEDIUMTEXT(4-64), required, unique
      `city` MEDIUMTEXT(4-64), required
      `state` MEDIUMTEXT(4-64), required
      `country` MEDIUMTEXT(4-64), required
      `age` INTEGER
      `gender` MEDIUMTEXT(4-6)


--- INTERMEDIATE ---

    -- USER TABLE
      `id` INTEGER, unique, required - PRIMARY KEY
      `user_name` MEDIUMTEXT(4-64), required, primary, unique
      `email` MEDIUMTEXT(4-64), required, unique
      `created_at` DATETIME
      `updated_at` DATETIME


    -- POST TABLE
      `id` INTEGER, required, unique - PRIMARY KEY
      `author_id` MEDIUMTEXT(4-64) required, unique - FOREIGN KEY - User Table ID
      `title` MEDIUMTEXT(4-64), required, unique
      `url` MEDIUMTEXT(4-64), required, unique
      `create_at` DATETIME
      `updated_at` DATETIME


    -- COMMENT TABLE
      `id` INTEGER, unique, required - PRIMARY KEY
      `author_id` MEDIUMTEXT(4-64), required - FOREIGN KEY - User Table ID
      `body` MEDIUMTEXT(4-64), required
      `created_at` DATETIME
      `updated_at` DATETIME
      `parent_id` INTEGER, - FOREIGN KEY - POST Or COMMENT ID
      `parent_type` MEDIUMTEXT "post" or "comment"

--- ADVANCED --

    -- USER TABLE
      `id` INTEGER NULL AUTO_INCREMENT DEFAULT NULL
      `first_name` MEDIUMTEXT(4-64), required
      `last_name` MEDIUMTEXT(4-64), required
      `email` MEDIUMTEXT(4-64), required, unique
      `address_id` INTEGER - FOREIGN KEY - ADRESSS TABLE ID
      `created_at` DATETIME
      `updated_at` DATETIME


    -- ORDER TABLE
      `id` INTEGER, unique - PRIMARY KEY
      `user_id` INTEGER - FOREIGN KEY - USER TABLE ID
      `shipment_id` INTEGER - FOREIGN KEY - SHIPMENT TABLE ID
      `created_at` DATETIME
      `updated_at` DATETIME


    -- PRODUCT TABLE
      `id` INTEGER, unique - PRIMARY KEY
      `name` MEDIUMTEXT(4-64), required, unique
      `description` MEDIUMTEXT(4-64), required, unique
      `price` DECIMAL, required
      `created_at` DATETIME
      `updated_at` DATETIME


    -- ORDERPRODUCT TABLE
      `order_id` INTEGER FOREIGN KEY - ORDER TABLE ID
      `product_id` INTEGER - FOREIGN KEY - PRODUCT TABLE ID
      COMPOSITE KEY (`order_id`, `product_id`)


    -- SHIPMENT TABLE
      `id` INTEGER, unique - PRIMARY KEY
      `address_id` INTEGER - FOREIGN KEY - ADDRESS TABLE ID
      `order_id` INTEGER - FOREIGN KEY - ORDER TABLE ID
      `ship_date` DATETIME
      `delivery_date` DATETIME
      `created_at` DATETIME
      `updated_at` DATETIME


    -- ADDRESS TABLE
      `id` INTEGER, unique, required - PRIMARY KEY
      `street_address` MEDIUMTEXT(4-64), reqiured
      `city_id` INTEGER, Foreign KEY - CITY TABLE ID 
      `created_at` DATETIME
      `updated_at` DATETIME


    -- CITY TABLE
      `id` INTEGER, unique, PRIMARY KEY
      `name`
      `state`
      `zip`
